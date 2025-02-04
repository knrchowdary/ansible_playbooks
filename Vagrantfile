$playbook = "test.yml"
$other_args ="--extra-vars 'server_groups=test1'"
servers=[
  {
    :hostname => "vagrant-test1",
    :ip => "192.168.94.21",
    :box => "ol76",
    :ram => 1024,
    :cpu => 1
  },
  {
    :hostname => "vagrant-test2",
    :ip => "192.168.94.22",
    :box => "ol76",
    :ram => 1024,
    :cpu => 1
  }
]

$log_folder = "logs"
$ssh_key = <<-SCRIPT
cat /vagrant/vagrant/id_rsa.pub >> /home/vagrant/.ssh/authorized_keys
SCRIPT

Vagrant.configure("2") do |config|
    config.vm.box = "ol76"
    config.vm.box_url ="https://yum.oracle.com/boxes/oraclelinux/ol76/ol76.box"

    if Vagrant.has_plugin?("vagrant-hostmanager")
      config.hostmanager.enabled = true
      config.hostmanager.manage_guest = true
    end

    if Vagrant.has_plugin?("vagrant-cachier")
      config.cache.scope = :box
    end

    config.vm.provision "shell", privileged: false, inline: $ssh_key
       
    servers.each do |machine|
      config.vm.define machine[:hostname] do |node|
        node.vm.box = machine[:box]
        node.vm.hostname = machine[:hostname]
        node.vm.network "private_network", ip: machine[:ip]
        node.vm.provider "virtualbox" do |vb|
            vb.memory = machine[:ram]
            vb.cpus = machine[:cpu]
            vb.linked_clone = true
        end
      end
    end
  
    #
    # this is our ansible controller VM which provisions the other VMs
    #
    config.vm.define "controller" do |controller|
      controller.vm.network :private_network, ip: "192.168.94.10"
      
      controller.vm.hostname = "controller"
      # install ansible and ssh private keys
      controller.vm.provision "shell", privileged: false, inline: <<-EOF
        cp /vagrant/vagrant/id_rsa.pub /home/vagrant/.ssh/id_rsa.pub
        cp /vagrant/vagrant/id_rsa /home/vagrant/.ssh/id_rsa
        chown vagrant:vagrant /home/vagrant/.ssh/id_rsa*
        chmod 600 /home/vagrant/.ssh/id_rsa*
        sudo yum install ansible cowsay bash-completion git -y      
      EOF

      # run ansible
      controller.vm.provision "ansible", type: "shell", privileged: false, inline: <<-EOF
        set -x
        rm -rf /tmp/provisioning
        cp -r /vagrant /tmp/provisioning
        cd /tmp/provisioning
        chmod -x hosts_vagrant
        chmod -x /tmp/provisioning/vault_pass
        export ANSIBLE_HOST_KEY_CHECKING=False
        export ANSIBLE_LOG_PATH=/vagrant/#{$log_folder}/#{$playbook}.log
        export ANSIBLE_NOCOWS=1
        mkdir -p /vagrant/#{$log_folder}
        ansible-galaxy install -r requirements.yml
        ansible-playbook -i inventories/vagrant/hosts.ini #{$playbook} #{$other_args}
      EOF

      controller.vm.provider "virtualbox" do |v|
        v.linked_clone = true
        v.memory = 384
        v.cpus = 1
      end
    end
  
  end
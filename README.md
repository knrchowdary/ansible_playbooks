# Requirements

1. Ansible - >~2.7

# ansible_playbooks

## Ansible General Folder Structure

We are using ansible folder standard as defined in https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html#alternative-directory-layout


We are adding following items which are extra as defined in https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html#alternative-directory-layout

### 1. Other files 

We are having `files` folder to store any extra files needed like certificates, extra dependency, etc. 

We also having subfolder like `files/{{ env }}/{{ httpd }}`

### 2. Vagrantfile 

You can also use vagrant to test or to run infra on your local system which is defined in Vagrantfile

### 3. Some common tasks 

For some common tasks which can be used between multiple roles (like systemd service template) we have a folder having name `roles/common_tasks`. In this we can put tasks on root folder and for templates use `templates` folder

```
├── systemd.yml
└── templates
    └── etc
        └── systemd
            └── system
                └── systemd.service.j2
```

And template usage example in tasks

```
- name: create template for systemd 
  template: 
    src: etc/systemd/system/systemd.service.j2
    dest: "/etc/systemd/system/{{ name }}.service"
```

## Common tasks 
For usage and variable see files in roles/common_tasks/{task_name}.yml

1. systemd
2. get_url

## Ansible Vault

We are using ansible vault for storing secrets. Generally we maintain different identity files for decrypting. 
We don't use a single file to store ecrypted values, instead using ansible vault string to encrypt and place in normal un-encrypted file, like below: 

```
## Without encryption
name: test
database_name: test
database_host: localhost
database_password: password
```

```
## With encryption
name: test
database_name: test
database_host: localhost
database_password: !vault |
          $ANSIBLE_VAULT;1.2;AES256;dev
          30613233633461343837653833666333643061636561303338373661313838333565653635353162
          3263363434623733343538653462613064333634333464660a663633623939393439316636633863
          61636237636537333938306331383339353265363239643939666639386530626330633337633833
          6664656334373166630a363736393262666465663432613932613036303963343263623137386239
          6330
```

To encrypt any plan string to encrypted one we run below command: 

```
ansible-vault encrypt_string --vault-id dev@a_password_file 'foooodev' --database_password 'the_dev_secret'
```

Result: 

```
database_password: !vault |
          $ANSIBLE_VAULT;1.2;AES256;dev
          30613233633461343837653833666333643061636561303338373661313838333565653635353162
          3263363434623733343538653462613064333634333464660a663633623939393439316636633863
          61636237636537333938306331383339353265363239643939666639386530626330633337633833
          6664656334373166630a363736393262666465663432613932613036303963343263623137386239
          6330
```


Now you can use above string to replace in our yml variable file

Ref: https://docs.ansible.com/ansible/latest/user_guide/vault.html#use-encrypt-string-to-create-encrypted-variables-to-embed-in-yaml

## Some best practice for ansible 

We are using many best practice when we are going to write playbooks or roles. Some of them mention below: 

1. Always try to put tasks in roles not playbook. Playbooks just used to co-relate roles with hosts and changing variables if required for specific role.
2. Don't put environment related specifications on roles, always try to maintain them in environment group variables like `inventories/{{env}}/group_vars/all.yml`.
3. Try to put all general specifications for roles in default variables so that we need to override variable very less, this help in having small environment group vars files. Small files are always easy to maintain and creates less problem in conflicts
5. Always use `ansible-galaxy init` to create a new role from  
4. Some more practices can get from URL https://www.ansible.com/blog/ansible-best-practices-essentials

## Using Vagrant

### Plugin need to install 

Command to install vagrant plugin 

`vagrant plugin install <plugin-name>`

1. vagrant-hostmanager

### Lifecycle 

`vagrant up` (Create machine and provisioning) => `vagrant provision controller` (re-run ansible-playbook) => `vagrant destroy` (destroy vms created by vagrant up)

### Creating Infrastructure

Just run `vagrant up` command and it will create VMs defined in Vagrantfile

### Vagrantfile configuration

Three variables are defined which used as below: 

1. playbook => playbook need to run at time of provisioning (default `test.yml`)
2. servers  => List of array having information on Virtualmachines need to created
3. log_folder   => Folder to store logs of ansible-playbook run

### Re-run ansible-playbook

`vagrant provision controller`

or to be more specific

`vagrant provision controller --provision-with ansible`

### Destroy

`vagrant destroy`

## Setting UP Domain Controller using Smaba 4 server

You can also setup Domain controller using role `mrlesmithjr.samba` role.
Below playbook can be used to setup domain controller for vagrant env. `inventories/vagrant/group_vars/controller.yml` is the variable file.

```yaml
- hosts: controller
  roles:
    - base
    - mrlesmithjr.samba
  become: yes
```

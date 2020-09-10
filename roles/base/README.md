base
=========

Role to do all basics stuff for oracle linux 7 and Oracle linux 6:

Like adding hostnames, yum_repos and basic packages.

For adding hostnames in /etc/hosts file, we are used hosts.yml playbook.

For adding yum repository, we are used yum_repo.yml palybook.

Requirements
------------

NA

Role Variables
--------------

```
base_yum_repo_oracle_7:  # Dict contains yum repo which need to be added. For all keys please have a look below
  ol7_optional_latest:
    description: Oracle Linux $releasever Optional Latest ($basearch)
    baseurl: https://yum.oracle.com/repo/OracleLinux/OL7/optional/latest/$basearch/
    gpgcheck: yes
    gpgkey: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-oracle
    enabled: yes
    file: oracle-linux-ol7     
```
``` 
base_yum_repo_oracle_6:
  epel:
    description: Extra Packages for Enterprise Linux 6 - $basearch
    baseurl: http://download.fedoraproject.org/pub/epel/6/$basearch
    mirrorlist: https://mirrors.fedoraproject.org/metalink?repo=epel-6&arch=$basearch
    failovermethod: priority
    enabled: yes
    gpgcheck: yes
    gpgkey: https://dl.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL-6
    file: oracle-epel-ol6

```

```
base_packages_7: # Array contains packages need to be installed
  - htop
  - bash-completion
  - unzip

base_packages_6:     
  - unzip
  - libselinux-python
```

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: base }

License
-------

Accommodations Plus International

Author Information
------------------

Varun Palekar

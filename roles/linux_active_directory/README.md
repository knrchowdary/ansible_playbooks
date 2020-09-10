Linux Active Directory
=========

This role is to add redhat family linux OS version 7 to Active Directory server, and you can also authenticate with it.

Requirements
------------

A running active directory server with DNS

Role Variables
--------------

| Variable Name                                  | default vaule               | Desc                                                                                         |
|------------------------------------------------|-----------------------------|----------------------------------------------------------------------------------------------|
| linux_active_directory_packages                | array of defaults packages  | list of yum packages which required for this role to work                                    |
| linux_active_directory_domain                  | test.com                    | domain name to which machine need to connect                                                 |
| linux_active_directory_bind_dn                 | administrator               | Username used to attach active directory                                                     |
| linux_active_directory_bind_pw                 | Welcome@123                 | Password used to attach active directory                                                     |
| linux_active_directory_computer                | OU={{ env }},DC=test,DC=com | Computer attach to further OU, DC, etc. Its in Ldap organisational form                      |
| linux_active_directory_group                   | - "{{ env }}"               | List of groups which are in AD has access to the node                                        |
| linux_active_directory_sudo_group              | - sudo                      | List of groups which are in AD has to be sudo access to the node                             |
| linux_active_directory_ssh_allow_password_auth | true                        | Do we need to allow password authentication on in SSH by  linux_active_directory_group group |

Dependencies
------------

NA


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
        - role: linux_active_directory
          linux_active_directory_domain: test.com
          linux_active_directory_bind_dn: administrator
          linux_active_directory_bind_pw: Welcome@123
          linux_active_directory_computer: "OU={{ env }},DC=test,DC=com"
          linux_active_directory_group:
            - "{{ env }}"
          linux_active_directory_sudo_group:
            - sudo

License
-------

Accommodations Plus International

Author Information
------------------

Varun Palekar
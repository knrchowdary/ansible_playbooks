Tomcat 8.5.34 Installation
=========

This role is to install tomcat on server.

Requirements
------------

A running server

Role Variables
--------------

| Variable Name                                  | default vaule               | Desc                                                                                         |
|------------------------------------------------|-----------------------------|----------------------------------------------------------------------------------------------|
| tomcat8_version                                | 8.5.34                      | This sets the tomcat version we want to set-up                                   |
| tomcat8_java_home                              | /usr/java/default           | This sets the java home for tomcat setup                                                 |
| tomcat8_port                                   | 3080                        | This value can be used if we want to change default tomcat port                                                     |
| tomcat_roles                                   | Set of array                | This is a set of array which contains all tomcat user roles 
| tomcat_users                                   | List                        | This sets username and password for accessing manager app                      |


Dependencies
------------

NA


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
        - role: tomcat8
          tomcat8_version: 8.5.34
          tomcat8_java_home: /usr/java/default
          tomcat8_port: 3080
          tomcat_roles:
            - manager-gui
            - manager-script
            - manager-jmx
            - manager-status  
          tomcat_users:
            - name: tomcat8
              password: changeme

License
-------

Accommodations Plus International

Author Information
------------------

Anurag Junghare
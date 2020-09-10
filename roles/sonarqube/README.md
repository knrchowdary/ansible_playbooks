SonarQube installation and Set-up
=========

This role is to install and configure SonarQube on server.

Requirements
------------

A running AWS/VM server with JDK 11 installed.

Role Variables
--------------

| Variable Name                                  | default vaule               | Desc                                                                                         |
|------------------------------------------------|-----------------------------|----------------------------------------------------------------------------------------------|
| sonarqube_version                              | 7.9.1                       | SonarQube version which we want to install                                    |
| sonarqube_max_map_count                        | 262144                      | Specifies the virtual memory count for Elasticsearch                                                 |
| sonarqube_fs_file_max                          | 65536                       | File no descriptors                                                     |
| sonarqube_db_name                              | d_sonar_db                  | Name of master database created in RDS                                                     |
| sonarqube_jdbc_url                             | rds instance end-point      | JDBC connection url for connectivity                      |
| sonarqube_jdbc_username                        | admin                       | RDS master database username                                        |
| sonarqube_jdbc_password                        | secret password             | RDS master database password                             |
| sonarqube_config_vars                          | list of config property     | List of configuration properties like RDS, database name, etc |

Dependencies
------------

Need to have RDS instance configured and also need to provide RDS master database name (i.e., sonarqube_db_name), username and password while making connections with SOnarQube.


Example Playbook
----------------

Including an example of how to use your role.

    - hosts: servers
      roles:
        - role: sonarqube

License
-------

Accommodations Plus International

Author Information
------------------

Anurag Junghare
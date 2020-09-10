Confluence Set-up
=========

This role is to set-up Confluence on target Server.

Requirements
------------

Physical Machine requirement for setting up Jira is to have atleast 2GB of RAM to run effeciently and another 1GB RAM for the OS. 
Also a Running Database to connect with Jira. 
JDK version should be 8 for running Jira.

Role Variables
--------------

| Variable Name                                  | default vaule               | Desc                                                                                         |
|------------------------------------------------|-----------------------------|----------------------------------------------------------------------------------------------|
| confluence_pkg_version                         | 6.15.1                      | Confluence Package Version                                    |
| oracle_java_version_string                     | 1.7.0_80                    | Java version we need to set-up for confluence, we need jdk8                                                 |
| confluence_java_mysql_connector_version        | 8.0.19                      | Mysql jdbc connector version                                                     |
| confluence_connector_port                      | 8081                        | Confluence connector port                                                     |
| confluence_db_name                             | d_confluence_db             | Name of initial database for confluence                       |
| confluence_db_user                             | confluence                  | Username for accessing confluence dayabase                                        |
| confluence_db_password                         | secret password             | Password for confluence database                             |

Dependencies
------------

NA


License
-------

Accommodations Plus International

Author Information
------------------

Anurag Junghare
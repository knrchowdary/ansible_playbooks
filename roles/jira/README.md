Jira Set-up
=========

This role is to set-up Jira on target server.

Requirements
------------

Physical Machine requirement for setting up Jira is to have atleast 2GB of RAM to run effeciently and another 1GB RAM for the OS.
Also a Running Database to connect with Jira.
JDK version should be 8 for running Jira.

Role Variables
--------------

| Variable Name                                  | default vaule               | Desc                                                                                         |
|------------------------------------------------|-----------------------------|----------------------------------------------------------------------------------------------|
| jira_version                                   | "7.13.1                     | Jira version we want to set-up                                    |
| oracle_java_version_string                     | 1.7.0_80                    | JDK version we want to set-up                                             |
| jira_java_home                                 | /usr/java/default           | Java home which need to provide for jira application                                                     |
| jira_java_mysql_connector_version              | 8.0.19                      | Mysql connector for Jira set-up                                                     |
| jira_rds_instance_end_point                    | RDS instance end point      | Database connection end point for Jira set-up                      |
| jira_database_port                             | 3306                        | Database port for Jira set-up                                        |
| jira_database_name                             | d_jira_db                   | Name of initial database created inside RDS, so that Jira can use that one       |
| jira_database_username                         | admin                       | Username for accessing database for jira       |
| jira_database_password                         | secret password             | Password for accessing database for jira       |

Dependencies
------------

NA

License
-------

Accommodations Plus International

Author Information
------------------

Anurag Junghare
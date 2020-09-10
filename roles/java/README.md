Java
=========

Role to install oracle java, currently supports following versions: 

1. 1.7 

Requirements
------------

Depends on Java binary stored repository.
Variables responsible for that: 

1. oracle_java_rpm_url
2. oracle_java_rpm_url_username
3. oracle_java_rpm_url_password

Role Variables
--------------

| Variable Name                | default vaule                                        | Desc                                                                          |
|------------------------------|------------------------------------------------------|-------------------------------------------------------------------------------|
| oracle_java_set_as_default   | yes                                                  | Either set default Java in whole system by creating link in /usr/bin/         |
| oracle_java_version_string   | 1.7.0_80                                             | Oracle Java Version get by java -version command                              |
| oracle_java_dir_source       | /opt/java                                            | default directory to download java rpm package                                |
| oracle_java_rpm_filename     | jdk.rpm                                              | download filename of java rpm                                                 |
| oracle_java_rpm_url          | http://10.10.103.162:8081/repository/thirdparty-release-raw/jdk-7u80-linux-x64.rpm | Download URL of JAVA rpm                                                      |
| oracle_java_rpm_url_username | ""                                                   | Download username of URL requires                                             |
| oracle_java_rpm_url_password | ""                                                   | Download username of URL requires                                             |
| oracle_java_home             | /usr/java/default                                    | Default location to which RPM install JAVA, can be different for different OS |

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: java }

Extra
-----

Curl command to download file from nexus repo 

```
curl -v --user 'admin:admin123' --upload-file ./README.md http://localhost:8081/repository/rawhosted1/no-type-README.md
curl -v --user 'admin:admin123' -X GET http://localhost:8081/repository/rawhosted1/README.md
curl -v --user 'admin:admin123' -X DELETE http://localhost:8081/repository/rawhosted1/README.md
curl -v --user 'admin:admin123' -X DELETE http://localhost:8081/repository/rawhosted1/no-type-README.md
```

License
-------

Accommodations Plus International

Author Information
------------------

Varun Palekar

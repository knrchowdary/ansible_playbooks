Jenkins
=========

Role to install Jenkins, currently supports following versions:

1. 2.213

Used playbooks are:
1. pre_tasks.yml
2. install.yml
3. configure.yml

Used playbooks are:
1. upgrade_plugin.yml

Import the configuration archive, used playbooks are:
1. import.yml


Requirements
------------

Depends on jenkins binary stored repository.
Variables responsible for that:

1. jenkins_url 
2. jenkins_plugin
3. jenkins_config_url
4. jenkins_url_username
5. jebkins_url_password

Role Variables
--------------

| Variable Name                | default vaule                                        | Desc                                                                          |

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: jenkins }

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

James Goley

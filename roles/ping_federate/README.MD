Ping Federate
=========

Role to install Ping Federate, currently supports following versions:

1. 9.2.2

Used playbooks are:
1. pre_tasks.yml
2. install.yml
3. configure.yml


To install custom adapters, There are two custom adapters being used on the API Ping Federate SSO server:

1. Ping Identity Agentless Integration Kit
2. API Adapter for Envoy Role Service

Used playbooks are:
1. upgrade_plugin.yml

Import the configuration archive, used playbooks are:
1. import.yml


Requirements
------------

Depends on ping federate binary stored repository.
Variables responsible for that:

1. ping_federate_url 
2. ping_federate_plugin
3. ping_federate_config_url
4. ping_federate_url_username
5. ping_federate_url_password

Role Variables
--------------

| Variable Name                | default vaule                                        | Desc                                                                          |

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: ping_federate }

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

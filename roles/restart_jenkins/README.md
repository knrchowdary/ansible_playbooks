Jenkins
=========

Simple restart of Jenkins

1. 2.213

Used playbooks are:
1. Handlers/main.yml


Requirements
------------

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

ec2_scheduler_start
===================

Role to start AWS servers by using tags.

Currently we are using tag key as ```Type``` and
                       tag value as  ```scheduled```


Requirements
------------
BOTO3

AWS_ACCESS_KEY

AWS_SECRET_ACCESS_KEY

All these requirement should be present in controller server(In our case AWX server) 

Role Variables
--------------

| Variable Name                | default vaule                                        | Desc                                                                          |
|------------------------------|------------------------------------------------------|-------------------------------------------------------------------------------|
| ec2_scheduler_region   | us-east-1                                                 | Our default region   |
| ec2_scheduler_tag  | Scheduled                                             | Default tag  value we are using scheduled      |


Example Playbook
----------------

    - hosts: servers
      gather_facts: false
      connection: local
      roles:
        - { role: ec2_scheduler_start }
      become: yes
      become_method: sudo
    

Extra
-----


```

License
-------

Accommodations Plus International

Author Information
------------------

Narasimha Rao

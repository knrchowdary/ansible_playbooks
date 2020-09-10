Linux Active Directory
=========

This role is to install and configure activemq and broker properties

Requirements
------------

NA

Role Variables
--------------

| Variable Name                                  | default vaule               | Desc                                                                                         |
|------------------------------------------------|-----------------------------|----------------------------------------------------------------------------------------------|
| activemq_version                               | activemq version            | ActiveMQ version which we want to install and configure                                    |
| activemq_opts_memory                           | -Xms1G -Xmx1G               | JVM heap options                                                 |
| brokers                                        | list of broker properties   | Specify the broker properties for Brokers                                                  |


Dependencies
------------

NA


Example Playbook
----------------

Including an example of how to use your role

    - hosts: servers
      roles:
        - role: activemq

License
-------

Accommodations Plus International

Author Information
------------------

Anurag Junghare

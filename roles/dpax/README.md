DPAX
=========

Role for dpax application deployment.

We are following serial deployment

In this strategy we deploy to each server one at a time. We take each server off the load balancer and then add it back once the deployment has succeeded


Requirements
------------

BOTO3

AWS_ACCESS_KEY

AWS__SECRET_ACCESS_KEY


Role Variables
--------------

| Variable Name                | default vaule                                        | Desc                                                                          |
|------------------------------|------------------------------------------------------|-------------------------------------------------------------------------------|
| dpax_tomcat_home   | /opt/tomcat8   | Tomcat home directory  |
|dpax_tomcat_deploy | {{ dpax_tomcat_home }}/webapps | This is the location where we are deploying war files |
| dpax_mvn_repo | http://10.10.103.162:8081/repository/{{ dpax_nexus_repo }} | URL of Nexus repository, From here we are pulling artifact |
| dpax_region | us-east-1 | AWS region  | 
| dpax_group_id | com.apihotels | Group id of maven project |
| dpax_artifact_id | DPAX | Artifact id of maven project |
| dpax_package_type | war | Package type of maven project |

Example Playbook
----------------

    - hosts: servers
      serial: 1
      vars_files:
       - "inventories/{{ env }}/group_vars/all.yml"
       - "inventories/{{ env }}/group_vars/AWS_{{ server_groups }}.yml"
      roles:
        - dpax  
      become: yes
      become_method: sudo
      remote_user: ec2-user

Extra
-----



```

```

License
-------

Accommodations Plus International

Author Information
------------------

Narasimha Rao

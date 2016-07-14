add_to_hosts_to_zabbix
=========

This playbook will add hosts to your Zabbix server.

Requirements
------------
This playbook use zabbix_host, zabbix_group, and zabbix_screen(Extra Module).
- zabbix-api(pip)
- python >= 2.6 
- ansible >= 2.0


Role Variables
--------------
see defaults


Example Playbook
----------------
```
- hosts: localhost
  connection: local
  vars: 
     zabbix_url: http://192.168.33.14/zabbix
     zabbix_hosts:
       - ip: 192.168.33.99
         hostname: testhost
         screen_name: testtest
       - ip: 192.168.33.100
         hostname: testhost2
         screen_name: testtest2
     zabbix_templates:
       - Template App Zabbix Agent
       - Template App HTTP Service
       - Template JMX Tomcat
     interfaces: 
       - type: 1
         main: 1
         useip: 1
         dns: ""
         port: "10050"
       - type: 4 
         main: 1
         useip: 1
         dns: ""
         port: "4270"
     login_user: Admin
     login_password: zabbix
     graph_names:
       - CPU utilization
       - CPU load
       - Memory Free
     create_screen: false
  roles:
    - add_hosts_to_zabbix   
```

License
-------
MIT

Author Information
------------------
@connvoi

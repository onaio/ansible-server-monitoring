Server Monitoring
=================

Use this role to setup monitoring on a server. This role will:

 - Set the server's hostname (for easy identification)
 - Instal [collectd](https://collectd.org/) and set up monitoring for server 'vitals'

Role Dependencies
-----------------

 - [onaio/hostname](http://github.com/onaio/ansible-hostname)
 - [onaio/collectd](http://github.com/onaio/ansible-collectd)


Role Variables
--------------

### Required Variables

None currently.

### Other Default variables are listed below:

    # collectd and Graphite
    server_monitoring_collectd_scripts: ["graphite", "cpu", "disk", "load", "memory"]
    server_monitoring_graphite_server_ip: "127.0.0.1"
    server_monitoring_graphite_server_port: "2003"
    server_monitoring_graphite_server_protocol: "tcp"
    # Name of entity that owns the server
    server_monitoring_owner: "ona"
    # Describes the server's purpose. If it's used to run a single app 'Test App' then server_monitoring_server_type can be 'test_app_server'
    server_monitoring_server_type: "generic"

    # Hostname
    # Whether to change the server's hostname or not
    server_monitoring_set_hostname: true
    server_monitoring_hostname: "{{ ansible_hostname }}"
    server_monitoring_hostname_from_ec2_Name_tag: true

Example Playbook
----------------

Setup monitoring on a server

    - name: Setup server monitoring
      hosts: servers
          server_monitoring_graphite_server_ip: "1.2.3.4"
          server_monitoring_server_type: "app-server"
      roles:
        - role: server-monitoring

License
-------

Apache 2

Authors
-------

Update by [Ona Engineering](https://ona.io)


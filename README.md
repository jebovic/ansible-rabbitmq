RabbitMQ
=========

[![Build Status](https://travis-ci.org/jebovic/ansible-rabbitmq.svg?branch=master)](https://travis-ci.org/jebovic/ansible-rabbitmq) [![Ansible Galaxy](https://img.shields.io/badge/galaxy-jebovic.rabbitmq-blue.svg?style=flat)](https://galaxy.ansible.com/jebovic/rabbitmq)

Install and configure RabbitMQ

This role is a part of my [OPS project](https://github.com/jebovic/ops), follow this link to see it in action. OPS provides a lot of stuff, like a vagrant file for development VMs, playbooks for roles orchestration, inventory files, examples for roles configuration, ansible configuration file, and many more.

Compatibility
-------------

Tested and approved on :

* Debian jessie (8+)
* Ubuntu Trusty (14.04 LTS)
* Ubuntu Xenial (16.04 LTS)

Role Variables
--------------

```yaml
# rabbitmq install configuration
rabbitmq_apt_key_url: https://www.rabbitmq.com/rabbitmq-release-signing-key.asc
rabbitmq_apt_repositories:
  - "deb http://www.rabbitmq.com/debian/ testing main"
rabbitmq_packages:
  - rabbitmq-server
rabbitmq_daemon: rabbitmq-server

# rabbitmq basic configuration
rabbitmq_config_path: /etc/rabbitmq
rabbitmq_env_config:
  node_ip_address: '""'
  node_port: 5672
  dist_port: 25672
  nodename: "rabbitmq-{{ ansible_hostname }}"
  conf_env_file: /etc/rabbitmq/rabbitmq-env.conf
  use_longname: "false"
  ctl_erl_args: no
  server_erl_args: no
  server_additional_erl_args: no
  server_start_args: no
rabbitmq_enable_plugins: yes
rabbitmq_enabled_plugins:
  - rabbitmq_management
rabbitmq_default_vhost: /
rabbitmq_default_user: rabbitmq
rabbitmq_default_user_group: rabbitmq
rabbitmq_default_pass: rabbitmq
rabbitmq_default_permissions: '[<<".*">>, <<".*">>, <<".*">>]'
rabbitmq_default_user_tags: admin, administrator
```

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
     - { role: jebovic.rabbitmq }
```

Example : config
----------------

```yaml
# Modify defaults variables to fit your needs
# One can add rabbitmq plugins, change the default admin user...
```

Tags
----

* rabbitmq_config : only update config and restart service

License
-------

MIT

Author Information
------------------

Jérémy Baumgarth https://github.com/jebovic

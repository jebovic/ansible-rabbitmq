RabbitMQ
=========

[![Build Status](https://travis-ci.org/jebovic/ansible-rabbitmq.svg?branch=master)](https://travis-ci.org/jebovic/ansible-rabbitmq) [![Ansible Galaxy](https://img.shields.io/badge/galaxy-jebovic.rabbitmq-blue.svg?style=flat)](https://galaxy.ansible.com/jebovic/rabbitmq)

Install and configure RabbitMQ

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

Tags
----

* rabbitmq_config : only update config and restart service

License
-------

MIT

Author Information
------------------

Jérémy Baumgarth https://github.com/jebovic

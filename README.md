Redis Ansible Role
=========

Ansible Role for setting up Redis standalone servers, replica sets and sentinel servers.

Role Variables
--------------

All variables of this role are listed in the [defaults/main.yml](defaults/main.yml) file.

Example Playbook
----------------

Examples of how to use this role.

    - name: standalone redis server
      hosts: redis-server.example.com
      vars:
        redis_bind: 127.0.0.1
      roles:
        - ansible-redis

    - name: setup redis slaves
      hosts: redis-slaves-group
      vars:
        redis_slaveof_host: 192.168.1.1
        redis_slaveof_port: 6379
      roles:
        - ansible-redis

    - name: setup sentinel servers
      hosts: redis-sentinels-group
      vars:
        redis_sentinel: yes
        redis_sentinel_monitors:
          - name: mymaster
            host: 192.168.1.1
            port: 6379
            pass: foobared
      roles:
        - ansible-redis

License
-------

GPL3

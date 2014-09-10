Nginx-proxy
=========

Ansible role for nginx-proxy (Ubuntu server).

Role Variables
--------------

    nginx_proxy_listen_port: 80
    nginx_proxy_hostname: web-app
    nginx_proxy_locations:
      '/' : ['expires max', 'root /home/web-app/web-app/public']

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: webbylab.nginx-proxy

License
-------

MIT

Author Information
------------------

WebbyLab (http://webbylab.com)

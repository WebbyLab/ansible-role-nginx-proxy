Nginx-proxy
=========

Ansible role for nginx-proxy (Ubuntu server).

Role Variables
--------------

    nginx_proxy_listen_port: 80
    nginx_proxy_hostname: web-app
    nginx_proxy_static_locations: [{location: '/static', root: '/home/web-app/web-app/public'}]
    nginx_proxy_pass_locations: [{location: '/api', proxy_pass: 'http://127.0.0.1:8080'}]
    nginx_proxy_try_files: {location: '/', try_files: '/index.html'}

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: webbylab.nginx-proxy
           nginx_proxy_listen_port: 80
           nginx_proxy_hostname: web-app
           nginx_proxy_static_locations: [{location: '/static', root: '/home/web-app/web-app/public'}]
           nginx_proxy_pass_locations: [{location: '/api', proxy_pass: 'http://127.0.0.1:8080'}]
           nginx_proxy_try_files: {location: '/', try_files: '/index.html'}

License
-------

MIT

Author Information
------------------

WebbyLab (http://webbylab.com)

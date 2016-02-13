Nginx-proxy
=========

Ansible role for nginx-proxy (Ubuntu server).

Role Variables
--------------

    nginx_proxy_listen_port: 80
    nginx_proxy_file: proxy
    nginx_proxy_hostname: web-app
    nginx_proxy_static_locations: [{location: '/static', root: '/home/web-app/web-app/public', try_files: '/index.html'}]
    nginx_proxy_pass_locations: [{location: '/api', proxy_pass: 'http://127.0.0.1:8080'}]

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: WebbyLab.nginx-proxy
           nginx_proxy_listen_port: 80
           nginx_proxy_hostname: web-app
           nginx_proxy_static_locations: 
             - {location: '/static', root: '/home/web-app/web-app/public', try_files: '/index.html'}
             - {location: '/assets', alias: '/home/web-app/web-app/assets'}
           nginx_proxy_pass_locations: [{location: '/api', proxy_pass: 'http://127.0.0.1:8080'}]

License
-------

MIT

Author Information
------------------

WebbyLab (http://webbylab.com)

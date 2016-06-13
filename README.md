Nginx-proxy
=========

Ansible role for nginx-proxy (Ubuntu server).

Role Variables
--------------
    nginx_proxy_configuration_name: proxy
    nginx_proxy_listen_port: 80
    nginx_proxy_hostname: web-app
    nginx_proxy_ssl_certificate: ''
    nginx_proxy_ssl_certificate_key: ''
    nginx_proxy_static_locations: [{location: '/static', root: '/home/web-app/web-app/public', try_files: '/index.html'}]
    nginx_proxy_pass_locations: [{location: '/api', proxy_pass: 'http://127.0.0.1:8080'}]

nginx_proxy_ssl_certificate - path to SSL cert file. File will be copied to /etc/nginx/ssl/${nginx_proxy_hostname}.cert
nginx_proxy_ssl_certificate_key - path to SSL key file. File will be copied to /etc/nginx/ssl/${nginx_proxy_hostname}.key

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: WebbyLab.nginx-proxy
           nginx_proxy_listen_port: 80
           nginx_proxy_hostname: web-app
           nginx_proxy_ssl_certificate: files/server.crt
           nginx_proxy_ssl_certificate_key: files/server.key
           nginx_proxy_static_locations:
             - {location: '/static', root: '/home/web-app/web-app/public', try_files: '/index.html'}
             - {location: '/assets', alias: '/home/web-app/web-app/assets'}
           nginx_proxy_pass_locations: [{location: '/api', proxy_pass: 'http://127.0.0.1:8080'}]



 Example Playbook with SSL and HTTP/2
 ------------------------------------

     - hosts: servers
       roles:
          - role: WebbyLab.nginx-proxy
            nginx_proxy_configuration_name: web-app
            nginx_proxy_listen_port: 80 ssl http2
            nginx_proxy_hostname: web-app
            nginx_proxy_ssl_certificate: files/server.crt
            nginx_proxy_ssl_certificate_key: files/server.key
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

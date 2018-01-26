nginx-backend
=========
Configure nginx backends on DigitalOcean Droplets that are configured to listen on the private network (eth1)

Requirements
------------
Be sure to place a directory with your content and ansible-vault encrypted certificate files in the role's **files/** directory.

Role Variables
--------------
**defaults/main.yml** or **group_vars/*group-name***

* *example1*: This is used as the configuration file name used by nginx in site-{available,enabled}.
* *doc_root*: Location for your site's document root.
* *server_name*: This will be what nginx uses to determine what server block to use.


    sites:
      example1:
        doc_root: /var/www/vhosts/example.com
        server_name: example.com

**defaults/main.yml**
* *tls_cert*: Name of your crt file
* *tls_key*: Name of private key file
* *nginx_sync_files*: Name of the directory holding your site's content.


    nginx_sync_files: "example.com"
    tls_cert: "example.crt"
    tls_key: "example.key"


Example Playbook
----------------

    ansible-galaxy install -r requirements.yml

or

    ansible-galaxy install cmndrsp0ck.nginx443-backend

Once it's installed in your **roles** directory, you can use the following in your playbook.

    - hosts: web_node
      roles:
         - { role: cmndrsp0ck.nginx443-backend }
      become: True

License
-------

BSD

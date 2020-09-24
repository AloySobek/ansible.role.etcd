 File              : README.md
 Author            : Rustam Khafizov <super.rustamm@gmail.com>
 Date              : 16.09.2020
 Last Modified Date: 16.09.2020
 Last Modified By  : Rustam Khafizov <super.rustamm@gmail.com>
Role Name
=========

Very simple etcd installation. Main configuration set by user in a playbook

Requirements
------------

For properly work you need to generate tls server peer and probably client tls keys for etcd every etcd member

Role Variables
--------------

- state: 'install', 'uninstall', 'full_uninstall'(removing etcd data)
- data_dir: --data-dir for etcd
- wal_dir: --wal-dir for etcd
- tls: enable tls - this need for transfer already generated keys to host
- server,client,peer_keys_path: path for every type of tls keys( directory )
- ca_cert_file: path to ca cert file( file )
- go_version: version of golang
- etcd_opts: main configuration file, here you can pass all other options for etcd

Dependencies
------------

No dependencies

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

MIT

Author Information
------------------

AloySobek

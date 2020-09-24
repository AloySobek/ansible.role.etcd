Role Name
=========

Installing and configuring etcd cluster with specefied parameters in form of ansible vars( very comfy )

Requirements
------------

For properly work you need to generate tls server peer and probably client tls keys for etcd every etcd member

Role Variables
--------------


- state: 'install', 'uninstall', 'full_uninstall'(removing etcd data)
- version: version of etcd to download
- remote_certs_location: path where to store tls certs on remote host 
- local_ca_cert_file: path where to get tls ca cert file
- local_server_keys_path: path where to get server cert and cert-key files
- local_client_keys_path: path where to get client cert and cert-key files
- local_peer_keys_path: path where to get peer (per host) cert and cert-key files
- ALL etcd parameters: just etcd flags like if you type it in terminal

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

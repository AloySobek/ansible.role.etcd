ANSIBLE.ROLE.ETCD
=========

Installing and configuring ( in yaml format ) etcd cluster as systemd service ( starting and enabling it )

Requirements
------------

For properly work you need to generate tls server peer(per member) and client tls keys

Role Variables
--------------

- state: 'install', 'uninstall', 'full_uninstall'(removing etcd data)
- version: version of etcd to download
- etcd_args: just copy of etcd binary args, see example

Dependencies
------------

No dependencies

Example Playbook
----------------

    - name: configuring etcd_cluster
      hosts: example
      roles:
        - ansible.role.etcd
      vars:
        state: 'install'
        version: '3.3.25'
        local_ca_cert_file: "/where/to/get/ca-cert"
        local_server_keys_path: '/where/to/get/server-keys/' - folder
        local_client_keys_path: '/where/to/get/client-keys/' - folder
        local_peer_keys_path: '/where/to/get/peer-keys/' - folder for every member
        remote_certs_location: '/where/to/store/all/this/keys' - remote folder

        name: example
        data_dir: "/where/data/store"
        wal_dir: "/where/wal-data/store'"
        listen_peer_urls: which ip to listen for other peers(members) of cluster
        listen_client_urls: which ip to listen for client control
        initial_advertise_peer_urls: which ip will be visible for other cluster members
        initial_cluster: list of all cluster member endpoints and their names( etcd=http://...:... )
        initial_cluster_state: 'new' or 'existing'
        initial_cluster_token: join token
        advertise_client_urls: this ips will be visible by clients
        client_cert_auth: true
        cert_file: remote_certs_location
        key_file: remote_certs_location 
        trusted_ca_file: remote_certs_location
        peer_client_cert_auth: true
        peer_cert_file: remote_certs_location
        peer_key_file: remote_certs_location
        peer_trusted_ca_file: remote_certs_location
        enable_v2: true - for flannel

License
-------

MIT

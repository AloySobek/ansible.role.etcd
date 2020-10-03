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
- necessary_dirs: this dirs will be created, default data and wal dirs for etcd
- set_v3: set ETCDCTL_API env variable to use etcd_v3 as default
- service_file: path to service file. This file describe how to start etcd
- remote_certs_dir: path where certs lies on host machine
- local_ca_cert_file: path where ca cert file lies on control machine
- local_server_certs_path: path where server certs lies (directory)
- local_peer_certs_path: path where peer certs  lies (directory)

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
        state: install
        version: 3.3.25
        necessary_dirs:
          - "/var/lib/etcd/data"
          - "/var/lib/etcd/wal"
        set_v3: true
        service_file: "./services/file.service"
        remote_certs_dir: "/path/where/store/certs"
        local_ca_cert_file: "/path/where/ca.pem"
        local_server_certs_dir: "/path/where/server"
        local_peer_certs_dir: "/path/where/peer"

License
-------

MIT

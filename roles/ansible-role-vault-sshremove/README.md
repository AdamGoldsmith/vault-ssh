Role : ansible-role-vault-sshremove
===================================

Unconfigure target's SSH daemon by
* Removing host's trusted user CA keys file
* Removing signed host certificate file
* Removing trusted user CA keys file from sshd_config
* Removing HostCertificate from sshd_config

Currently tested on these Operating Systems
* Oracle Linux/RHEL/CentOS
* Debian/Stretch64

Requirements
------------

* Ansible 2.5 or higher

Role Variables
--------------

defaults/main.yml
```
ssh_user_ca_keys: "/etc/ssh/trusted-user-ca-keys.pem"       # Certificate file for Trusted user CA keys
ssh_host_key: "/etc/ssh/ssh_host_rsa_key"                   # SSH server host key
sshd_conf: "/etc/ssh/sshd_config"                           # SSH service configuration file
```

Dependencies
------------

Requires elevated root privileges

Example Playbook
----------------

```
---

- name: Configure SSH Server
  hosts: ssh_server
  become: yes

  roles:

    - name: Remove SSH config
      role: ansible-role-vault-sshremove
      tags:
        - 'never'
        - 'remove'

```

License
-------

MIT License

Author Information
------------------

Adam Goldsmith


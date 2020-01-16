Role : ansible-role-vault-sshserver
===================================

Configure target's SSH daemon to accept trusted incoming users by
* Write Vault's client signing public key to host's trusted user CA keys file
* Sign server's host public key in Vault
* Adding trusted user CA keys file to sshd_config
* Adding HostKey to sshd_config
* Adding HostCertificate to sshd_config

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
vault_sshkeysignertokenfile: "~/.hashicorp_sshkeysigner_token.json"   # Local file storing sshkeysigner token
vault_addr: "10.1.42.10"                                              # Vault listener address
vault_port: "8200"                                                    # Vault listener port
sshd_conf: "/etc/ssh/sshd_config"                                     # SSH service configuration file
ssh_user_ca_keys: "/etc/ssh/trusted-user-ca-keys.pem"                 # Certificate file for Trusted user CA keys
ssh_host_key: "/etc/ssh/ssh_host_rsa_key"                             # SSH server host key
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
  become: True

  roles:
  
    - name: Configure SSH Server
      role: ansible-role-vault-sshserver
      tags:
        - 'sshserver'
```

License
-------

MIT License

Author Information
------------------

Adam Goldsmith


Role : ansible-role-vault-sshclient
===================================

Configure target's SSH user configuration for trusted SSH connectivity
* Write Vault's host signing public key to system's known hosts file
* Sign user's public key in Vault
* Write signed key to user's certificate file

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
ssh_user_name: "ansible"                                              # Owner of SSH public key to sign
ssh_user_key: "/home/ansible/.ssh/id_rsa"                             # Location of user's SSH public key
ssh_known_hosts: "/etc/ssh/ssh_known_hosts"                           # Loation of system's known hosts file
```

Dependencies
------------

Requires elevated root privileges

Example Playbook
----------------

```
---

- name: Configure SSH Client
  hosts: ssh_client
  become: yes

  roles:

    - name: Configure SSH Client
      role: ansible-role-vault-sshclient
      tags:
        - 'sshclient'
```

License
-------

MIT License

Author Information
------------------

Adam Goldsmith


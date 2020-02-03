# SSH Server & Client Certificate Authentication

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Use Hashicorp Vault to sign user and host public SSH keys to allow time-leased SSH access and host authenticity

See [hashicorp documentation](https://www.vaultproject.io/docs/secrets/ssh/signed-ssh-certificates.html) for details

### Overview of SSH key signing process
![Alt text](/images/key-signing-overview.png "Key signing overview")

>__Note__: Highly recommended to have deployed Vault + Consul cluster using the Ansible playbooks at this [repository](https://github.com/AdamGoldsmith/consul-vault), or at least peruse for better understanding


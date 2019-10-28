# CentOS 7 Testing VM Ansible Playbook

Playbook and Vagrantfile to set up a CentOS 7 VM with tools and default configurations I like to have.

Vagrant provider is VirtualBox. A host-only adapter (enp0s8) is also configured and enabled by default so the host can connect to the VM.

## Running

Just 

```
# Provision VM without most recent packages.
vagrant up
# Or upgrade all packages during provisioning.
VM_UPGRADE_PKG=true vagrant up
```
to run.

## Setting a default user password
Passwords passed to the Ansible user module need to be pre-hashed. This command can generate the hash:
```
ansible all -i localhost, -m debug -a "msg={{ 'mypassword' | password_hash('sha512', 'mysecretsalt') }}"
```



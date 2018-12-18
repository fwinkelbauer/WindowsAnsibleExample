# Windows Ansible Example

This repository contains a very small example on how to setup and use Ansible on Windows using a virtual machine.

## Target Machine

- Copy the [ConfigureRemotingForAnsible.ps1](https://github.com/ansible/ansible/blob/devel/examples/scripts/ConfigureRemotingForAnsible.ps1) script onto the target computer
- Run the script on the target computer:

``` powershell
.\ConfigureRemotingForAnsible.ps1 -EnableCredSSP
```

- Enter the correct IP address, username and password of the target machine in `.\windows\hosts.ini`.

**Note:** Ansible offers [several authentication options](https://docs.ansible.com/ansible/latest/user_guide/windows_winrm.html#authentication-options).
This example uses CredSSP because of its credential delegation capabilities (which can be used to authenticate on a computer in a different domain).

## Ansible Box

Prerequisites:

- Enable Hyper-V, or install [Virtualbox](https://www.virtualbox.org/)
- Install [Vagrant](https://www.vagrantup.com/) (e.g. `choco install vagrant`)

Afterwards you can start the Ansible VM using a Powershell Administrator terminal:

``` powershell
# Hyper-V SMB username: <user>@<domain> (e.g. someuser@mydomain.com)
vagrant up
vagrant ssh
cd /vagrant/windows
ansible windows -i hosts.ini -m win_ping
ansible-playbook -i hosts.ini sample-playbook.yaml --syntax-check
ansible-playbook -i hosts.ini sample-playbook.yaml
exit
vagrant halt
```

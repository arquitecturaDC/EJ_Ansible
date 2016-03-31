# EJ_Ansible
## Instalar Ansible Controller
>http://docs.ansible.com/ansible/intro_installation.html

Ejemplo en Ubuntu 14.04:
```sh
$ sudo apt-get install software-properties-common
$ sudo apt-add-repository ppa:ansible/ansible
$ sudo apt-get update
$ sudo apt-get install ansible
```
## Especificar el archivo hosts
```sh
[vpn]
[removevpn]
[elasticsearch_master_data_nodes]
node01
node02
node03
[git]
node01
```
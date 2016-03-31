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
En el archivo hosts se deberán especificar los nodos sobre los cuales se ejecutarán las acciones.
Será posible agrupar los mismos en categorías utilizando la nomenclatura **[categoria]**.
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

## Authenticación SSH con usuario root y clave pública
Acciones a realizar el Ansible Controller

```sh
$ sudo -s
$ ssh-kegen
```

Se generarán los siguientes archivos:
```sh
$ ls /root/.ssh/
id_rsa  id_rsa.pub  known_hosts
```

Para garantizar la autenticación con usuario root por ssh se deberá adicionar el archivo **/root/.ssh/authorized_keys** la clave pública del controller presente en **/root/.ssh/id_rsa.pub**

Ejemplo del archivo authorized_keys:

```sh
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC2PPXTHVQt8HlXt4gzUu4W2BZ3Gk8h6ADYqXUl3Kg5YrFDaT343wr5B0XeO7zT9GagYjCE1RoW4isDtFSIIdsY1qanwRRrSx3KNxQ47GHc5NLV6XcxoVrWa+YnzI3DjFcxJ2SxPHesxOOUA3UP8EPKRnN9DAoSmmnQnZ5zqmMI0inPDb1DxO6+yBBXkiK3LgcwSuSKBLVOLDrQ0hlX3Zf3b4UFdvcsn4jMI8sPD4HwT6i7729Ns6oXEBrbAGlxbYWez2dDeeAXPVsvCX+i5tQlEfqd92IF86YdRmFJt0l2QjhgKDosaKzJkI5Vac0C3TwdGjSuLitqMfLxSgovPior root@ubuntu
```

## Ejemplo playbook
El ejemplo a continuación instala git y crea un archivo en el /opt
```sh
$ more ~/ansible-tinc/install_git.yml
---

- hosts: git
  become: true
  tasks:
  - name: Install package
    apt: name=git state=latest
  - name: Crear archivo en /opt
    file: path=/opt/archivoAnsible.prueba state=touch
```

Se puede descargar de los ejemplos presente en el proyecto.

# Ansible-practice

## Informacion relevante
Funcionamiento: 

Se asegura que el estado del servidor es el deseado despues de terminar su ejecución

- Inventory: Fichero usado para agrupar y definir los diferentes hosts y algunas variables
- Playbooks: Archivos para describir las tareas que queremos que se ejecuten sobre host/s

ANSIBLE GALAXY: Repositorio publico de proyectos ansible creados por la comunidad

Documentacion: https://docs.ansible.com/ansible/2.8/modules/list_of_packaging_modules.html

## Configurar conexion ssh con servidores remotos

    $ curl https://github.com/agevega.keys >> ~/.ssh/authorized_keys

## Instalar Ansible en maquina Master

    $ sudo apt-get update
    $ sudo apt-add-repository -y ppa:ansible/ansible
    $ sudo apt-get update

    $ sudo apt-get install -y ansible

    $ ansible --version


## Comandos Ansible Ad-hoc

Parametros:
* -i --> direccion del inventario (aqui se detallan las variables como el usuario con el que nos conectaremos o la clave ssh)
* -m --> modulo de ansible a usar
* -a --> parametros del modulo 
* -b --> become root
* -K --> clave root
* -v --> verbose

    $ ansible agevega.com -m ping

    $ ansible aws -m ping -i hosts/inventory.ini

    $ ansible aws -i hosts/inventory.ini -a 'echo hello world!'

    $ ansible aws -i hosts/inventory.ini -m apt -a 'name=zsh state=present' -b -K


## Comandos Ansible Playbooks

    $ ansible-playbook -i hosts/inventory.ini playbooks/test.yml

    $ ansible-playbook -i hosts/inventory.ini playbooks/test.yml -K


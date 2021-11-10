Jibri Docker
=========

Ce rôle sert à déployer/remettre en état un serveur Jibri via le projet Docker Compose officiel de Jitsi Meet. 

Requirements
------------

### Matériel
* 8 vcore + 16 Go de RAM

### Système d'exploitation
* Ubuntu 20.04 (seul SE testé)

### Docker et Docker Compose
* IMPORTANT : Docker et Docker Compose NE SONT PAS installés par le rôle
* NOTE : Les paquets .deb disponibles dans Ubuntu 20.04 (universe) sont suffisants

Role Variables
--------------

### defaults/main.yml

Dependencies
------------

Aucune dépendance à d'autres rôles Ansible.

Example Playbook
----------------

```
- name: "Deployer un serveur Jibri via Docker Compose"
  hosts: 
    - all
  vars:
    # Supplanter ici les variables du role 'ansible-jibri-role' au besoin
    utilisateur_unix: "jibri826"
    jitsi_domaine: "jitsi.mondomaine.net"
    # Les 2 variables ci-bas doivent être == à celles du serveur Jitsi
    jibri_xmpp_mdp: "SECRET_A_CHANGER_01"
    jibri_enregistreur_mdp: "SECRET_A_CHANGER_02"

  pre_tasks:
    - name: "Installer Docker et Docker Compose"
      apt:
        name: docker.io, docker-compose
        state: present
      become: yes
  roles:
    - ansible-jibri-role
```

License
-------

GPL-3.0-only

Author Information
------------------

Mathieu GP, admin. sys. pour Coderbunker

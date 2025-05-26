ansible-project/
├── ansible.cfg
├── inventory
├── README.md
│   # 🛠️ Ansible Ubuntu Web Infrastructure
│   
│   ## 📌 Description
│   
│   Ce projet Ansible automatise le déploiement d'une infrastructure web sur des serveurs **Ubuntu 22.04**. Il s’appuie sur une architecture modulaire à base de rôles et est conçu pour les environnements de développement et de test. Il permet de :
│   
│   - Installer et configurer un serveur **Apache2**
│   - Activer le pare-feu avec **UFW** pour autoriser HTTP
│   - Déployer un site web simple avec contenu statique
│   - Installer **PHP** et **MariaDB** pour une base LAMP
│   
│   ---
│   
│   ## 📂 Structure du projet
│   
│   ```
│   ansible-project/
│   ├── ansible.cfg              # Fichier de configuration Ansible
│   ├── inventory                # Inventaire des hôtes (dev, test)
│   ├── playbooks/               # Contient les playbooks principaux
│   │   ├── apache.yml           # Déploiement du serveur Apache
│   │   ├── webcontent.yml       # Gestion du contenu web
│   │   └── packages.yml         # Installation de PHP et MariaDB
│   ├── roles/                   # Rôles Ansible (apache, lamp, webcontent)
│   └── README.md                # Documentation du projet
│   ```
│   
│   ---
│   
│   ## 🚀 Lancement rapide
│   
│   ### 1. Préparation
│   
│   Assurez-vous que :
│   - Ansible est installé sur votre machine de contrôle
│   - Vos hôtes sont accessibles via SSH (ex : Vagrant)
│   - Vos machines utilisent Ubuntu 22.04
│   
│   ### 2. Configuration de l'inventaire
│   
│   Exemple :
│   
│   ```ini
│   [dev]
│   192.168.33.10
│   
│   [test]
│   192.168.33.11
│   ```
│   
│   ### 3. Exécution des playbooks
│   
│   ```bash
│   ansible-playbook playbooks/apache.yml
│   ansible-playbook playbooks/webcontent.yml
│   ansible-playbook playbooks/packages.yml
│   ```
│   
│   ### 4. Vérification
│   
│   - Accédez à `http://192.168.33.10` pour vérifier Apache
│   - Accédez à `http://192.168.33.10/devdirectory/` pour le contenu déployé
│   
│   ---
│   
│   ## 📦 Rôles inclus
│   
│   - **apache** : installe apache2, configure UFW, déploie un fichier HTML et un répertoire symbolique
│   - **webcontent** : gère la structure de fichiers et de contenu (optionnel si fusionné avec apache)
│   - **lamp** : installe php, mariadb-server et met à jour les paquets
│   
│   ---
│   
│   ## 🧱 Technologies
│   
│   - Ansible
│   - Apache2
│   - PHP
│   - MariaDB
│   - Ubuntu 22.04
│   - Vagrant (optionnel pour tests)
│   
│   ---
│   
│   ## 👨‍💻 Auteur
│   
│   Projet réalisé avec ❤️ pour l'apprentissage et la pratique DevOps
├── playbooks/
│   ├── apache.yml
│   │       ---
│   │       - name: Deploy Apache Web Server
│   │         hosts: dev
│   │         become: yes
│   │         roles:
│   │           - apache
│   ├── webcontent.yml
│   │       ---
│   │       - name: Manage Web Content
│   │         hosts: dev
│   │         become: yes
│   │         roles:
│   │           - webcontent
│   └── packages.yml
│           ---
│           - name: Install PHP and MariaDB
│             hosts: test
│             become: yes
│             roles:
│               - lamp
├── roles/
│   ├── apache/
│   │   ├── tasks/
│   │   │   └── main.yml
│   │   ├── handlers/
│   │   │   └── main.yml
│   │   ├── templates/
│   │   │   └── index.html.j2
│   │   ├── defaults/
│   │   │   └── main.yml
│   │   └── meta/
│   │       └── main.yml
│   ├── webcontent/
│   │   ├── tasks/
│   │   │   └── main.yml
│   │   ├── handlers/
│   │   │   └── main.yml
│   │   └── defaults/
│   │       └── main.yml
│   └── lamp/
│       ├── tasks/
│       │   └── main.yml
│       ├── defaults/
│       │   └── main.yml
│       └── meta/
│           └── main.yml


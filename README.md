Rapport technique : Automatisation du serveur MySQL
1. Déploiement du Playbook

Le déploiement a été réalisé via un rôle Ansible structuré. Comme on peut le voir sur la capture ci-dessous, l'intégralité des tâches a été exécutée avec succès (failed=0).

<img width="1790" height="492" alt="playbook launch" src="https://github.com/user-attachments/assets/cf4aff2d-f0a8-42e0-940f-d9d4d0187b50" />

    Commentaire : On observe le passage des différentes étapes : installation des paquets, configuration du service et application du template. Le RECAP montre 7 tâches réussies et 3 changements effectifs sur le système.

2. Gestion de la Sécurité (Ansible Vault)

Pour garantir la confidentialité des identifiants (comme le mysql_root_password), on a utilisé Ansible Vault. Cette méthode permet de chiffrer les variables sensibles en AES-256.

<img width="629" height="140" alt="vault chiffre" src="https://github.com/user-attachments/assets/186b2ab9-0b57-458b-9f72-eeadfd6e9362" />
    
    Commentaire : Le fichier vars/vault.yml est illisible sans la clé de coffre, ce qui sécurise le dépôt de code sur GitHub contre les fuites de secrets.

3. Validation de l'état opérationnel

Pour confirmer le succès du déploiement automatisé, on a vérifié l'état des processus système. Malgré les limitations de l'environnement conteneurisé (absence de gestionnaire de services standard), la commande ps aux confirme que le démon MySQL a été correctement initialisé par Ansible.

<img width="1641" height="74" alt="mysql running" src="https://github.com/user-attachments/assets/5face66e-d307-4b2a-a148-72539cfcd367" />

    Commentaire : Le processus /usr/sbin/mysqld est actif.

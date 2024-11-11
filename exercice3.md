# EXERCIE 3 "QUIZ"

-----
### Donne une ligne de commande bash qui permet de lister la liste des utilisateurs d'un système Linux
`cut -d: -f1 /etc/passwd`
### Cette commande extrait les noms des utilisateurs à partir du fichier /etc/passwd, où chaque utilisateur a une entrée.
-----
### 2. Quelle commande bash permet de changer les droits du fichier myfile en rwxr—r-- ?
`chmod 744 myfile`
### Le mode 744 définit les permissions de rwxr--r-- pour le propriétaire, le groupe et les autres utilisateurs respectivement.
-----
### 3. Comment faire pour que les fichiers pdf d'un dépôt local git ne soient pas pris en compte lors d'un git push ?
`echo '*.pdf' >> .gitignore
git add .gitignore
git commit -m "Ajout des fichiers PDF à .gitignore"`
### Cela empêchera les fichiers PDF d'être suivis et poussés dans le dépôt Git.
----
### 4. Basculer sur la branche main (la branche de destination de la fusion) :
`git checkout main`

#### 1. Fusionner la branche test_valide dans main :
`git merge test_valide`

#### 2. Gérer les conflits si nécessaire : Si des conflits surviennent, Git vous le signalera. Vous devrez alors résoudre les conflits dans les fichiers concernés, les marquer comme résolus et compléter la fusion avec :
`git add <fichiers_concernés>
git commit`

#### 3. Pousser les changements vers le dépôt distant (optionnel) :
`git push origin main`

----

### 5. Donne la(les) ligne(s) de commande(s) bash pour afficher le texte suivant 

- `echo 'Malgré le prix élevé de 100$, il a dit "Bonjour !" au vendeur :'`
- `echo '- "Bonjour est-ce que ce clavier fonctionne bien ?"'`
- `echo '- "Evidemment ! On peut tout écrire avec, que ce soit des pipe | ou bien des backslash \\ !"'`
- `echo '- "Même des tildes ~ ?"'`
- `echo '- "Evidemment !"'`

### 6. La commande jobs -l donne le résultat ci-dessous :

#### Pour mettre en avant le processus gedit, vous pouvez utiliser la commande fg suivie du numéro du job associé, ici [1] pour gedit.
----
### 7. Quels matériels réseaux sont sur la couche 2 et la couche 3 du modèle OSI ? Donne leurs spécificités.

Couxhe 2 (Couche de liaison de données) :
- Switch (commutateur) - Dispositif qui connecte plusieurs périphériques sur le même réseau en utilisant des adresses MAC pour transférer les données.
- Pont (bridge) - Dispositif qui divise un réseau en segments et filtre les données en fonction des adresses MAC
- Point d'accès Wi-Fi (AP) - Bien que fonctionnant aussi en couche 1 pour la transmission sans fil, un point d'accès utilise la couche 2 pour la gestion des adresses MAC dans les réseaux Wi-Fi.
- Concentrateur Ethernet (hub) - Bien qu'il soit obsolète, il connecte plusieurs périphériques sur un réseau local en transmettant les signaux à tous les ports (fonctionne aussi en couche 1 mais agit en couche 2 pour la transmission des trames).

Couche 3 (Couche réseau) :
- Routeur - Dispositif qui dirige les paquets de données entre différents réseaux en utilisant des adresses IP
- Switch de couche 3 (switch avec routage) - Switch capable de faire le routage entre réseaux locaux (VLANs), combinant les fonctionnalités des couches 2 et 3.
- Pare-feu (firewall) - Bien que pouvant opérer sur plusieurs couches, un pare-feu configuré pour le filtrage IP et le routage opère en couche 3.

----
### 8. Quels sont les équivalent PowerShell des commandes bash cd, cp, mkdir, ls.

  BASH  --  POWERSHEL
-  cd   --  Set-Location <chemin>
-  cp   --  Copy-Item <source> <destination>
-  mkdir -- New-Item -ItemType Directory -Name <nom_du_dossier>
-  ls   --  Get-ChildItem
----
### 9. Dans la trame ethernet, qu'est-ce que le payload ?

Dans une trame Ethernet, le payload (ou charge utile) est la portion qui contient les données transportées pour les couches supérieures, comme IP ou les données de l'utilisateur. Il s’agit de l’information principale que la trame transmet, avec une taille comprise entre 46 et 1500 octets, en excluant les en-têtes et le contrôle d’erreurs.

### 10. Pourquoi les classes IP sont remplacées par le CIDR ?

Les classes IP ont été remplacées par le CIDR (Classless Inter-Domain Routing) pour optimiser l’utilisation des adresses IP et améliorer la flexibilité du routage. Voici les raisons principales de ce remplacement :
Économie d'adresses IP : Les classes IP (A, B, C) imposaient des tailles de sous-réseaux fixes, souvent surdimensionnées pour les besoins réels. Le CIDR permet d’allouer des plages d'adresses de tailles ajustées à la demande, réduisant le gaspillage d'adresses.
Routage plus efficace : Le CIDR utilise une notation par longueur de préfixe (par exemple, 192.168.0.0/24), permettant de regrouper plusieurs réseaux sous un seul préfixe. Cela simplifie les tables de routage et améliore l'efficacité du routage inter-domaine.
Scalabilité accrue : Avec la croissance rapide d’Internet, le CIDR a permis de mieux gérer l’expansion du réseau et de retarder l’épuisement des adresses IPv4 en répartissant plus efficacement les adresses disponibles.
En résumé, le CIDR a remplacé les classes IP pour une utilisation plus rationnelle et flexible des adresses IP, répondant mieux aux besoins variés des réseaux modernes.





















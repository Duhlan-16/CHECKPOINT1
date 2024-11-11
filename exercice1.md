
# Partitionnement sur Debian

Cette procédure explique comment créer une partition de données et une partition swap sur un disque secondaire (`/dev/sdb`) sur Debian.

## 1. Ouvrir l’outil `fdisk`

Lancez `fdisk` pour le disque `/dev/sdb` :
```bash
sudo fdisk /dev/sdb
```

## 2. Créer une partition de données de 6 Go

- Tapez `n` pour créer une nouvelle partition.
- Choisissez `p` pour une partition principale (primary).
- Laissez le numéro de partition par défaut (probablement 1).
- Pour le premier secteur, laissez la valeur par défaut.
- Pour le dernier secteur, entrez `+6G` pour limiter la taille à 6 Go.

## 3. Créer une partition de swap avec l’espace restant

- Tapez `n` pour créer une autre partition.
- Choisissez `p` pour une partition principale.
- Laissez le numéro de partition par défaut (probablement 2).
- Laissez les valeurs par défaut pour occuper tout l’espace restant.

## 4. Changer le type de la partition en swap

- Tapez `t` pour changer le type de partition.
- Sélectionnez la partition 2.
- Entrez le code `82` pour définir cette partition comme Linux swap.

## 5. Enregistrer les modifications et quitter fdisk

- Tapez `w` pour écrire les modifications sur le disque et quitter fdisk.

## 6. Formater les partitions

### Formater la partition de données en ext4
```bash
sudo mkfs.ext4 -L DATA /dev/sdb1
```

### Initialiser la partition swap
```bash
sudo mkswap -L SWAP /dev/sdb2
```

## 7. Activer le swap

### Désactiver le swap existant (si nécessaire) :
```bash
sudo swapoff -a
```

### Activer le nouveau swap sur /dev/sdb2 :
```bash
sudo swapon /dev/sdb2
```

### Vérifier que le swap est activé :
```bash
swapon --show
```

## 8. Montage automatique de la partition de données

### Créer le point de montage pour DATA
```bash
sudo mkdir -p /mnt/data
```

### Obtenir l’UUID de la partition /dev/sdb1
```bash
blkid /dev/sdb1
```

### Ajouter une entrée dans /etc/fstab

Ouvrez `/etc/fstab` dans un éditeur de texte :
```bash
sudo nano /etc/fstab
```

Ajoutez les lignes suivantes, en remplaçant `<UUID_DATA>` par l'UUID obtenu pour `/dev/sdb1` et `<UUID_SWAP>` par l'UUID de `/dev/sdb2` :
```plaintext
UUID=<UUID_DATA> /mnt/data ext4 defaults 0 2
UUID=<UUID_SWAP> none swap sw 0 0
```

Enregistrez et quittez l’éditeur.

### Monter toutes les partitions spécifiées dans /etc/fstab
```bash
sudo mount -a
```

### Vérifier le montage
```bash
df -h
```

## 9. Vérifications supplémentaires

### Liste des partitions et leurs tailles
```bash
sudo fdisk -l /dev/sdb
```

### Type de système de fichiers et UUID
```bash
blkid /dev/sdb1
blkid /dev/sdb2
```

### Vérification finale du swap
```bash
swapon --show
```

### Contenu de /etc/fstab pour montrer la configuration
```bash
cat /etc/fstab
```

Après avoir suivi ces étapes, votre partition de données sera montée automatiquement au démarrage et le swap sera activé.

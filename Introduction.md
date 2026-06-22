# Introduction

## Qu'est-ce qu'une distribution Linux ? 

Une distribution Linux (ou "distro") est un système d'exploitation complet basé sur le noyau Linux, accompagné d'un ensemble de logiciels, d'outils et de configurations. Elle comprend :

- **Le noyau Linux** : cœur du système d'exploitation
- **Un système d'initialisation** :  systemd, OpenRC, runit... 
- **Un shell** : bash, zsh, fish...
- **Un gestionnaire de paquets** : apt, pacman, dnf...
- **Des applications** : navigateur, éditeur de texte, outils système... 
- **Un environnement de bureau** (optionnel) : GNOME, KDE, Xfce...

### Différence entre le noyau et la distribution

```
┌─────────────────────────────────────┐
│     Applications utilisateur        │
├─────────────────────────────────────┤
│   Bibliothèques et outils système   │
├─────────────────────────────────────┤
│         Noyau Linux (Kernel)        │
├─────────────────────────────────────┤
│            Matériel (CPU, RAM...)   │
└─────────────────────────────────────┘
```

Le **noyau Linux** est uniquement le cœur du système qui gère le matériel et les ressources.  La **distribution** ajoute tous les outils, bibliothèques et applications nécessaires pour avoir un système utilisable.

## Pourquoi créer une distribution personnalisée ? 

### Avantages

1. **Optimisation** :  Adapter le système à des besoins spécifiques (serveur, desktop, embarqué)
2. **Sécurité** : Contrôler exactement ce qui est installé et supprimer les composants inutiles
3. **Légèreté** : Créer un système minimal sans bloatware
4. **Apprentissage** : Comprendre le fonctionnement interne de Linux en profondeur
5. **Déploiement** : Créer des images standardisées pour une organisation ou un projet

### Cas d'usage

- **Systèmes embarqués** : Routeurs, IoT, systèmes industriels avec ressources limitées
- **Sécurité** : Tests de pénétration, forensics, audits de sécurité
- **Éducation** :  Environnements d'apprentissage standardisés pour formations
- **Entreprise** :  Postes de travail préconfigurés avec logiciels et politiques spécifiques
- **Recovery** : Systèmes de récupération et maintenance (live USB)
- **Gaming** : Distributions optimisées pour le jeu (ex: SteamOS)
- **Serveurs** :  Configurations serveur minimales et sécurisées

## Exemples de distributions personnalisées existantes

### Kali Linux
- **Base** : Debian
- **Objectif** : Tests de sécurité et pentesting
- **Caractéristiques** : Plus de 600 outils de sécurité préinstallés (Metasploit, Nmap, Wireshark, etc.)
- **Public** : Professionnels de la cybersécurité, ethical hackers

### Linux From Scratch (LFS)
- **Base** : Construction depuis zéro (aucune base préexistante)
- **Objectif** : Apprentissage approfondi du système Linux
- **Caractéristiques** : Compilation manuelle de tous les composants, contrôle total
- **Public** : Étudiants, passionnés souhaitant maîtriser Linux en profondeur

### TinyCore Linux
- **Base** :  Système minimal indépendant
- **Objectif** :  Extrême légèreté (11 MB pour le système de base)
- **Caractéristiques** : Fonctionne entièrement en RAM, démarrage ultra-rapide
- **Public** : Vieux matériel, systèmes embarqués, kiosques

### Ubuntu Server Live
- **Base** : Ubuntu
- **Objectif** : Déploiement serveur simplifié
- **Caractéristiques** : Installation automatisée via cloud-init, snapshots
- **Public** :  Administrateurs système, datacenters

### Raspberry Pi OS
- **Base** : Debian
- **Objectif** : Optimisé pour Raspberry Pi
- **Caractéristiques** : Support ARM optimisé, outils éducatifs (Scratch, Python)
- **Public** : Makers, éducation, projets IoT

### Tails
- **Base** :  Debian
- **Objectif** : Confidentialité et anonymat
- **Caractéristiques** : Tout le trafic passe par Tor, ne laisse pas de traces
- **Public** :  Journalistes, activistes, utilisateurs soucieux de la vie privée

### SteamOS
- **Base** : Arch Linux
- **Objectif** : Gaming sur PC et Steam Deck
- **Caractéristiques** : Proton intégré, interface gaming, optimisations graphiques
- **Public** :  Gamers

## Prérequis techniques

Avant de commencer la création d'une distribution personnalisée, il est important de maîtriser : 

### Compétences Linux de base
- Navigation en ligne de commande (cd, ls, cp, mv, rm, etc.)
- Gestion des permissions (chmod, chown, sudo)
- Édition de fichiers (vim, nano)
- Gestion des processus (ps, top, kill)

### Structure du système de fichiers
- **FHS (Filesystem Hierarchy Standard)** : 
  - `/bin` : Binaires essentiels
  - `/etc` : Fichiers de configuration
  - `/home` : Répertoires utilisateurs
  - `/boot` : Fichiers de démarrage (kernel, initrd)
  - `/usr` : Applications et bibliothèques
  - `/var` : Données variables (logs, cache)

### Gestion des paquets
- Comprendre apt (Debian/Ubuntu), pacman (Arch), dnf (Fedora)
- Installation, mise à jour, suppression de paquets
- Résolution des dépendances

### Processus de démarrage (boot)
1. **BIOS/UEFI** : Initialisation du matériel
2. **Bootloader** :  GRUB charge le noyau
3. **Kernel** : Initialisation du système
4. **Init system** : systemd lance les services
5. **Login** : Accès utilisateur

### Compilation de logiciels
- Utilisation de `make`, `gcc`
- Configuration :  `./configure`
- Compilation : `make`
- Installation : `make install`

### Scripts shell
- Bash scripting de base
- Variables, boucles, conditions
- Automatisation de tâches

## Concepts clés à comprendre

### Le noyau Linux (Kernel)
Le noyau est le cœur du système.  Il gère : 
- **Gestion des processus** :  Scheduling, multitâche
- **Gestion de la mémoire** : RAM, swap, virtual memory
- **Pilotes matériels** : Communication avec CPU, disques, réseau
- **Système de fichiers** : ext4, btrfs, xfs... 
- **Sécurité** : Permissions, SELinux, AppArmor

### L'espace utilisateur (Userspace)
Tout ce qui s'exécute au-dessus du noyau : 
- Shell et utilitaires
- Applications
- Services système
- Interfaces graphiques

### Les dépendances
Les logiciels dépendent de bibliothèques partagées :
```bash
# Voir les dépendances d'un binaire
ldd /bin/bash
```

### Les systèmes de fichiers
- **ext4** : Standard Linux, fiable
- **btrfs** :  Moderne, snapshots, compression
- **xfs** :  Haute performance
- **squashfs** : Lecture seule, compression (utilisé pour les live CD)

## Outils essentiels

Pour créer une distribution, vous utiliserez :

- **debootstrap** : Créer un système Debian minimal
- **chroot** : Tester et modifier un système depuis un autre
- **mksquashfs** : Créer des images compressées
- **grub-install** : Installer le bootloader
- **genisoimage / xorriso** : Créer des images ISO
- **qemu** : Tester les images dans une machine virtuelle

## Structure d'une distribution Linux

```
Distribution Linux
│
├── Noyau Linux (kernel)
│   ├── Pilotes matériels
│   ├── Gestion processus
│   └── Système de fichiers
│
├── Système d'initialisation
│   ├── systemd (moderne)
│   ├── OpenRC (simple)
│   └── runit (minimal)
│
├── Bibliothèques système
│   ├── glibc (GNU C Library)
│   ├── libssl (cryptographie)
│   └── autres libs partagées
│
├── Shell et utilitaires
│   ├── bash, zsh, fish
│   ├── coreutils (ls, cp, mv...)
│   └── util-linux (mount, fdisk...)
│
├── Gestionnaire de paquets
│   ├── apt (Debian/Ubuntu)
│   ├── pacman (Arch)
│   └── dnf (Fedora)
│
└── Applications
    ├── Environnement de bureau (optionnel)
    ├── Navigateur web
    ├── Éditeurs de texte
    └── Outils spécifiques
```

## Défis de la création d'une distribution

### Défis techniques
- **Dépendances complexes** : Gérer les milliers de dépendances entre paquets
- **Compatibilité matérielle** : Support de différents CPU, GPU, périphériques
- **Taille de l'image** : Équilibre entre complétude et légèreté
- **Sécurité** : Patches, mises à jour, durcissement du système

### Défis de maintenance
- **Mises à jour** : Suivre les mises à jour de sécurité
- **Tests** : Vérifier que tout fonctionne sur différentes configurations
- **Documentation** : Maintenir une documentation à jour
- **Support communautaire** : Répondre aux questions, gérer les bugs

## Approches possibles

Il existe plusieurs niveaux de personnalisation :

1. **Remastering** : Modifier une ISO existante (le plus simple)
   - Outils :  Cubic, Remastersys
   - Temps :  Quelques heures
   - Contrôle :  Limité

2. **Build system** : Utiliser des outils officiels
   - Outils :  live-build, archiso
   - Temps :  Quelques jours
   - Contrôle : Bon

3. **From Scratch** : Tout compiler manuellement
   - Guide : Linux From Scratch
   - Temps : Plusieurs semaines
   - Contrôle : Total

## Navigation

⬅️ Précédent : [Accueil](../README.md)  
➡️ Suivant : [Choix de la base](02-choix-base.md)

# linux-distro-personnalisee
Rapport complet sur la création d'une distribution Linux personnalisée
# Distribution Linux Personnalisée - Projet d'évaluation

## 📋 Table des matières

1. [Introduction](docs/01-introduction.md)
2. [Choix de la base](docs/02-choix-base.md)
3. [Méthodes de création](docs/03-methodes-creation. md)
4. [Installation et configuration](docs/04-installation-configuration.md)
5. [Personnalisation avancée](docs/05-personnalisation. md)
6. [Tests et déploiement](docs/06-tests-deploiement.md)
7. [Conclusion](docs/07-conclusion.md)

## 🎯 Objectif du projet

Ce rapport présente le processus complet de création d'une distribution Linux personnalisée, depuis la sélection d'une base jusqu'à la génération d'une image bootable. 

## 🚀 Démarrage rapide

Consultez la section [Méthodes de création](docs/03-methodes-creation.md) pour des exemples pratiques.

## 📚 Ressources

- [Linux From Scratch](http://www.linuxfromscratch.org/)
- [Debian Live Manual](https://live-team.pages.debian.net/live-manual/)
- [Archiso Documentation](https://wiki.archlinux.org/title/Archiso)

## 📖 Structure du projet

```
linux-distro-personnalisee/
├── README.md                          # Page d'accueil du projet
├── docs/                              # Documentation complète
│   ├── 01-introduction.md
│   ├── 02-choix-base.md
│   ├── 03-methodes-creation.md
│   ├── 04-installation-configuration.md
│   ├── 05-personnalisation.md
│   ├── 06-tests-deploiement.md
│   └── 07-conclusion.md
├── scripts/                           # Scripts automatisés
│   ├── live-build/
│   │   └── build. sh
│   └── archiso/
│       └── build-arch.sh
└── exemples/                          # Fichiers d'exemple
    ├── packages-lists/
    └── hooks/
```

## 🔧 Méthodes couvertes

Ce projet explore plusieurs méthodes de création de distributions Linux : 

- **Live Build (Debian)** - Outil officiel Debian
- **Archiso (Arch Linux)** - Rolling release et minimalisme
- **Cubic (Ubuntu)** - Interface graphique conviviale
- **Linux From Scratch** - Approche pédagogique complète

## 💡 Pourquoi ce projet ? 

Créer une distribution Linux personnalisée permet de : 

✅ Comprendre en profondeur le fonctionnement de Linux  
✅ Optimiser un système pour des besoins spécifiques  
✅ Maîtriser les composants essentiels (kernel, bootloader, init system)  
✅ Développer des compétences en administration système avancée  

## 👨‍💻 Auteur

**Fantamaini** - Projet d'évaluation Linux  
Date :  Décembre 2025

## 📝 Licence

Ce projet est à but éducatif. 

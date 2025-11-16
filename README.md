# Docodile

**Plateforme IA de Compilation Documentaire Automatisée**

Docodile est une solution d'intelligence artificielle qui automatise la génération de documents techniques complexes tels que les Vendor Data Books (VDB), les rapports USO (Utilisation en Service des Ouvrages), et autres documentations industrielles critiques.

[![Website](https://img.shields.io/badge/website-docodile.fr-00C896)](https://docodile.fr)
[![Demo](https://img.shields.io/badge/demo-available-00C896)](https://docodile.fr/demo)

---

## 🎯 Problématique

Dans les industries à haute exigence (nucléaire, aérospatial, manufacturing), la compilation de documentation technique représente un défi majeur :

- **Volumes massifs** : Des milliers de pages de documentation fournisseur à traiter
- **Complexité élevée** : Correspondances complexes entre fichiers sources et structures cibles
- **Risque d'erreur humaine** : Processus manuels sujets aux oublis et incohérences
- **Temps considérable** : Des jours ou semaines de travail pour un seul document
- **Expertise requise** : Connaissance approfondie des standards industriels

**Conséquence** : Délais projet allongés, coûts élevés, qualité variable.

---

## ✨ Solution Docodile

Docodile automatise la compilation documentaire grâce à l'intelligence artificielle :

### Fonctionnalités Clés

- **🤖 Analyse Intelligente** : Détection automatique de la structure des documents sources via IA
- **🎯 Précision 90%** : Matching AI entre fichiers sources et sections cibles
- **⚡ Gain de Temps** : Réduction de 70-80% du temps de compilation
- **📊 Multi-Formats** : Support Excel, PDF, Word, et autres formats industriels
- **🔍 Triple Cascade AI** : Système d'analyse en trois niveaux pour une précision maximale
- **🌐 Multi-Plateformes** : Interface web Streamlit + CLI + packages clients Windows/Linux/macOS

---

## 🏭 Cas d'Usage

### 1. Vendor Data Books (VDB)

Les VDB regroupent toutes les données techniques d'un équipement industriel (caractéristiques, certifications, maintenance, etc.).

**Avant Docodile** :
- ⏱️ 5-10 jours de travail manuel
- 📄 Gestion de centaines de fichiers PDF
- ⚠️ Risques d'oublis ou erreurs

**Avec Docodile** :
- ⚡ 1-2 jours avec vérification humaine
- 🤖 Mapping automatique des documents
- ✅ Rapport de validation détaillé

[📖 Documentation VDB détaillée](docs/VDB.md)

### 2. Rapports USO (Utilisation en Service des Ouvrages)

Documentation requise pour le suivi et la maintenance d'équipements en service.

**Avant Docodile** :
- ⏱️ 3-7 jours de compilation manuelle
- 📑 Extraction manuelle depuis Purchase Orders (PO)
- ⚠️ Formats variés et non standardisés

**Avec Docodile** :
- ⚡ Quelques heures de traitement automatisé
- 🤖 Parsing intelligent des PO Excel/PDF
- ✅ Génération conforme aux standards

[📖 Documentation USO détaillée](docs/USO.md)

### 3. Documentation Technique Personnalisée

Génération de manuels techniques, procédures, audits qualité selon des templates spécifiques.

---

## 🏗️ Architecture

Docodile utilise une architecture modulaire avec intelligence artificielle intégrée :

```
┌─────────────────────────────────────────────┐
│         Interface Utilisateur               │
│  (Streamlit Web UI + CLI + Client Apps)     │
└─────────────────┬───────────────────────────┘
                  │
┌─────────────────▼───────────────────────────┐
│        Core Engine (Python)                 │
│                                             │
│  ┌─────────────────────────────────────┐   │
│  │  SmartDirectoryMapper (AI)          │   │
│  │  → Détection structure documents    │   │
│  └─────────────────────────────────────┘   │
│                                             │
│  ┌─────────────────────────────────────┐   │
│  │  FileMatchingEngine (AI)            │   │
│  │  → Correspondance Excel ↔ Fichiers  │   │
│  └─────────────────────────────────────┘   │
│                                             │
│  ┌─────────────────────────────────────┐   │
│  │  VDBGenerator / USOGenerator        │   │
│  │  → Compilation finale               │   │
│  └─────────────────────────────────────┘   │
└─────────────────────────────────────────────┘
```

**Technologies** :
- **IA/ML** : sentence-transformers, scikit-learn, PyTorch (CPU)
- **Backend** : Python 3.9+, Flask
- **Frontend** : React + TypeScript, Streamlit
- **Distribution** : Packages obfusqués avec système de licences JWT

[📖 Architecture détaillée](docs/ARCHITECTURE.md)

---

## 🚀 Démo en Ligne

Testez Docodile sans installation :

👉 **[https://docodile.fr/demo](https://docodile.fr/demo)**

**Modes de démo disponibles** :
- 🔓 **Démo en ligne** : Accès immédiat sans licence
- 🔑 **Installation complète** : Avec clé de licence (contactez-nous)

---

## 📊 Résultats

### Performances Validées

| Métrique | Valeur |
|----------|--------|
| **Précision AI** | 90% (matching fichiers) |
| **Gain de temps** | 70-80% vs. manuel |
| **Formats supportés** | Excel, PDF, Word, CSV |
| **Taux de satisfaction** | 95% (pilotes clients) |

### Industries Servies

- ⚛️ **Nucléaire** : Compilation VDB équipements critiques
- ✈️ **Aérospatial** : Documentation technique aéronautique
- 🏭 **Manufacturing** : Rapports USO et maintenance
- 🔬 **Pharmaceutique** : Documentation qualité et compliance

---

## 📚 Documentation

- [📖 VDB (Vendor Data Books)](docs/VDB.md) - Guide complet sur les VDB
- [📖 USO (Utilisation en Service des Ouvrages)](docs/USO.md) - Rapports USO en détail
- [🏗️ Architecture Technique](docs/ARCHITECTURE.md) - Comment fonctionne Docodile
- [❓ FAQ](docs/FAQ.md) - Questions fréquentes

---

## 🤝 Contact & Support

**Site web** : [https://docodile.fr](https://docodile.fr)

**Email** : contact@docodile.fr

**Demande d'accès démo** : [https://docodile.fr/demo](https://docodile.fr/demo)

---

## 📜 Licence

Ce dépôt contient la **documentation publique** de Docodile.

Le logiciel Docodile lui-même est propriétaire. Contactez-nous pour obtenir une licence.

Documentation © 2025 Docodile. Tous droits réservés.

---

## 🌟 Pourquoi Docodile ?

> "Docodile a transformé notre processus de compilation documentaire. Ce qui prenait 10 jours se fait maintenant en 2 jours avec une précision inégalée."
>
> — *Responsable Documentation, Industrie Nucléaire*

**Rejoignez les entreprises qui font confiance à Docodile pour leur documentation critique.**

[🚀 Demander une démo](https://docodile.fr/demo)

# Architecture Technique Docodile

## 🏗️ Vue d'Ensemble

Docodile est une plateforme de compilation documentaire basée sur l'intelligence artificielle, conçue avec une architecture modulaire et scalable.

```
┌──────────────────────────────────────────────────────────────┐
│                     INTERFACES UTILISATEUR                   │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐   │
│  │  Streamlit   │  │     CLI      │  │  Client Apps     │   │
│  │   Web UI     │  │  (Terminal)  │  │ (Win/Linux/Mac)  │   │
│  └──────┬───────┘  └──────┬───────┘  └────────┬─────────┘   │
└─────────┼──────────────────┼───────────────────┼─────────────┘
          │                  │                   │
┌─────────▼──────────────────▼───────────────────▼─────────────┐
│                      CORE ENGINE (Python)                     │
│                                                               │
│  ┌────────────────────────────────────────────────────────┐  │
│  │  AI Document Analyzer                                  │  │
│  │  → Détection automatique de structure documentaire     │  │
│  │  → Analyse sémantique intelligente                     │  │
│  └────────────────────────────────────────────────────────┘  │
│                                                               │
│  ┌────────────────────────────────────────────────────────┐  │
│  │  Matching Engine                                       │  │
│  │  → Correspondance automatique fichiers ↔ sections      │  │
│  │  → Précision 90%                                       │  │
│  └────────────────────────────────────────────────────────┘  │
│                                                               │
│  ┌────────────────────────────────────────────────────────┐  │
│  │  Document Generator                                    │  │
│  │  → Compilation documentaire multi-modes                │  │
│  │  → Rapports de validation                              │  │
│  └────────────────────────────────────────────────────────┘  │
└───────────────────────────────────────────────────────────────┘
                            │
┌───────────────────────────▼───────────────────────────────────┐
│                     COUCHE IA / ML                            │
│                                                               │
│  Machine Learning & NLP pour analyse documentaire            │
│  Embeddings sémantiques + Analyse structurelle               │
│  Précision 90% sur matching documentaire                     │
└───────────────────────────────────────────────────────────────┘
```

---

## 🎯 Principes d'Architecture

### 1. Modularité

Docodile est construit en modules indépendants :
- **Core** : Moteur de génération documentaire
- **AI** : Intelligence artificielle et analyse sémantique
- **Interfaces** : CLI, Web UI, APIs
- **Utils** : Utilitaires de parsing et manipulation de fichiers

Chaque module peut être mis à jour indépendamment.

### 2. Intelligence Artificielle

L'IA de Docodile combine :
- **Analyse sémantique** : Compréhension du sens des documents
- **Analyse structurelle** : Détection de patterns et métadonnées
- **Validation croisée** : Vérification multi-niveaux pour garantir la précision

Cette approche hybride permet d'atteindre **90% de précision** sur le matching documentaire.

### 3. Scalabilité

Architecture conçue pour gérer :
- **Petits projets** : 10-20 sections, 50-100 fichiers (< 1 min)
- **Projets moyens** : 30-50 sections, 200-500 fichiers (< 10 min)
- **Grands projets** : 100+ sections, 1000+ fichiers (< 30 min)

---

## 🔐 Sécurité et Distribution

### Système de Licences

Docodile utilise un système de licences JWT pour :
- Authentification des clients
- Validation machine (machine fingerprinting)
- Distribution sécurisée des modules

### Protection du Code

Le code distribué aux clients est protégé par :
- Obfuscation Python
- Licences liées à la machine
- Vérification périodique de validité

---

## 🎨 Workflow Général

### Génération de Documents (Vue Simplifiée)

```
1. IMPORT
   → Template Excel (structure attendue)
   → Fichiers sources (PDF, Word, Excel)

2. ANALYSE IA
   → Scan automatique des fichiers
   → Détection de structure
   → Matching intelligent

3. VALIDATION
   → Rapport de correspondances trouvées
   → Détection fichiers manquants
   → Niveau de confiance par match

4. GÉNÉRATION
   → Compilation document final
   → Export multi-formats (PDF, JSON, TXT)
```

---

## 📊 Technologies Utilisées

### Backend
- **Python 3.9+** - Langage principal
- **Flask** - Serveur web (license server)
- **SQLite** - Base de données

### IA / ML
- **Machine Learning** - Analyse sémantique de documents
- **NLP** - Traitement du langage naturel
- **Embeddings** - Vectorisation de contenu textuel

### Frontend
- **Streamlit** - Interface web interactive
- **React + TypeScript** - Landing page

### Formats Supportés
- **Entrées** : Excel, PDF, Word, CSV, Images (OCR)
- **Sorties** : PDF, JSON, TXT, structures de fichiers

---

## 🚀 Performances

### Temps de Traitement Typiques

| Taille Projet | Fichiers | Temps Traitement |
|--------------|----------|------------------|
| Petit | 50-100 | ~1 minute |
| Moyen | 200-500 | ~6 minutes |
| Grand | 1000+ | ~30 minutes |

### Précision

- **Matching automatique** : 90%
- **Détection fichiers manquants** : 100%
- **Extraction données Excel** : 99%

---

## 🔧 Modes de Déploiement

### 1. Installation Locale (Client)

- Téléchargement package client
- Validation licence
- Installation automatique dépendances
- Fonctionnement hors-ligne possible

### 2. Interface Web (Streamlit)

- Accès navigateur localhost
- Interface graphique intuitive
- Pas de configuration requise

### 3. CLI (Terminal)

- Commandes en ligne
- Intégration scripts
- Automatisation possible

---

## 📈 Évolutions Futures

### En Développement
- API REST pour intégration externe
- Dashboard Analytics (métriques temps réel)
- Système de Versioning (tracking révisions)

### Roadmap
- Déploiement Cloud (AWS/Azure)
- Scalabilité Horizontale
- Intégrations SharePoint, SAP

---

## ❓ Questions Fréquentes Techniques

### Pourquoi Python ?

- Écosystème ML/IA riche
- Parsing de documents efficace
- Multi-plateforme (Windows, Linux, macOS)
- Communauté active

### Docodile nécessite-t-il un GPU ?

Non. Docodile est optimisé CPU uniquement pour fonctionner sur ordinateurs standards sans carte graphique dédiée.

### Peut-on personnaliser le moteur ?

Oui, selon votre licence. Les clients entreprise peuvent demander des personnalisations :
- Templates spécifiques
- Règles métier personnalisées
- Intégrations sur-mesure

Contact : contact@docodile.fr

---

## 📞 Support Technique

Pour toute question technique :

📧 **Email** : contact@docodile.fr
🌐 **Site** : [https://docodile.fr](https://docodile.fr)
🚀 **Démo** : [https://docodile.fr/demo](https://docodile.fr/demo)

---

[⬅️ Retour à la documentation](../README.md)

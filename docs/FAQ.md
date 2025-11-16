# FAQ - Questions Fréquentes

## 📚 Général

### Qu'est-ce que Docodile ?

Docodile est une plateforme d'intelligence artificielle qui automatise la génération de documents techniques complexes tels que les Vendor Data Books (VDB), les rapports USO, et autres documentations industrielles critiques.

### Pourquoi "Docodile" ?

**Doco**dile = **Doco**mentation + crocodile

Le crocodile symbolise :
- 🐊 **Puissance** : Capacité à traiter des volumes massifs de documents
- 🐊 **Précision** : Mâchoire puissante = précision dans le matching
- 🐊 **Fiabilité** : Animal ancien et robuste = solution éprouvée

### Quelle est la précision de Docodile ?

- **Matching fichiers ↔ sections** : 90% de précision
- **Extraction données Excel** : 99% de précision
- **Détection fichiers manquants** : 100% (exhaustif)

Les 10% nécessitant validation manuelle sont clairement identifiés dans les rapports avec leur niveau de confiance.

---

## 🎯 Fonctionnalités

### Quels types de documents Docodile peut-il générer ?

Docodile supporte plusieurs modes de compilation :

1. **VDB (Vendor Data Books)** - Production-ready
   - Documentation technique complète d'équipements
   - Certifications, manuels, rapports de tests
   - Industries : nucléaire, aérospatial, pétrole & gaz

2. **USO (Utilisation en Service des Ouvrages)** - Production-ready
   - Rapports réglementaires nucléaires français
   - Parsing Purchase Orders Excel/PDF
   - Matching équipements ↔ documents

3. **Documentation Personnalisée** - En développement
   - Manuels techniques
   - Procédures qualité
   - Rapports d'audit

### Quels formats de fichiers sont supportés ?

**Entrées** :
- ✅ **Excel** : .xlsx, .xls (templates VDB, Purchase Orders)
- ✅ **PDF** : avec ou sans OCR
- ✅ **Word** : .docx, .doc
- ✅ **Images** : .png, .jpg, .jpeg (avec OCR)

**Sorties** :
- 📄 **PDF** : Rapports finaux compilés
- 📊 **JSON** : Données structurées machine-readable
- 📝 **TXT** : Rapports human-readable
- 📁 **Structure de fichiers** : Dossiers organisés par section

### Docodile peut-il gérer des documents en plusieurs langues ?

Actuellement, Docodile est optimisé pour :
- 🇫🇷 **Français** (priorité, secteur nucléaire)
- 🇬🇧 **Anglais** (industrie internationale)

Les modèles IA utilisés supportent naturellement 50+ langues, mais la précision peut varier.

---

## 🏭 Cas d'Usage

### Docodile convient-il à mon industrie ?

Docodile est particulièrement adapté aux industries avec des exigences documentaires strictes :

- ⚛️ **Nucléaire** : Conformité ASN, VDB, USO
- ✈️ **Aérospatial** : Documentation FAA/EASA, certifications
- 🏭 **Manufacturing** : Rapports qualité, maintenance
- 🔬 **Pharmaceutique** : Documentation FDA, GMP
- 🏗️ **BTP** : Dossiers techniques ouvrages (DTO)
- ⚙️ **Oil & Gas** : Documentation API, ATEX

Si votre activité nécessite de compiler des centaines de documents techniques selon un template standardisé, Docodile peut vous aider.

### Combien de temps faut-il pour compiler un VDB avec Docodile ?

**Sans Docodile** : 7-11 jours
**Avec Docodile** : 1.5-2 jours (validation incluse)

**Gain de temps** : ~80%

### Peut-on utiliser Docodile sur des projets confidentiels ?

**Oui, absolument.**

- 🔒 **Installation locale** : Docodile s'installe sur vos machines, pas de cloud
- 🔒 **Pas d'envoi de données** : Vos documents restent sur votre infrastructure
- 🔒 **Validation de licence** : Seule la clé de licence est validée en ligne (HTTPS)

Docodile ne transmet **aucun contenu** de vos documents vers des serveurs externes.

---

## 💻 Installation & Utilisation

### Quels sont les prérequis système ?

**Minimum** :
- OS : Windows 10+, Linux (Ubuntu 20.04+), macOS 11+
- CPU : 2 cœurs
- RAM : 4 GB
- Stockage : 2 GB (installation + modèles IA)
- Python : 3.9, 3.10, 3.11, 3.12

**Recommandé** :
- CPU : 4+ cœurs
- RAM : 8 GB
- SSD pour meilleures performances

**Non supporté** :
- ❌ Python 3.13+ (incompatibilité numpy/torch)
- ❌ Python < 3.9 (trop ancien)

### Ai-je besoin d'une connexion Internet ?

**Pendant l'installation** : Oui
- Téléchargement des modules Docodile (~1 MB)
- Installation dépendances Python (~500 MB)
- Téléchargement modèle IA (~90 MB)

**Pendant l'utilisation** : Non (optionnel)
- Validation licence (requête HTTPS unique)
- Mode démo en ligne (optionnel)
- Fonctionnement hors-ligne possible après installation

### Comment obtenir une licence ?

1. **Demande d'accès** : [https://docodile.fr/demo](https://docodile.fr/demo)
2. **Formulaire** : Remplir les informations (nom, email, entreprise, cas d'usage)
3. **Réception** : Licence par email sous 24-48h
4. **Activation** : Saisir la clé dans le client Docodile

**Format de licence** : `DCD-XXX-2025-XXXXXXXX`

**Types de licence** :
- 🔓 **Démo** : Accès limité en ligne
- 🔑 **Pilote** : Installation complète pour tests (durée limitée)
- 💼 **Souscription** : Licence commerciale complète

### Puis-je tester Docodile sans installation ?

**Oui !** Deux options :

1. **Démo en ligne** : [https://docodile.fr/demo](https://docodile.fr/demo)
   - Accès immédiat sans licence
   - Fonctionnalités limitées
   - Idéal pour découvrir l'interface

2. **Licence pilote** : Installation complète pour tests
   - Contactez-nous : contact@docodile.fr
   - Accès complet pendant la période pilote
   - Support inclus

---

## 🔧 Technique

### Quelle IA utilise Docodile ?

Docodile utilise des **modèles d'IA avancés** spécialisés dans l'analyse documentaire :

- **Type** : Modèles de langage et analyse sémantique
- **Taille** : Optimisé pour fonctionner sur CPU standard
- **Précision** : 90% sur matching documentaire
- **Performance** : Pas besoin de GPU
- **Déploiement** : Fonctionne entièrement hors-ligne

Les modèles sont optimisés pour le traitement de documents techniques industriels.

### Docodile nécessite-t-il un GPU ?

**Non.** Docodile est optimisé pour CPU uniquement.

- ✅ Fonctionne sur ordinateurs portables standards
- ✅ Pas de GPU requis (coût réduit)
- ✅ Frameworks ML optimisés CPU (installation légère)

### Comment Docodile protège-t-il mon code ?

Docodile utilise **plusieurs techniques de protection avancées** pour sécuriser le code distribué :

- 🔒 **Obfuscation multi-niveaux** : Code protégé contre le reverse-engineering
- 🔒 **Licence liée machine** : Un client = une machine autorisée
- 🔒 **Authentification sécurisée** : Tokens JWT avec validation serveur

Le code source complet reste **propriétaire et privé**.

### Puis-je intégrer Docodile dans mon système existant ?

**En développement.**

Roadmap 2025 :
- 🔄 **API REST** pour appels externes
- 🔗 **Webhooks** pour notifications
- 📊 **Export GMAO** (SAP, Maximo)
- 🌐 **Intégrations** SharePoint, Documentum

Contactez-nous pour discuter de vos besoins spécifiques : contact@docodile.fr

---

## 📊 Pricing & Licences

### Quel est le coût de Docodile ?

**Nous contacter** : [contact@docodile.fr](mailto:contact@docodile.fr)

Le pricing dépend de :
- Nombre d'utilisateurs
- Volume de projets/an
- Support requis (standard, premium)
- Intégrations spécifiques

**Démo gratuite** disponible pour évaluation.

### Existe-t-il une version gratuite ?

**Démo en ligne gratuite** : Oui
- Accès à l'interface Streamlit
- Fonctionnalités limitées
- Données de démonstration uniquement

**Version complète gratuite** : Non
- Logiciel professionnel avec licence commerciale
- Support et mises à jour inclus dans la souscription

### Quelle est la différence entre les types de licences ?

| Type | Usage | Durée | Support |
|------|-------|-------|---------|
| **Démo** | Découverte en ligne | Illimité | - |
| **Pilote** | Tests installation complète | 1-3 mois | Email |
| **Souscription** | Production | 1 an (renouvelable) | Premium |

---

## 🚀 Support & Évolutions

### Comment obtenir du support ?

**Email** : contact@docodile.fr
- Réponse sous 24-48h (jours ouvrés)

**Documentation** : [Ce repository GitHub](https://github.com/votre-username/docodile-public)
- Guides d'utilisation
- FAQ
- Exemples

**Support premium** (clients sous souscription) :
- Réponse prioritaire < 4h
- Support téléphonique
- Formations personnalisées

### Docodile est-il open-source ?

**Non.** Docodile est un logiciel **propriétaire**.

**Ce qui est public** :
- ✅ Documentation (ce repository)
- ✅ Exemples d'utilisation
- ✅ Spécifications techniques

**Ce qui est privé** :
- ❌ Code source complet
- ❌ Modèles IA fine-tunés
- ❌ Algorithmes propriétaires

### À quelle fréquence Docodile est-il mis à jour ?

**Mises à jour régulières** :
- 🔄 **Mineures** (bug fixes) : Mensuel
- 🚀 **Majeures** (nouvelles features) : Trimestriel
- 🔐 **Sécurité** : Immédiat si critique

Les clients sous souscription reçoivent automatiquement les mises à jour.

### Comment suggérer une fonctionnalité ?

**Email** : contact@docodile.fr

Nous sommes à l'écoute de nos utilisateurs ! Décrivez :
- 📝 **Use case** : Quel problème vous essayez de résoudre
- 🎯 **Fonctionnalité** : Ce que vous aimeriez voir
- 📊 **Impact** : Combien de temps/coût cela vous ferait économiser

---

## 🌍 Réglementaire & Compliance

### Docodile est-il conforme RGPD ?

**Oui.**

- ✅ **Données personnelles** : Uniquement nom, email, entreprise (formulaire démo)
- ✅ **Stockage** : Serveurs en Europe (OVH France)
- ✅ **Pas de tracking** : Pas de cookies publicitaires
- ✅ **Droit à l'oubli** : Suppression sur demande

Docodile ne traite **aucun contenu** de vos documents techniques (tout reste local).

### Docodile peut-il être utilisé pour la conformité ASN ?

**Oui.** Docodile aide à la préparation de documents conformes ASN (rapports USO notamment).

**Important** :
- ✅ Docodile **facilite** la compilation
- ⚠️ **Validation humaine requise** : L'ingénieur doit vérifier les rapports
- ⚠️ **Responsabilité** : L'exploitant reste responsable de la conformité finale

Docodile est un **outil d'assistance**, pas un substitut à l'expertise humaine.

---

## ❓ Autres Questions

### Puis-je utiliser Docodile pour des projets personnels ?

Docodile est conçu pour un **usage professionnel/industriel**.

Pour des projets personnels ou académiques, contactez-nous : contact@docodile.fr

### Docodile fonctionne-t-il sur Mac avec Apple Silicon (M1/M2/M3) ?

**Oui**, avec quelques précautions :

- ✅ Python 3.9-3.12 (ARM64 natif)
- ✅ Frameworks ML compatibles ARM64
- ⚠️ Performances légèrement inférieures vs. x86_64

Recommandé : Python depuis Homebrew (`brew install python@3.12`)

### Les données sont-elles chiffrées ?

**En transit** : Oui
- HTTPS (TLS 1.3) pour validation licence
- Certificat Let's Encrypt

**Au repos** : Responsabilité utilisateur
- Docodile stocke tout localement sur vos machines
- Utilisez le chiffrement disque de votre OS (BitLocker, FileVault, LUKS)

### Existe-t-il des vidéos de démonstration ?

Actuellement non, mais prévu pour 2025 :
- 🎥 Vidéo démo VDB (5 min)
- 🎥 Vidéo démo USO (5 min)
- 🎥 Tutoriel installation (10 min)

En attendant : [Démo en ligne](https://docodile.fr/demo)

---

## 📞 Contact

**Vous ne trouvez pas votre réponse ?**

📧 **Email** : contact@docodile.fr
🌐 **Site** : [https://docodile.fr](https://docodile.fr)
🚀 **Démo** : [https://docodile.fr/demo](https://docodile.fr/demo)

Nous répondons sous 24-48h (jours ouvrés).

---

[⬅️ Retour à la documentation](../README.md)

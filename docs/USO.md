# Rapports USO (Utilisation en Service des Ouvrages)

## 📖 Qu'est-ce qu'un Rapport USO ?

Un **rapport USO (Utilisation en Service des Ouvrages)** est un document de suivi réglementaire obligatoire dans l'industrie nucléaire française. Il documente l'historique complet d'un équipement depuis sa fabrication jusqu'à sa mise en service et son exploitation.

### Acronyme USO

**USO** = **U**tilisation en **S**ervice des **O**uvrages

Ce terme est spécifique au secteur nucléaire français, défini par l'ASN (Autorité de Sûreté Nucléaire).

---

## 🏭 Contexte Réglementaire

### Exigences ASN

L'ASN impose la constitution de rapports USO pour :
- ⚛️ **Équipements importants pour la sûreté (EPS)**
- ⚛️ **Équipements sous pression nucléaires (ESPN)**
- ⚛️ **Composants critiques** des installations nucléaires

**Objectif** : Traçabilité complète pour garantir la sûreté nucléaire.

### Contenu Réglementaire d'un USO

Un rapport USO complet contient :

1. **📋 Identification de l'Équipement**
   - Désignation, numéro de série, repère
   - Localisation dans l'installation
   - Classification sûreté

2. **📜 Historique de Conception**
   - Plans et dessins d'ensemble
   - Notes de calcul de dimensionnement
   - Spécifications techniques

3. **🏭 Historique de Fabrication**
   - Certificats matières (EN 10204 3.1/3.2)
   - Procès-verbaux de fabrication
   - Rapports de contrôles non destructifs (CND)

4. **🔬 Contrôles et Essais**
   - Épreuves hydrauliques
   - Contrôles dimensionnels
   - Examens de surface (ressuage, magnétoscopie)

5. **✅ Réception et Mise en Service**
   - Procès-verbal de réception (PV)
   - Rapports d'installation
   - Résultats des essais de mise en service

6. **🛠️ Historique d'Exploitation**
   - Interventions de maintenance
   - Modifications apportées
   - Incidents survenus

---

## 🎯 Problématique de Compilation USO

### Volume et Complexité

Un projet nucléaire typique génère :
- **50-200 équipements** nécessitant un USO
- **100-500 pages** par USO
- **Des milliers de documents sources** à compiler

**Exemple** : Un réacteur nucléaire = **10 000+ pages** d'USO au total

### Sources de Données Éclatées

Les informations proviennent de multiples sources :

#### 1. Purchase Orders (PO) - Bons de Commande

**Format** : Excel ou PDF
**Contenu** :
- Liste des équipements commandés
- Références fabricant
- Quantités, prix, délais
- Spécifications techniques de base

**Problème** : Les PO peuvent contenir des dizaines d'équipements différents dans un seul fichier Excel, nécessitant un parsing intelligent.

#### 2. Documentation Fabricant

**Format** : PDF, Word, fichiers CAO
**Contenu** :
- Certificats matières
- Rapports de tests
- Plans techniques
- Manuels d'exploitation

**Problème** : Nommage incohérent, structure de répertoires variable selon les fabricants.

#### 3. Documents Projet

**Format** : Excel, Word, PDF
**Contenu** :
- Plans d'implantation
- Spécifications projet
- Procédures de réception
- Rapports de mise en service

**Problème** : Documents évolutifs avec multiples révisions.

### Exemple de Complexité

**Entrée** : Purchase Order Excel contenant 25 équipements

| Ligne | Repère | Désignation | Fabricant | Quantité | N° Série | ... |
|-------|--------|-------------|-----------|----------|----------|-----|
| 1 | V-001 | Vanne papillon DN100 | ACME Valves | 1 | SN-12345 | ... |
| 2 | V-002 | Vanne papillon DN100 | ACME Valves | 1 | SN-12346 | ... |
| ... | ... | ... | ... | ... | ... | ... |
| 25 | P-010 | Pompe centrifuge | Flowtech | 1 | SN-98765 | ... |

**Attendu** : 25 rapports USO individuels, un par équipement, avec tous les documents associés.

**Défi** : Comment extraire automatiquement les données de chaque ligne et associer les bons documents sources ?

---

## 🤖 Solution Docodile pour les USO

### 1. Parsing Intelligent des Purchase Orders

Docodile analyse automatiquement les PO Excel/PDF :

**Technologie** :
- **Detection de Structure** : Identification automatique des colonnes (repère, désignation, fabricant, etc.)
- **Extraction Multi-Lignes** : Création d'une fiche par équipement
- **Normalisation** : Standardisation des formats de données

**Entrée** : `Purchase_Order_2025.xlsx`

**Sortie** : Données structurées contenant :
- Identifiants équipements (repère, numéro de série)
- Caractéristiques techniques extraites
- Informations fabricant
- Métadonnées complémentaires

Format : JSON pour traitement automatique

### 2. Matching Documents ↔ Équipements

Pour chaque équipement extrait du PO, Docodile cherche automatiquement les documents associés :

**Analyse IA Multi-Critères** :
- 🔍 Analyse des identifiants uniques (numéros de série, repères)
- 🔍 Analyse sémantique des désignations et types d'équipements
- 🔍 Correspondance fabricants et références
- 🔍 Validation croisée avec métadonnées

Le système calcule un score de confiance pour chaque correspondance trouvée et signale les matches incertains pour validation manuelle.

### 3. Génération Rapports USO Individuels

Pour chaque équipement, Docodile génère :

**📄 Fichier USO standardisé** :
```
USO_V-001_Vanne_Papillon_DN100/
├── 01_Identification.md
├── 02_Specifications_Techniques.md
├── 03_Documents_Fabricant/
│   ├── Certificate_Material_SN-12345.pdf
│   ├── Test_Report_V001_ACME.pdf
│   └── Drawing_Butterfly_Valve_DN100.pdf
├── 04_Reception_Mise_en_Service.md
└── USO_V-001_RAPPORT_COMPLET.pdf
```

**📊 Métadonnées structurées** :
```json
{
  "repere": "V-001",
  "designation": "Vanne papillon DN100",
  "numero_serie": "SN-12345",
  "fabricant": "ACME Valves",
  "documents_associes": [
    {
      "fichier": "Certificate_Material_SN-12345.pdf",
      "type": "Certificat matière",
      "confiance": 0.98
    }
  ],
  "statut_completude": "80%",
  "documents_manquants": [
    "Procès-verbal de réception",
    "Rapport de mise en service"
  ]
}
```

### 4. Validation et Traçabilité

**Rapport de Génération détaillé** :
```
==========================================
RAPPORT GÉNÉRATION USO - 2025-11-16
==========================================

Purchase Order analysé : Purchase_Order_2025.xlsx
Nombre d'équipements détectés : 25

RÉSULTATS PAR ÉQUIPEMENT :
--------------------------

[1/25] V-001 - Vanne papillon DN100 (SN-12345)
  ✅ Données PO extraites : 12 champs
  ✅ Documents trouvés : 3 fichiers
  ⚠️  Documents manquants : 2 (PV réception, rapport MS)
  📊 Complétude : 75%

[2/25] V-002 - Vanne papillon DN100 (SN-12346)
  ✅ Données PO extraites : 12 champs
  ✅ Documents trouvés : 4 fichiers
  ✅ Complétude : 95%

...

STATISTIQUES GLOBALES :
-----------------------
✅ Équipements traités : 25/25 (100%)
✅ Documents matchés : 87 fichiers
⚠️  Documents manquants : 15 fichiers
📊 Complétude moyenne : 82%
⏱️  Temps de traitement : 12 minutes
```

---

## 📊 Résultats Concrets

### Gain de Temps

| Tâche | Manuel | Avec Docodile | Gain |
|-------|--------|---------------|------|
| **Parsing PO Excel** | 1-2 jours | 5-10 minutes | **-95%** |
| **Matching docs ↔ équipements** | 2-4 jours | 10-20 minutes | **-90%** |
| **Génération rapports individuels** | 3-5 jours | 30-60 minutes | **-95%** |
| **Vérification & validation** | 1-2 jours | 3-5 heures | **-75%** |
| **TOTAL (25 équipements)** | **7-13 jours** | **0.5-1 jour** | **~90%** |

### Précision

- **Extraction PO** : 99% de précision (structure Excel standardisée)
- **Matching Documents** : 85-90% de précision (nécessite validation)
- **Détection Fichiers Manquants** : 100% (liste exhaustive générée)

---

## 🎯 Workflow Docodile USO

```
┌──────────────────────────────────────────────────────┐
│ 1. PRÉPARATION                                       │
│    → Purchase Order Excel/PDF                        │
│    → Dossier avec documents fabricant                │
└────────────────┬─────────────────────────────────────┘
                 │
┌────────────────▼─────────────────────────────────────┐
│ 2. IMPORT DOCODILE MODE USO                          │
│    → python uso_cli.py generate /path/to/project     │
│    → ou Interface Streamlit (Mode USO)               │
└────────────────┬─────────────────────────────────────┘
                 │
┌────────────────▼─────────────────────────────────────┐
│ 3. PARSING PO                                        │
│    → Détection automatique structure PO              │
│    → Extraction des équipements (25 lignes)          │
│    → Génération données structurées                  │
└────────────────┬─────────────────────────────────────┘
                 │
┌────────────────▼─────────────────────────────────────┐
│ 4. MATCHING IA                                       │
│    → Analyse multi-critères pour chaque équipement   │
│    → Recherche intelligente documents associés       │
│    → Calcul scores de confiance                      │
│    → Génération inventaire de correspondances        │
└────────────────┬─────────────────────────────────────┘
                 │
┌────────────────▼─────────────────────────────────────┐
│ 5. GÉNÉRATION USO                                    │
│    → Création de 25 dossiers USO individuels         │
│    → Copie des documents associés                    │
│    → Génération rapports PDF                         │
└────────────────┬─────────────────────────────────────┘
                 │
┌────────────────▼─────────────────────────────────────┐
│ 6. VALIDATION HUMAINE                                │
│    → Revue du rapport de génération                  │
│    → Vérification des documents manquants            │
│    → Complétion manuelle si nécessaire (10-20%)      │
└──────────────────────────────────────────────────────┘
```

**Temps total** : 0.5-1 jour (vs. 7-13 jours en manuel)

---

## 💡 Cas d'Usage Réel

### Projet Nucléaire - Remplacement Tuyauterie

**Contexte** :
- 45 équipements (vannes, tuyaux, supports)
- 1 Purchase Order Excel (18 colonnes, 45 lignes)
- 280 documents PDF fabricant
- Exigence ASN : USO complet pour mise en service

**Avant Docodile** :
- ⏱️ 3 semaines (2 ingénieurs)
- ⚠️ 8 erreurs de matching détectées lors du contrôle ASN → retard
- 💰 Coût : 35 000€ (main d'œuvre)

**Avec Docodile** :
- ⏱️ 2 jours (1 ingénieur + validation)
- ✅ 0 erreur de matching (validation complète avant soumission ASN)
- ✅ 12 documents manquants identifiés immédiatement → demandés au fabricant
- 💰 Coût : 6 000€ → **Économie 83%**

**Retour client** :
> "Docodile a transformé notre processus USO. La détection automatique des documents manquants nous a évité un rejet ASN qui aurait coûté 2 mois de retard."

---

## 🔧 Format des Entrées

### Purchase Order Excel

**Structure attendue** :

| Colonne Recommandée | Description | Exemple |
|---------------------|-------------|---------|
| **Repère** | Identifiant unique | V-001 |
| **Désignation** | Description équipement | Vanne papillon DN100 |
| **Fabricant** | Nom du fournisseur | ACME Valves |
| **Numéro Série** | N° unique de fabrication | SN-12345 |
| **Quantité** | Nombre d'unités | 1 |
| **Matériau** | Matériau principal | Inox 316L |
| **Pression Service** | Pression nominale | 16 bar |
| **Température Service** | Température nominale | -10°C à +120°C |

**Notes** :
- ✅ Docodile s'adapte automatiquement à la structure du PO (noms de colonnes variables)
- ✅ Les colonnes manquantes sont détectées et signalées
- ✅ Format .xlsx ou .xls supporté

### Documents Fabricant

**Organisation recommandée** :
```
Documents_Fabricant/
├── Certificates/
│   ├── Certificate_Material_SN-12345.pdf
│   ├── Certificate_Material_SN-12346.pdf
│   └── ...
├── Test_Reports/
│   ├── Test_Report_V001.pdf
│   ├── Test_Report_V002.pdf
│   └── ...
├── Drawings/
│   └── ...
└── Manuals/
    └── ...
```

**Ou** : Un seul répertoire plat (Docodile scanne récursivement)

---

## 📈 Évolutions Futures

Fonctionnalités en développement :
- 🔄 **Import PO PDF** : OCR avancé pour PO scannés
- 🌐 **Multi-PO** : Gestion de plusieurs PO simultanés
- 🔗 **Export GMAO** : Interface avec systèmes de maintenance (SAP, Maximo)
- 📊 **Dashboard Complétude** : Suivi en temps réel par équipement
- ✅ **Validation ASN** : Checklist automatique de conformité réglementaire

---

## 📞 Support USO

Pour toute question sur l'utilisation de Docodile pour vos rapports USO :

📧 **Email** : contact@docodile.fr
🌐 **Site** : [https://docodile.fr](https://docodile.fr)
🚀 **Démo** : [https://docodile.fr/demo](https://docodile.fr/demo)

---

[⬅️ Retour à la documentation](../README.md)

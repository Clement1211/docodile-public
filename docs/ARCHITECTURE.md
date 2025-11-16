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
│  │  SmartDirectoryMapper                                  │  │
│  │  → IA de détection de structure documentaire           │  │
│  │  → Triple Cascade AI (3 niveaux d'analyse)            │  │
│  └────────────────────────────────────────────────────────┘  │
│                                                               │
│  ┌────────────────────────────────────────────────────────┐  │
│  │  FileMatchingEngine                                    │  │
│  │  → Matching Excel ↔ Fichiers (AI-powered)             │  │
│  │  → Embeddings sémantiques + Similarité cosinus        │  │
│  └────────────────────────────────────────────────────────┘  │
│                                                               │
│  ┌────────────────────────────────────────────────────────┐  │
│  │  VDBGenerator / USOGenerator / CustomGenerator        │  │
│  │  → Compilation documentaire multi-modes                │  │
│  │  → Génération rapports validation                      │  │
│  └────────────────────────────────────────────────────────┘  │
│                                                               │
│  ┌────────────────────────────────────────────────────────┐  │
│  │  DocodileLogger                                        │  │
│  │  → Logging enterprise-grade (JSON Lines)               │  │
│  │  → Traçabilité complète des opérations                 │  │
│  └────────────────────────────────────────────────────────┘  │
└───────────────────────────────────────────────────────────────┘
                            │
┌───────────────────────────▼───────────────────────────────────┐
│                     COUCHE IA / ML                            │
│                                                               │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐   │
│  │ Sentence     │  │  PyTorch     │  │  Scikit-Learn    │   │
│  │ Transformers │  │  (CPU only)  │  │  (Clustering)    │   │
│  └──────────────┘  └──────────────┘  └──────────────────┘   │
│                                                               │
│  Modèle : sentence-transformers/all-MiniLM-L6-v2             │
│  → Embeddings de 384 dimensions                              │
│  → Précision 90% sur matching documentaire                   │
└───────────────────────────────────────────────────────────────┘
```

---

## 🧠 Triple Cascade AI - Cœur du Système

Le **Triple Cascade AI** est le moteur d'analyse documentaire de Docodile. Il analyse les documents en trois niveaux de profondeur croissante.

### Niveau 1 : Analyse Structurelle (Métadonnées)

**Objectif** : Détection rapide basée sur les métadonnées et noms de fichiers

**Technologies** :
- Regex patterns pour extraction de numéros de série, repères
- Analyse des noms de fichiers (parsing intelligent)
- Détection de mots-clés dans les chemins

**Exemple** :
```python
# Fichier: "Certificate_Material_SN-12345_V001.pdf"
# Extraction:
{
  "numero_serie": "SN-12345",
  "repere": "V001",
  "type": "Certificate",
  "sous_type": "Material",
  "confiance_niveau1": 0.85
}
```

**Avantage** : Très rapide (< 1 seconde par fichier)

**Limite** : Dépend de la qualité du nommage des fichiers

### Niveau 2 : Analyse Sémantique (Embeddings)

**Objectif** : Compréhension du contenu textuel via IA

**Technologies** :
- **Modèle** : `sentence-transformers/all-MiniLM-L6-v2`
- **Extraction texte** : PyMuPDF (PDF), python-docx (Word), pandas (Excel)
- **Vectorisation** : Embeddings de 384 dimensions
- **Similarité** : Cosinus entre vecteurs

**Processus** :
```python
# 1. Extraction du texte du PDF
texte_pdf = extract_text_from_pdf("Certificate_Material.pdf")
# "This is to certify that material Stainless Steel 316L..."

# 2. Génération embedding (vecteur 384D)
embedding_pdf = model.encode(texte_pdf)
# [0.234, -0.123, 0.567, ..., 0.089]  # 384 valeurs

# 3. Comparaison avec section VDB attendue
section_vdb = "Material Certification for Stainless Steel"
embedding_vdb = model.encode(section_vdb)

# 4. Calcul similarité cosinus
similarite = cosine_similarity(embedding_pdf, embedding_vdb)
# 0.92 → Très probable match !
```

**Avantage** : Comprend le sens, pas seulement les mots-clés

**Limite** : Plus lent (5-10 secondes par fichier selon taille)

### Niveau 3 : Validation Croisée (Hybrid AI)

**Objectif** : Combinaison des résultats des niveaux 1 et 2 + heuristiques métier

**Technologies** :
- Algorithmes de fusion de scores
- Règles métier (seuils de confiance, contraintes logiques)
- Détection d'anomalies

**Processus** :
```python
# Score final hybride
score_final = (
    0.3 * confiance_niveau1 +  # Métadonnées
    0.6 * confiance_niveau2 +  # Sémantique
    0.1 * bonus_heuristiques   # Règles métier
)

# Exemple de règles métier:
if "certificate" in filename.lower() and "material" in texte_pdf:
    bonus_heuristiques += 0.1

if numero_serie_in_filename == numero_serie_in_vdb:
    bonus_heuristiques += 0.15
```

**Avantage** : Robustesse maximale, réduction des faux positifs

---

## 📦 Modules Principaux

### 1. Core Engine (`core/`)

**Responsabilités** :
- Orchestration du pipeline de génération
- Gestion des templates documentaires
- Coordination entre modules

**Fichiers clés** :
- `core/vdb_generator.py` - Moteur VDB (production-ready)
- `core/uso_generator.py` - Moteur USO (en développement)
- `core/logger.py` - Système de logging centralisé

### 2. AI Engine (`ai/`)

**Responsabilités** :
- Détection de structure documentaire
- Matching fichiers ↔ sections
- Embeddings sémantiques

**Fichiers clés** :
- `ai/smart_directory_mapper.py` - Analyse structure de répertoires
- `ai/file_matching_engine.py` - Matching AI
- `ai/embeddings_light.py` - Gestion des embeddings (CPU-optimized)

### 3. Hybrid Engine (`hybrid/`)

**Responsabilités** :
- Fusion des résultats AI + règles métier
- Optimisation des scores de confiance
- Gestion des cas limites

**Fichiers clés** :
- `hybrid/hybrid_matcher.py` - Matching hybride
- `hybrid/confidence_optimizer.py` - Optimisation scores

### 4. Interfaces (`interfaces/`)

**Responsabilités** :
- CLI (terminal)
- Streamlit (web UI)
- APIs pour clients externes

**Fichiers clés** :
- `interfaces/vdb_cli.py` - Interface ligne de commande VDB
- `interfaces/app_streamlit_real.py` - Interface web Streamlit
- `interfaces/docodile_platform.py` - Plateforme unifiée multi-modes

### 5. Utils (`utils/`)

**Responsabilités** :
- Parsing Excel/PDF/Word
- Gestion des fichiers
- Utilitaires divers

**Fichiers clés** :
- `utils/excel_parser.py` - Parsing intelligent de fichiers Excel
- `utils/pdf_extractor.py` - Extraction texte des PDF
- `utils/file_matcher.py` - Matching de base (non-AI)

---

## 🔐 Architecture de Distribution

Docodile utilise un système de distribution sécurisé avec licences et obfuscation.

### Serveur de Licences (VPS Production)

```
┌──────────────────────────────────────────────┐
│         VPS Production (84.54.23.65)         │
│                                              │
│  ┌────────────────────────────────────────┐ │
│  │  Flask License Server (Port 5000)      │ │
│  │  → Validation JWT tokens               │ │
│  │  → Gestion licences clients            │ │
│  │  → Machine fingerprinting              │ │
│  └────────────────────────────────────────┘ │
│                                              │
│  ┌────────────────────────────────────────┐ │
│  │  Nginx Reverse Proxy (Port 443)        │ │
│  │  → HTTPS termination (Let's Encrypt)   │ │
│  │  → Routing /api/, /auth/, /admin/      │ │
│  └────────────────────────────────────────┘ │
│                                              │
│  ┌────────────────────────────────────────┐ │
│  │  SQLite Database                       │ │
│  │  → Licenses                            │ │
│  │  → Authorized machines                 │ │
│  │  → Demo requests                       │ │
│  └────────────────────────────────────────┘ │
│                                              │
│  ┌────────────────────────────────────────┐ │
│  │  Modules Repository (/var/docodile/)   │ │
│  │  → Packages obfusqués (.tar.gz)        │ │
│  │  → Scripts de build                    │ │
│  └────────────────────────────────────────┘ │
└──────────────────────────────────────────────┘
```

### Client Installation

**Workflow d'installation client** :

```
1. Admin télécharge : client_minimal_windows.tar.gz
   ↓
2. Client extrait : docodile/docodile_client.py
   ↓
3. Client exécute : python docodile_client.py
   ↓
4. Saisie licence : DCD-SUB-2025-XXXXXXXX
   ↓
5. Validation JWT : POST /auth/token
   ↓
6. Téléchargement modules : GET /api/v1/releases/bundle
   → ai.tar.gz (180 KB)
   → core.tar.gz (220 KB)
   → interfaces.tar.gz (150 KB)
   → streamlit.tar.gz (50 KB)
   → uso.tar.gz (30 KB)
   → utils.tar.gz (120 KB)
   → vdb.tar.gz (200 KB)
   → hybrid.tar.gz (100 KB)
   ↓
7. Extraction automatique : ai/, core/, interfaces/, etc.
   ↓
8. Installation dépendances : pip install -r requirements.txt
   ↓
9. Lancement Streamlit : streamlit run interfaces/app_streamlit_real.py
```

**Total téléchargé** : ~1 MB (packages obfusqués)

### Obfuscation

Docodile utilise l'obfuscation Python pour protéger le code source distribué aux clients.

**Outils** :
- PyArmor (obfuscation AST)
- Niveau "light" pour compatibilité f-strings Python 3.9+

**Pipeline** :
```bash
# Scripts VPS
./scripts/vps_obfuscation_pipeline.sh staging light

# Génère:
/var/docodile/production/staging_light_fixed/
├── docodile-ai-linux-v1.0.0-obfuscated.tar.gz
├── docodile-core-linux-v1.0.0-obfuscated.tar.gz
├── docodile-interfaces-linux-v1.0.0-obfuscated.tar.gz
└── ...
```

**Licence types** :
- **Clean** (`DCD-TEST-2025-CLEAN01`) : Code non obfusqué pour tests
- **Obfuscated** (`DCD-SUB-2025-XXXXXXXX`) : Code obfusqué pour production

---

## 🎯 Pipeline de Génération VDB

Workflow détaillé d'une génération VDB :

```python
# 1. Initialisation
logger = DocodileLogger("vdb_generation")
vdb_gen = VDBGenerator(project_path="/path/to/project")

# 2. Lecture template Excel
template = ExcelParser.parse(project_path + "/template.xlsx")
# Résultat: {sections: [...], structure: {...}}

# 3. Scan fichiers sources
mapper = SmartDirectoryMapper(project_path + "/vendor_docs/")
inventory = mapper.scan_directory()
# Résultat: {files: [...], metadata: {...}}

# 4. Matching IA
matcher = FileMatchingEngine()
matches = []
for section in template.sections:
    best_match = matcher.find_best_match(
        section=section,
        inventory=inventory,
        threshold=0.7
    )
    matches.append({
        "section": section,
        "file": best_match,
        "confidence": best_match.score
    })

# 5. Validation
validator = ValidationEngine()
report = validator.validate(matches)
# Résultat: {
#   "matched": 85,
#   "missing": 5,
#   "orphans": 3,
#   "confidence_avg": 0.89
# }

# 6. Génération VDB final
if report.is_acceptable():
    vdb_gen.generate_vdb(matches)
    # Crée: output/VDB_Final.pdf, output/validation_report.json
```

---

## 📊 Formats de Sortie

### JSON Lines (JSONL) - Logs

Tous les logs sont en format JSON Lines pour faciliter l'analyse.

**Exemple** : `logs/vdb_generator.jsonl`
```jsonl
{"timestamp":"2025-11-16T10:30:15","level":"INFO","module":"vdb_generator","message":"Début génération VDB","project_path":"/path/to/project"}
{"timestamp":"2025-11-16T10:30:16","level":"INFO","module":"excel_parser","message":"Template Excel lu","sections":35,"rows":42}
{"timestamp":"2025-11-16T10:30:45","level":"INFO","module":"smart_directory_mapper","message":"Scan répertoire terminé","files_found":127,"duration_sec":29}
{"timestamp":"2025-11-16T10:32:10","level":"WARNING","module":"file_matching_engine","message":"Confiance faible","section":"3.2.1","confidence":0.65}
{"timestamp":"2025-11-16T10:33:00","level":"INFO","module":"vdb_generator","message":"VDB généré avec succès","duration_min":2.75,"matched":32,"missing":3}
```

### JSON - Rapports Structurés

**Exemple** : `output/validation_report.json`
```json
{
  "project_name": "Projet_Pompes_2025",
  "generation_date": "2025-11-16T10:33:00",
  "statistics": {
    "total_sections": 35,
    "matched": 32,
    "missing": 3,
    "confidence_avg": 0.87,
    "confidence_min": 0.65,
    "confidence_max": 0.99
  },
  "matched_files": [
    {
      "section": "3.2.1",
      "titre": "Operating Manual",
      "file": "Manual_V3_Final.pdf",
      "confidence": 0.95,
      "method": "semantic_embedding"
    },
    ...
  ],
  "missing_sections": [
    {
      "section": "7.2.3",
      "titre": "Design Drawings",
      "required": true
    },
    ...
  ]
}
```

### TXT - Rapports Humains

**Exemple** : `output/validation_report.txt`
```
==========================================
RAPPORT DE VALIDATION VDB
==========================================
Projet : Projet_Pompes_2025
Date : 2025-11-16 10:33:00

STATISTIQUES GLOBALES
---------------------
✅ Sections matchées : 32/35 (91%)
⚠️  Sections manquantes : 3/35 (9%)
📊 Confiance moyenne : 87%

DÉTAIL DES MATCHS
-----------------
✅ [3.2.1] Operating Manual
   Fichier : Manual_V3_Final.pdf
   Confiance : 95%

✅ [5.1.4] Material Certifications
   Fichier : Certificate_Material_A.pdf
   Confiance : 92%

⚠️  [7.2.3] Design Drawings
   Statut : NON TROUVÉ (obligatoire)

...
```

---

## 🔬 Technologies Utilisées

### Backend
- **Python 3.9+** - Langage principal
- **Flask** - Serveur web (license server)
- **SQLite** - Base de données (licences, logs)
- **PyMuPDF** - Extraction texte PDF
- **pandas** - Manipulation données Excel
- **python-docx** - Parsing Word

### IA / ML
- **sentence-transformers** - Embeddings sémantiques
- **PyTorch (CPU)** - Framework ML (optimisé CPU pour clients)
- **scikit-learn** - Clustering, classification
- **numpy** - Calculs matriciels

### Frontend
- **Streamlit** - Interface web interactive
- **React + TypeScript** - Landing page (docodile.fr)
- **Tailwind CSS** - Styling

### DevOps
- **Nginx** - Reverse proxy, HTTPS termination
- **Let's Encrypt** - Certificats SSL gratuits
- **Git** - Versioning
- **PyArmor** - Obfuscation code

---

## 📈 Performance

### Temps de Traitement

| Tâche | Petit Projet | Moyen Projet | Grand Projet |
|-------|--------------|--------------|--------------|
| **Scan répertoire** | 5 sec | 30 sec | 2 min |
| **Parsing Excel** | 1 sec | 5 sec | 15 sec |
| **Matching IA** | 30 sec | 5 min | 20 min |
| **Génération rapport** | 10 sec | 1 min | 5 min |
| **TOTAL** | ~1 min | ~6 min | ~30 min |

**Définitions** :
- Petit : 10-20 sections VDB, 50-100 fichiers sources
- Moyen : 30-50 sections, 200-500 fichiers
- Grand : 100+ sections, 1000+ fichiers

### Consommation Ressources

**CPU** :
- Idle : 5-10%
- Matching IA : 60-80% (1-4 cœurs)
- Génération PDF : 30-50%

**RAM** :
- Minimum : 2 GB
- Recommandé : 4 GB
- Grand projet : 8 GB

**Stockage** :
- Installation : 500 MB (avec modèles IA)
- Par projet VDB : 100-500 MB (output)

---

## 🔧 Évolutions Architecture

### En Développement
- 🌐 **API REST** pour intégration externe
- 📊 **Dashboard Analytics** (métriques temps réel)
- 🔄 **Système de Versioning** (tracking révisions VDB)

### Roadmap Future
- ☁️ **Cloud Deployment** (AWS/Azure)
- 🚀 **Scalabilité Horizontale** (multi-workers)
- 🤖 **Fine-tuning Modèles IA** sur données client
- 🔗 **Intégrations** SharePoint, Documentum, SAP

---

[⬅️ Retour à la documentation](../README.md)

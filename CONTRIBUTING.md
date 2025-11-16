# Contribuer à la Documentation Docodile

Merci de votre intérêt pour améliorer la documentation Docodile !

## 📝 Types de Contributions Acceptées

Nous acceptons les contributions suivantes :

### ✅ Accepté
- **Corrections de fautes** (orthographe, grammaire, typos)
- **Clarifications** : Amélioration de la clarté des explications
- **Exemples supplémentaires** : Cas d'usage, snippets de code
- **Traductions** : Versions anglaises des documents
- **Questions FAQ** : Nouvelles questions fréquentes
- **Améliorations de formatage** : Markdown, structure, lisibilité

### ❌ Non Accepté
- Modifications du code source Docodile (propriétaire, non public)
- Changements majeurs de structure sans discussion préalable
- Contenu publicitaire ou promotionnel
- Informations confidentielles ou sensibles

---

## 🚀 Comment Contribuer

### 1. Fork & Clone

```bash
# Fork le repository sur GitHub (bouton "Fork")

# Clone votre fork
git clone https://github.com/VOTRE-USERNAME/docodile-public.git
cd docodile-public
```

### 2. Créer une Branche

```bash
# Créer une branche pour votre contribution
git checkout -b fix/typo-readme
# ou
git checkout -b feat/add-faq-question
```

**Convention de nommage** :
- `fix/` : Corrections (typos, bugs doc)
- `feat/` : Nouvelles sections ou exemples
- `docs/` : Améliorations générales de documentation

### 3. Faire vos Modifications

Éditez les fichiers Markdown avec votre éditeur préféré :
- `README.md` : Page principale
- `docs/VDB.md` : Documentation VDB
- `docs/USO.md` : Documentation USO
- `docs/ARCHITECTURE.md` : Architecture technique
- `docs/FAQ.md` : Questions fréquentes

**Guidelines d'écriture** :
- Utilisez un langage clair et concis
- Ajoutez des exemples quand c'est pertinent
- Utilisez des emojis pour la lisibilité (avec modération)
- Respectez le ton professionnel mais accessible

### 4. Tester vos Modifications

Prévisualisez le rendu Markdown :
- **VS Code** : Extension "Markdown Preview Enhanced"
- **GitHub** : Preview dans l'interface web
- **En ligne** : [StackEdit](https://stackedit.io/), [Dillinger](https://dillinger.io/)

### 5. Commit & Push

```bash
# Ajouter vos modifications
git add .

# Commit avec message descriptif
git commit -m "fix: corriger typo dans README section VDB"

# Push vers votre fork
git push origin fix/typo-readme
```

**Convention de commits** :
- `fix: ...` : Corrections
- `feat: ...` : Nouvelles fonctionnalités
- `docs: ...` : Améliorations documentation
- `style: ...` : Formatage, sans changement de contenu

### 6. Créer une Pull Request

1. Allez sur votre fork GitHub
2. Cliquez "Compare & pull request"
3. Remplissez le template de PR :
   - **Titre** : Résumé concis de vos changements
   - **Description** : Détails de ce que vous avez modifié et pourquoi
4. Soumettez la PR

---

## 📋 Checklist PR

Avant de soumettre votre Pull Request, vérifiez :

- [ ] Pas de fautes d'orthographe/grammaire
- [ ] Markdown valide (preview OK)
- [ ] Liens fonctionnels (si nouveaux liens ajoutés)
- [ ] Cohérence avec le style existant
- [ ] Commit messages descriptifs
- [ ] Branch à jour avec `main`

---

## 🔍 Processus de Review

1. **Soumission** : Vous créez la PR
2. **Review** : L'équipe Docodile examine vos modifications (1-3 jours)
3. **Feedback** : Commentaires ou demandes de modifications
4. **Révision** : Vous apportez les changements si nécessaire
5. **Merge** : PR acceptée et fusionnée dans `main`

---

## 💡 Idées de Contributions

Besoin d'inspiration ? Voici des idées :

### Corrections Rapides
- Corriger les typos
- Améliorer la grammaire
- Réparer les liens cassés
- Uniformiser le formatage

### Améliorations Moyennes
- Ajouter des exemples concrets
- Créer des diagrammes (mermaid.js)
- Enrichir la FAQ
- Traduire en anglais

### Contributions Majeures
- Créer un guide d'installation détaillé
- Rédiger des tutoriels pas-à-pas
- Documenter des cas d'usage complexes
- Créer une section troubleshooting

---

## 🎨 Guide de Style

### Markdown

**Titres** :
```markdown
# Titre Niveau 1 (un seul par page)
## Titre Niveau 2
### Titre Niveau 3
```

**Listes** :
```markdown
- Point de liste
  - Sous-point indenté (2 espaces)
- Autre point

1. Liste numérotée
2. Deuxième élément
```

**Code** :
```markdown
Code inline : `docodile_client.py`

Code block :
```python
def fonction():
    return "exemple"
\`\`\`
```

**Emojis** :
- ✅ : Validé, fonctionnel, autorisé
- ❌ : Interdit, non fonctionnel, erreur
- ⚠️ : Attention, avertissement
- 📊 : Données, statistiques
- 🚀 : Fonctionnalité, lancement
- 🔧 : Configuration, technique
- 📝 : Documentation, notes

**Tableaux** :
```markdown
| Colonne 1 | Colonne 2 |
|-----------|-----------|
| Valeur A  | Valeur B  |
```

### Ton et Style

**Préférez** :
- Ton professionnel mais accessible
- Phrases courtes et claires
- Exemples concrets
- Listes à puces pour la lisibilité

**Évitez** :
- Jargon excessif sans explication
- Phrases trop longues
- Ambiguïtés
- Anglicismes inutiles (sauf termes techniques)

---

## ❓ Questions ?

**Avant de contribuer** :
- Consultez la [FAQ](docs/FAQ.md)
- Lisez les [issues existantes](https://github.com/votre-username/docodile-public/issues)

**Pour discuter d'une contribution majeure** :
- Créez une [issue](https://github.com/votre-username/docodile-public/issues/new) pour en discuter d'abord
- Email : contact@docodile.fr

---

## 🙏 Remerciements

Merci de contribuer à améliorer la documentation Docodile !

Chaque contribution, aussi petite soit-elle, aide la communauté d'utilisateurs.

---

[⬅️ Retour au README](README.md)

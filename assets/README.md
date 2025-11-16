# Assets Docodile

Ce dossier contient les ressources visuelles de Docodile.

## Structure

```
assets/
├── logos/          # Logos Docodile (différents formats)
│   ├── logo.svg    # Logo vectoriel (format préféré)
│   ├── logo.png    # Logo PNG haute résolution
│   ├── logo.ico    # Favicon pour site web
│   └── ...
│
└── images/         # Images diverses (screenshots, diagrammes)
    ├── screenshots/
    ├── diagrams/
    └── ...
```

## Formats de Logo

### Logo Principal
- **Format vectoriel** : `logo.svg` (scalable, préféré)
- **PNG haute résolution** : `logo.png` (2000x2000px minimum)
- **Favicon** : `logo.ico` (16x16, 32x32, 64x64 inclus)

### Variantes
- Logo couleur (fond blanc)
- Logo blanc (fond transparent, pour fonds sombres)
- Logo monochrome (noir & blanc)

## Charte Graphique

**Couleur principale Docodile** : `#00C896` (vert/turquoise)

**Utilisation recommandée** :
- Logo sur fond blanc : Version couleur
- Logo sur fond sombre : Version blanche
- Favicon site : 32x32px avec marge 2px

## Ajout de Visuels

Pour ajouter des visuels :

```bash
cd /home/cleme/projects/docodile-public/assets

# Ajouter vos fichiers
cp /chemin/vers/logo.ico logos/
cp /chemin/vers/logo.svg logos/
cp /chemin/vers/logo.png logos/

# Commit et push
git add assets/
git commit -m "feat: add Docodile visual assets (logo, favicon)"
git push
```

## Licence

Les visuels Docodile (logos, icônes) sont la propriété de Docodile.
Utilisation autorisée uniquement pour référencer Docodile dans un contexte approprié.

Pas d'utilisation commerciale sans autorisation : contact@docodile.fr

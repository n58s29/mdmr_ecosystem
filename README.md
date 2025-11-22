# 🕸️ Réseau d'Amis - Visualisation en Toile d'Araignée

Outil de visualisation interactive pour cartographier les relations entre amis et connaissances.

## 📋 Prérequis

- **Python 3.8+** installé sur votre ordinateur
  - Télécharger depuis: https://www.python.org/downloads/
  - ⚠️ Cochez "Add Python to PATH" pendant l'installation

## 🚀 Installation

1. **Première utilisation**: Double-cliquez sur `install.bat`
   - Crée l'environnement virtuel Python
   - Installe toutes les dépendances nécessaires

## 📊 Préparation des données

### Structure des fichiers Excel requis

Vous devez préparer **2 fichiers Excel** dans le dossier `data/input/`:

#### Fichier 1: Matrice d'adjacence (ex: Classeur2.xlsx)
Tableau avec les personnes en lignes et colonnes, avec un "x" pour indiquer les relations:

| ID | Prénom NOM | Marilia DURAND | Mathieu RIBOURG | Thomas SALEH | ... |
|----|------------|----------------|-----------------|--------------|-----|
| 1  | Marilia DURAND | - | x | x | ... |
| 2  | Mathieu RIBOURG | | - | x | ... |
| 3  | Thomas SALEH | | | - | ... |

#### Fichier 2: Rattachements (ex: Classeur3.xlsx)
Tableau indiquant d'où chaque personne est connue:

| ID | Prénom Nom | Rattachement origine | Type rattachement origine |
|----|------------|----------------------|---------------------------|
| 1  | Marilia DURAND | - | - |
| 2  | Mathieu RIBOURG | - | - |
| 3  | Thomas SALEH | Mathieu RIBOURG | Ami.e d'enfance |
| 4  | Thibault LOISEAU | Mathieu RIBOURG | Ami.e d'enfance |

### Types de rattachement disponibles
- `Famille` - Liens familiaux
- `Ami.e d'enfance` - Amis d'enfance
- `Ami.e d'école` - Amis d'école
- `Travail` - Collègues
- `Sport` - Relations sportives
- `Autre` - Autres types de relations

## 🎯 Utilisation

### Méthode simple (Glisser-Déposer)

1. **Préparez vos fichiers Excel** comme décrit ci-dessus
2. **Glissez vos 2 fichiers Excel** dans le dossier `data/input/`
3. **Double-cliquez sur `run.bat`**
   - Convertit vos Excel en JSON
   - Vérifie les données
4. **Double-cliquez sur `visu.bat`**
   - Génère la visualisation HTML
   - Ouvre automatiquement dans votre navigateur

### Résultats

Tous les fichiers générés se trouvent dans `data/output/`:
- `reseau_amis.json` - Données au format JSON
- `reseau_amis.html` - Visualisation interactive

## 🎨 Fonctionnalités de la visualisation

### Interface interactive
- **Zoom**: Molette de la souris
- **Déplacement**: Clic + glisser sur le fond
- **Sélection**: Cliquez sur un nœud pour voir ses détails
- **Contrôles physiques**: Ajustez la force de répulsion et la gravité

### Informations affichées
- **Groupes colorés**: Chaque type de personne a une couleur
- **Relations colorées**: Chaque type de relation a une couleur
- **Statistiques**: Nombre de personnes, connexions, groupes
- **Détails au clic**: Informations sur chaque personne

## 🎨 Personnalisation

### Modifier les couleurs

Éditez le fichier `convert_to_json.py` et modifiez le dictionnaire `COULEURS_CATEGORIES`:

```python
COULEURS_CATEGORIES = {
    "Couple": "#FF1744",        # Rouge
    "Famille": "#FFA726",       # Orange
    "Ami.e d'enfance": "#66BB6A", # Vert
    "Ami.e d'école": "#42A5F5",  # Bleu
    "Travail": "#AB47BC",       # Violet
    "Sport": "#26C6DA",         # Cyan
    "Autre": "#78909C"          # Gris
}
```

## 🔧 Structure du projet

```
reseau_amis/
├── install.bat              # Installation de l'environnement
├── run.bat                  # Conversion Excel → JSON
├── visu.bat                 # Génération du HTML
├── requirements.txt         # Dépendances Python
├── convert_to_json.py       # Script de conversion
├── generate_visu.py         # Script de visualisation
├── data/
│   ├── input/              # 📥 Placez vos fichiers Excel ici
│   └── output/             # 📤 Fichiers générés (JSON + HTML)
└── venv/                   # Environnement virtuel (auto-généré)
```

## ❓ Dépannage

### "Python n'est pas reconnu..."
- Installez Python depuis https://www.python.org/downloads/
- Lors de l'installation, cochez **"Add Python to PATH"**
- Redémarrez votre ordinateur après l'installation

### "Il faut 2 fichiers Excel..."
- Vérifiez que vous avez bien 2 fichiers `.xlsx` dans `data/input/`
- Les fichiers doivent avoir la structure décrite ci-dessus

### Le réseau ne s'affiche pas correctement
- Cliquez sur "Recentrer la vue" dans la barre latérale
- Ajustez les contrôles de "Force de répulsion" et "Force gravitationnelle"
- Cliquez sur "Réinitialiser" pour revenir aux paramètres par défaut

### Modifier les données
1. Modifiez vos fichiers Excel dans `data/input/`
2. Relancez `run.bat` pour reconvertir
3. Relancez `visu.bat` pour régénérer la visualisation

## 📝 Notes

- Les fichiers Excel d'origine ne sont jamais modifiés
- Chaque exécution de `run.bat` écrase le JSON précédent
- Chaque exécution de `visu.bat` écrase le HTML précédent
- Sauvegardez vos visualisations importantes en les renommant

## 🎉 Astuce

Pour créer plusieurs visualisations différentes:
1. Renommez `data/output/reseau_amis.html` en `reseau_amis_v1.html`
2. Modifiez vos données Excel
3. Relancez `run.bat` puis `visu.bat`
4. Vous aurez maintenant 2 versions!

---

Créé avec ❤️ pour visualiser les réseaux sociaux

# Analyse des causes d'attrition chez TechNova Partners

![Python Version](https://img.shields.io/badge/python-3.13%2B-blue)
![UV](https://img.shields.io/badge/uv-package%20manager-orange)
![Status](https://img.shields.io/badge/status-en%20cours-yellow)

## 📋 Description du projet

Projet de data science visant à identifier les causes d'attrition (départs d'employés) au sein de l'ESN TechNova Partners. L'analyse s'appuie sur trois sources de données :

- **SIRH** : Informations RH (âge, salaire, poste, ancienneté)
- **Évaluations** : Notes de performance et satisfaction des employés
- **Sondage** : Données comportementales et variable cible (`a_quitte_l_entreprise`)

## 🎯 Objectifs

1. **Analyse exploratoire** : Identifier les différences clés entre employés ayant quitté et ceux restés
2. **Modélisation** : Créer un modèle de classification pour prédire les démissions
3. **Interprétation** : Extraire les causes potentielles avec SHAP

## 🚀 Installation

### Prérequis

- Python 3.13+
- [UV](https://docs.astral.sh/uv/) (gestionnaire de packages ultra-rapide)

### Installation de UV

```bash
# Sur Linux/macOS
curl -LsSf https://astral.sh/uv/install.sh | sh

# Redémarrer votre terminal ou recharger votre configuration
source ~/.bashrc  # ou source ~/.zshrc
```

### Installation du projet

```bash
# 1. Cloner le repository
git clone https://github.com/vler0ux/esn.git
cd esn

# 2. Installer les dépendances avec UV
uv sync

# 3. Ajouter Jupyter Lab (si pas déjà fait)
uv add jupyterlab ipykernel

# 4. Vérifier l'installation
uv run jupyter lab --version

# 5.Synchroniser et installer toutes les dépendances depuis pyproject.toml
uv sync

si vous n'avez pas encore de pyproject.toml complet, ajoutez les packages un par un :

uv add pandas numpy matplotlib seaborn plotly scikit-learn xgboost catboost imbalanced-learn jupyterlab ipykernel notebook
```
## 📂 Structure du projet

```
p4_ESN_uv/
│
├── extrait_sirh.csv           # Données SIRH
├── extrait_eval.csv           # Données évaluations
├── extrait_sondage.csv        # Données sondage (avec variable cible)
├── note_ESN.docx              # Cahier des charges du projet
│
├── 01_analyse_exploratoire.ipynb   # Notebook d'analyse exploratoire
│
├── pyproject.toml             # Configuration du projet et dépendances
├── uv.lock                    # Fichier de verrouillage des versions
├── .gitignore                 # Fichiers à ignorer par Git
└── README.md                  # Ce fichier
```

## 🔧 Utilisation

### Lancer Jupyter Lab

```bash
cd ~/OpenClassRoom/p4_ESN_uv
uv run jupyter lab
```

Jupyter Lab s'ouvrira automatiquement dans votre navigateur à l'adresse `http://localhost:8888`.

### Exécuter les notebooks

1. Ouvrir le notebook `01_analyse_exploratoire.ipynb`
2. Exécuter les cellules séquentiellement (Shift + Enter)
3. Valider chaque sous-étape avant de passer à la suivante

## 📊 Étapes du projet

### ✅ Étape 1 : Configuration de l'environnement
- Installation de UV
- Configuration du `pyproject.toml`
- Installation des dépendances

### 🔄 Étape 2 : Analyse exploratoire (en cours)
- [x] **Sous-étape 2.1** : Chargement des données
- [x] **Sous-étape 2.2** : Identification et nettoyage des colonnes
- [ ] **Sous-étape 2.3** : Fusion des 3 fichiers
- [ ] **Sous-étape 2.4** : Statistiques descriptives
- [ ] **Sous-étape 2.5** : Visualisations

### 🔮 Étape 3 : Feature engineering (à venir)
- Encodage des variables qualitatives
- Gestion des corrélations
- Création de nouvelles features

### 🤖 Étape 4 : Modélisation (à venir)
- Séparation train/test avec stratification
- Modèles : Dummy, Linéaire, Non-linéaire (XGBoost, CatBoost)
- Gestion du déséquilibre des classes
- Fine-tuning des hyperparamètres

### 🔍 Étape 5 : Interprétabilité (à venir)
- Feature importance globale (SHAP)
- Feature importance locale (Waterfall plots)
- Extraction des causes d'attrition

### 📊 Étape 6 : Présentation (à venir)
- Support PowerPoint
- Communication des insights clés

## 📦 Dépendances principales

```toml
[tool.uv]
dependencies = [
    "pandas>=2.2.0",
    "numpy>=2.0.0",
    "matplotlib>=3.9.0",
    "seaborn>=0.13.0",
    "scikit-learn>=1.5.0",
    "xgboost>=2.1.0",
    "catboost>=1.2.0",
    "imbalanced-learn>=0.12.0",
    "shap>=0.46.0",
    "jupyterlab>=4.0.0",
]
```

## 🛠️ Commandes utiles

### Gestion des dépendances

```bash
# Ajouter une dépendance
uv add <package-name>

# Mettre à jour les dépendances
uv sync

# Lister les dépendances installées
uv pip list

# Exécuter un script Python
uv run python script.py

# Exécuter une commande dans l'environnement
uv run <commande>
```

### Git

```bash
# Statut du repository
git status

# Ajouter des fichiers
git add .

# Commit
git commit -m "Description du commit"

# Pousser vers GitHub
git push origin main
```

## 📝 Notes importantes

### Variables à nettoyer
- **augementation_salaire_precedente** : Format "11 %" → conversion en float nécessaire

### Clés de jointure
Les 3 fichiers (SIRH, évaluations, sondage) sont **déjà alignés** avec le même ordre de 1470 employés. La jointure se fait donc par **index de ligne**.

### Déséquilibre des classes
La variable cible `a_quitte_l_entreprise` présente un déséquilibre (à vérifier). Des techniques de rééquilibrage seront nécessaires (SMOTE, class_weight, etc.).

## 👥 Auteur

**Véronique** - Projet réalisé dans le cadre de la formation Data Scientist - OpenClassrooms

## 📄 Licence

Ce projet est à usage éducatif dans le cadre de la formation OpenClassrooms.

## 🔗 Ressources

- [Documentation UV](https://docs.astral.sh/uv/)
- [Documentation scikit-learn](https://scikit-learn.org/)
- [Documentation SHAP](https://shap.readthedocs.io/)
- [Cours OpenClassrooms - Maîtrisez l'apprentissage supervisé](https://openclassrooms.com/fr/courses/8431846-maitrisez-lapprentissage-supervise)

---

**Dernière mise à jour** : Janvier 2026
# Générateur de Site Généalogique Gosset

> Outil de conversion Gramps Web → Site web HTML autonome pour partager votre arbre généalogique

---

## 📋 À propos

Ce projet permet de **générer un site web statique** à partir des données d'un arbre généalogique hébergé sur **Gramps Web**. Le résultat est un fichier HTML autonome (avec CSS externe) accompagnés des médias (photos, documents), prêt à être hébergé n'importe où.

### Fonctionnalités

- ✅ Import automatique des données JSON depuis Gramps Web
- ✅ Téléchargement de tous les médias associés
- ✅ Génération de fiches individuelles détaillées
- ✅ Visualisation des liens familiaux (parents, conjoints, enfants)
- ✅ Arbre généalogique sur N générations
- ✅ Intégration des photos et documents
- ✅ Design responsive avec CSS externe
- ✅ **Deux interfaces** : CLI (ligne de commande) et GUI (graphique)

---

## 🏗️ Structure du projet

```
.
├── generate.py              # Script principal CLI (orchestration)
├── gramps_import.py         # Import JSON + médias depuis Gramps Web
├── gramps_parser.py         # Parseur du format JSON Gramps
├── gramps_to_html.py        # Génération HTML (version CLI)
├── gramps_html_generator.py # Moteur de génération HTML
├── gramps_ihm.py            # Interface graphique (Tkinter)
├── style.css                # Feuille de style CSS externe
├── export.json              # Données généalogiques (exemple)
├── index.html               # Résultat généré (exemple)
├── media/                  # Dossier des médias (photos, documents)
└── README.md                # Ce fichier
```

---

## 🛠️ Prérequis

- **Python** 3.8 ou supérieur
- **Git** (pour cloner le dépôt)
- **Accès à une instance Gramps Web** avec les identifiants

### Dépendances Python

```bash
pip install requests
```

*(Aucune autre dépendance externe n'est nécessaire)*

---

## 📥 Installation

### 1. Cloner le dépôt

```bash
git clone http://192.168.1.26:30008/bernard/magenea.git
cd magenea
```

### 2. Installer les dépendances

```bash
pip install -r requirements.txt  # si le fichier existe
# ou
pip install requests
```

---

## 🚀 Utilisation

### Méthode 1 : Interface en ligne de commande (CLI)

Le moyen le plus simple pour générer le site complet :

```bash
python3 generate.py
```

Le script vous demandera :
- Le mot de passe de votre compte Gramps Web (masqué à la saisie)

Il exécute automatiquement :
1. Téléchargement du JSON et des médias depuis Gramps Web
2. Génération du fichier `index.html`

#### Options avancées

```bash
# Générer avec un nombre spécifique de générations
python3 gramps_to_html.py export.json sortie.html 10

# Importer uniquement sans générer
python3 gramps_import.py \
    --url http://100.64.202.79:30179 \
    --user bernard \
    --password votremotdepasse \
    --force
```

### Méthode 2 : Interface graphique (GUI)

Pour une utilisation plus visuelle :

```bash
python3 gramps_ihm.py
```

Une fenêtre Tkinter s'ouvre et vous guide à travers :
1. Sélection du fichier JSON
2. Choix du nombre de générations
3. Sélection du fichier HTML de sortie

### Méthode 3 : Étapes manuelles

```bash
# 1. Importer les données
python3 gramps_import.py \
    --url http://votre-serveur-gramps:30179 \
    --user votrenom \
    --password votremotdepasse \
    --force

# 2. Générer le HTML
python3 gramps_to_html.py export.json index.html 10
```

---

## 📊 Paramètres de configuration

| Paramètre | Description | Valeur par défaut |
|-----------|-------------|-------------------|
| `GRAMPS_URL` | URL de l'instance Gramps Web | `http://100.64.202.79:30179` |
| `GRAMPS_USER` | Nom d'utilisateur | `bernard` |
| `JSON_FILE` | Fichier JSON d'export | `export.json` |
| `HTML_FILE` | Fichier HTML généré | `index.html` |
| `MAX_GENERATIONS` | Nombre de générations dans l'arbre | `10` |

> ⚠️ Modifiez ces paramètres directement dans `generate.py` ou passez-les en arguments.

---

## 📂 Sortie générée

Après exécution, vous obtiendrez :

```
.
├── index.html          # Site web complet
├── style.css          # Feuille de style
└── media/             # Tous les médias (photos, documents)
    ├── photo1.png
    ├── photo2.jpg
    └── ...
```

Le fichier `index.html` est **autonome** et peut être :
- Ouvert directement dans un navigateur
- Hébergé sur un serveur web (GitHub Pages, Netlify, etc.)
- Copié sur une clé USB pour partage hors ligne

---

## 🌿 Branches

| Branche | Description |
|---------|-------------|
| `main` | Version stable du projet |
| `evolution-css-separe` | **Branche actuelle** - Développement avec CSS externe séparé |
| `correction-evolution` | Corrections et améliorations |

---

## 🤝 Contribution

Les contributions sont les bienvenues !

1. Forker le projet
2. Créer une branche de fonctionnalité (`git checkout -b feature/ma-fonctionnalité`)
3. Commiter vos changements (`git commit -m 'Ajout de ma fonctionnalité'`)
4. Pousser vers la branche (`git push origin feature/ma-fonctionnalité`)
5. Ouvrir une Pull Request

---

## 📄 Licence

Ce projet est sous licence **MIT** - libre d'utilisation pour un usage personnel ou commercial.

---

## 📞 Contact

Pour toute question ou suggestion, contactez : **Bernard Gosset**

---

*Généré avec ❤️ pour la généalogie famille Gosset - Mai 2026*

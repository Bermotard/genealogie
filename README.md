# genealogie
Exposer mon arbre généalogique.

Ce site est généré à partir du programme suivant:

# magenea

Générateur HTML de généalogie à partir d'un export **Gramps** au format **JSON Lines**.

Le projet produit un fichier HTML autonome avec :
- listage des individus (liens père/mère/enfants)
- filtre hommes/femmes
- listage des familles
- arbre des ascendants avec profondeur configurable
- liens vers les médias rattachés aux individus

## Fichiers principaux

- `gramps_to_html.py` : exécution en ligne de commande
- `gramps_ihm.py` : interface graphique (`tkinter`)
- `gramps_parser.py` : lecture/parsing des données Gramps
- `gramps_html_generator.py` : génération du HTML

## Prérequis

- Python 3.10+
- Export Gramps en `.json` (1 objet JSON par ligne)
- Optionnel : `medias.zip` dans le même dossier que le JSON

## Utilisation en ligne de commande

```bash
python3 gramps_to_html.py <fichier.json> [sortie.html] [nb_generations]
```

Exemples :

```bash
python3 gramps_to_html.py gramps-web-export-20260504125737.json
python3 gramps_to_html.py gramps-web-export-20260504125737.json genealogie.html 9
```

### Paramètres

- `fichier.json` : export Gramps
- `sortie.html` : nom du fichier HTML de sortie (optionnel)
- `nb_generations` : profondeur de l'arbre (optionnel, entier >= 1)

Si `nb_generations` n'est pas fourni, le programme le demande (défaut `4`).

## Utilisation via IHM

```bash
python3 gramps_ihm.py
```

L'application demande successivement :
1. Le fichier JSON (explorateur)
2. Le nombre de générations
3. Le fichier HTML de sortie

## Gestion des médias

Si un fichier `medias.zip` est présent à côté du JSON :
- les médias référencés sont extraits automatiquement vers `media/` (à côté du HTML)
- les fiches individus affichent des liens cliquables vers ces documents

Structure attendue après génération :

```text
sortie.html
media/
  <fichiers .jpg/.png/.pdf ...>
```

## Dépannage

- **Lien média introuvable** : régénérer le HTML et vérifier que le dossier `media/` a bien été créé.
- **JSON invalide** : vérifier qu'il s'agit d'un export Gramps en JSON Lines.
- **Arbre trop large** : utiliser les boutons de zoom dans l'onglet Arbre (`-`, `100%`, `+`).

## Licence

Usage privé/projet personnel (à ajuster selon vos besoins).

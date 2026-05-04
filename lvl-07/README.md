# Bandit Level 7 

## 🎯 Objectif
Le mot de passe est stocké dans le fichier `data.txt`, à côté du mot "millionth".

## 🧠 Raisonnement
J'ai d'abord fait `ls` pour voir ce qu'il y avait dans le dossier, puis `pwd` pour confirmer où j'étais.
J'ai d'abord essayé `cat` mais le fichier était énorme — environ 1 minute de texte à défiler.
J'ai alors pensé à utiliser `grep` pour chercher directement le mot "millionth" dans le fichier, ce qui m'a donné la ligne exacte avec le mot de passe.

## 🔧 Commandes utilisées

| Commande | Syntaxe | Description |
|----------|---------|-------------|
| `ls` | `ls` | Liste les fichiers du répertoire courant |
| `pwd` | `pwd` | Affiche le répertoire courant |
| `cat` | `cat data.txt` | Affiche tout le contenu d'un fichier (pas adapté aux gros fichiers) |
| `grep` | `grep <mot> <fichier>` | Recherche une chaîne de caractères dans un fichier |
| `du` | `du <fichier>` | Affiche la taille d'un fichier ou dossier |

## 💡 Difficultés rencontrées
- J'ai fait `cat` sans vérifier la taille du fichier → 1 minute de texte qui défile 😅
- Ma première commande `grep millionth` était incomplète : j'avais oublié de préciser le nom du fichier `data.txt`
- Leçon retenue : toujours vérifier la taille avec `du` avant de faire `cat` sur un fichier inconnu

## 📚 Ce que j'ai appris
`grep` permet de chercher une chaîne de caractères dans un fichier et affiche uniquement la ligne qui contient ce mot.
Syntaxe : `grep <mot_cherché> <fichier>`

Sur un gros fichier, `cat` est inutile — `grep` permet d'aller directement à l'information sans tout lire.
# Bandit Level 4

## 🎯 Objectif
Trouver le mot de passe dans le seul fichier "human-readable" (lisible par un humain) dans le dossier `inhere`, parmi 10 fichiers.

## 🧠 Raisonnement
En entrant dans le dossier `inhere` avec `cd`, j'ai trouvé 10 fichiers nommés `-file00` à `-file09`. L'objectif était de trouver le seul lisible par un humain. Plutôt que de les ouvrir un par un avec `cat`, j'ai utilisé la commande `file` pour identifier le type de chaque fichier. Comme les noms commencent par `-`, j'ai utilisé `./` devant. Pour ne pas faire la commande 10 fois, j'ai utilisé le wildcard `*` pour tester tous les fichiers d'un coup. Seul `-file07` affichait "ASCII text", donc lisible par un humain. J'ai ensuite fait `cat` pour lire son contenu.

## 🔧 Commandes utilisées

| Commande | Syntaxe | Description |
|----------|---------|-------------|
| `cd` | `cd <dossier>` | Entre dans un dossier |
| `ls` | `ls` | Liste les fichiers visibles |
| `file` | `file ./<fichier>` | Identifie le type d'un fichier (ASCII text, data, DOS executable...) |
| `file` + wildcard | `file ./-file0*` | Identifie le type de tous les fichiers correspondant au pattern en une seule commande |
| `cat` | `cat ./<fichier>` | Affiche le contenu d'un fichier |

## 💡 Difficultés rencontrées
Les fichiers commençaient par `-`, ce qui posait problème avec `file` sans `./`. J'ai aussi découvert le wildcard `*` qui permet de remplacer n'importe quelle suite de caractères dans un nom de fichier, évitant de répéter la commande 10 fois.

## 📚 Ce que j'ai appris
- **ASCII text** = fichier contenant des caractères lisibles par un humain (lettres, chiffres, symboles). L'ASCII est un système qui associe des nombres à des caractères.
- **Wildcard `*`** = caractère joker qui remplace n'importe quelle suite de caractères. Très utile pour appliquer une commande sur plusieurs fichiers d'un coup.
- `file` permet de connaître le type d'un fichier sans avoir à l'ouvrir.
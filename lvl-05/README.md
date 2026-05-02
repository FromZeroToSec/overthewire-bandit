# Bandit Level 5

## 🎯 Objectif
Trouver le mot de passe dans un fichier avec 3 propriétés précises : human-readable, 1033 bytes, non exécutable. Le fichier est quelque part dans le dossier `inhere` qui contient 20 sous-dossiers.

## 🧠 Raisonnement
En entrant dans `inhere` avec `cd`, j'ai vu 20 dossiers `maybehere00` à `maybehere19`. Trop de fichiers pour explorer manuellement. J'ai d'abord essayé `find` seul mais ça listait tout sans filtrer. J'ai aussi essayé `du -b` pour voir les tailles mais ça donnait la taille des dossiers, pas des fichiers. J'ai cherché comment utiliser `find` avec une taille en bytes et découvert l'option `-size` avec le suffixe `c` pour les bytes. La commande `find -size 1033c` a retourné un seul fichier : `./maybehere07/.file2`. J'ai ensuite fait `cat` pour lire son contenu.

## 🔧 Commandes utilisées

| Commande | Syntaxe | Description |
|----------|---------|-------------|
| `cd` | `cd <dossier>` | Entre dans un dossier |
| `cd ..` | `cd ...` | Remonte d'un niveau dans l'arborescence |
| `ls` | `ls` | Liste les fichiers visibles |
| `ls -l` | `ls -l` | Liste les fichiers avec les détails (permissions, taille, date...) |
| `find` | `find` | Cherche des fichiers — sans option, liste tout |
| `find -size` | `find -size 1033c` | Cherche des fichiers par taille exacte (`c` = bytes) |
| `cat` | `cat <chemin/fichier>` | Affiche le contenu d'un fichier |

## 💡 Difficultés rencontrées
`find` seul listait absolument tous les fichiers sans filtrer. `du -b` montrait la taille des dossiers et non des fichiers individuels. Il fallait connaître l'option `-size` de `find` et savoir que `c` signifie bytes. Aussi, le fichier s'appelait `.file2` et non `.file02` — une faute de frappe qui a causé une erreur.

## 📚 Ce que j'ai appris
- `find -size 1033c` permet de chercher un fichier par taille exacte en bytes
- `c` après la valeur dans `find -size` signifie "bytes"
- `cd ..` permet de remonter d'un niveau dans l'arborescence
- `ls -l` affiche les détails des fichiers dont leur taille
- Quand il y a des centaines de fichiers, les outils de filtrage comme `find` sont indispensables
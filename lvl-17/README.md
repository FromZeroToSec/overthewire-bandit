# Bandit Level 17

## 🎯 Objectif
Se connecter en bandit17 via une clé SSH privée récupérée au niveau précédent, puis comparer deux fichiers (`passwords.old` et `passwords.new`) pour trouver la ligne qui a changé — c'est le mot de passe du niveau suivant.

## 🧠 Raisonnement
La connexion se fait avec une clé privée SSH, mais avant de l'utiliser il faut lui appliquer les bonnes permissions avec `chmod 600`, sinon SSH refuse de l'utiliser et demande un mot de passe.

Une fois connecté, deux fichiers sont présents : `passwords.old` et `passwords.new`. La commande `diff` permet de comparer les deux et d'identifier la seule ligne qui diffère.

Dans l'output de `diff passwords.new passwords.old` :
- `<` = la ligne venant du **premier fichier** (`passwords.new`)
- `>` = la ligne venant du **deuxième fichier** (`passwords.old`)

Le mot de passe du niveau suivant se trouve dans `passwords.new`, donc on prend la ligne marquée `<`.

## 🔧 Commandes utilisées

| Commande | Description |
|----------|-------------|
| `chmod 600 <fichier>` | Restreint les permissions : lecture + écriture pour moi seul (requis pour les clés SSH) |
| `ssh bandit17@bandit.labs.overthewire.org -i <clé> -p 2220` | Connexion SSH avec une clé privée |
| `ls` | Lister les fichiers du répertoire courant |
| `diff <fichier1> <fichier2>` | Compare deux fichiers et affiche les lignes différentes |

## 💡 Difficultés rencontrées
- Oubli du `chmod 600` sur la clé privée → SSH demandait un mot de passe
- Confusion dans l'interprétation de l'output de `diff` : `<` et `>` représentent l'ordre des fichiers dans la commande, pas leur taille

## 📚 Ce que j'ai appris
- Une clé SSH privée doit avoir les permissions `600` pour être acceptée par SSH
- `diff fichier1 fichier2` compare deux fichiers ligne par ligne : `<` = fichier1, `>` = fichier2
- Pour trouver une modification entre deux versions d'un fichier, `diff` est l'outil idéal
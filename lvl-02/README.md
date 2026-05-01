# Bandit  Level 2

## 🎯 Objectif
Trouver le mot de passe stocké dans un fichier appelé `-` situé dans le répertoire home.

## 🧠 Raisonnement
En listant le contenu du répertoire avec `ls`, j'ai trouvé le fichier `-`. En essayant de le lire directement avec `cat -`, ça ne fonctionnait pas car le terminal interprétait `-` comme une option de commande. J'ai cherché comment contourner ce problème et trouvé que `./` permet d'indiquer au terminal qu'il s'agit d'un fichier local et non d'une option.

## 🔧 Commandes utilisées

| Commande | Syntaxe | Description |
|----------|---------|-------------|
| `ssh` | `ssh user@host -p port` | Se connecter à un serveur distant via SSH |
| `pwd` | `pwd` | Affiche le chemin du dossier courant |
| `ls` | `ls` | Liste les fichiers et dossiers présents dans le répertoire courant |
| `cat` | `cat ./-` | Affiche le contenu d'un fichier — `./` précise que c'est un fichier local |

## 💡 Difficultés rencontrées
Le fichier s'appelait `-`, ce que le terminal interprétait comme une option de commande plutôt que comme un nom de fichier. J'ai aussi essayé `cd ./-` par réflexe, mais `cd` sert à naviguer dans des dossiers, pas à lire des fichiers.

## 📚 Ce que j'ai appris
Quand un fichier a un nom qui commence par `-`, le terminal le confond avec une option de commande. Utiliser `./` devant le nom du fichier indique explicitement au terminal qu'il s'agit d'un fichier situé dans le répertoire courant.
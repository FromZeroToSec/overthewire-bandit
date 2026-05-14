# Bandit Level 18

## 🎯 Objectif
Récupérer le mot de passe stocké dans un fichier `readme` dans le home directory de bandit18. Le problème : quelqu'un a modifié le fichier `.bashrc` pour nous déconnecter automatiquement dès qu'on se connecte en SSH.

## 🧠 Raisonnement
Une connexion SSH classique ouvre un shell interactif, qui lit et exécute `.bashrc` au démarrage — lequel contient probablement un `exit`, provoquant une déconnexion immédiate.

La solution : utiliser SSH pour exécuter une commande directement, sans ouvrir de shell interactif. Ainsi `.bashrc` n'est jamais lu et la commande s'exécute normalement.

Étapes :
1. Tentative de connexion classique → "Byebye !" → déconnexion immédiate
2. `ssh bandit18@... -p 2220 ls` → liste le home directory → `readme` visible
3. `ssh bandit18@... -p 2220 cat readme` → mot de passe récupéré ✅

## 🔧 Commandes utilisées

| Commande | Syntaxe | Description |
|----------|---------|-------------|
| `ssh` (avec commande) | `ssh user@host -p port <commande>` | Exécute une commande directement via SSH sans ouvrir de shell interactif |
| `ls` | `ls` | Liste les fichiers du répertoire courant |
| `cat` | `cat <fichier>` | Affiche le contenu d'un fichier |

## 💡 Difficultés rencontrées
- La connexion SSH classique déclenchait le `.bashrc` modifié et fermait la session avant de pouvoir faire quoi que ce soit
- Comprendre que `cat readme` tapé après le `ls` s'exécutait en local et non sur le serveur distant

## 📚 Ce que j'ai appris
- `.bashrc` est un fichier exécuté automatiquement à l'ouverture d'un shell bash — on peut y mettre des configs, alias, ou n'importe quelle commande
- SSH ne sert pas uniquement à ouvrir un shell interactif : on peut lui passer une commande directement en argument, ce qui bypass complètement `.bashrc`
- Quand SSH exécute une commande directe, il se ferme automatiquement après — c'est le comportement normal, pas une expulsion
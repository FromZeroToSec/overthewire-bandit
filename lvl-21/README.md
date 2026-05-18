# Bandit Level 21 

## 🎯 Objectif
Trouver le mot de passe de bandit22 en exploitant une tâche automatisée tournant via **cron**, le planificateur de tâches Linux.

## 🧠 Raisonnement
L'énoncé indique qu'un programme tourne automatiquement à intervalles réguliers via cron. En allant dans `/etc/cron.d/`, on trouve le fichier `cronjob_bandit22` qui pointe vers un script. En lisant ce script, on comprend qu'il copie automatiquement le mot de passe de bandit22 dans un fichier temporaire lisible par tous dans `/tmp/`. Il suffit alors de lire ce fichier.

## 🔧 Commandes utilisées

| Commande | Syntaxe | Description |
|---|---|---|
| `cd` | `cd /etc/cron.d/` | Se déplacer dans le dossier des tâches cron |
| `ls` | `ls` | Lister les fichiers du dossier |
| `cat` | `cat cronjob_bandit22` | Lire le fichier de config cron |
| `cat` | `cat /usr/bin/cronjob_bandit22.sh` | Lire le script exécuté par cron |
| `cat` | `cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv` | Lire le fichier contenant le mot de passe |

## 💡 Difficultés rencontrées
- Le concept de cron n'était pas clair au départ — comprendre qu'un script tourne automatiquement en arrière-plan sans intervention humaine
- Erreur de vouloir exécuter le script au lieu de juste le lire avec `cat`
- Confusion sur le rôle du `>` dans le script (redirection de sortie vers un fichier)

## 📚 Ce que j'ai appris
- **cron** est un planificateur de tâches Linux qui exécute des scripts automatiquement à intervalles définis (ici toutes les minutes avec `* * * * *`)
- Les configs cron se trouvent dans `/etc/cron.d/`
- L'opérateur `>` redirige la sortie d'une commande vers un fichier
- `chmod 644` rend un fichier lisible par tous les utilisateurs
- Un script peut tourner avec les permissions d'un autre utilisateur (ici bandit22) et ainsi accéder à des fichiers normalement inaccessibles
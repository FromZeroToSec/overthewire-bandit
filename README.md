# 🏴‍☠️ OverTheWire — Bandit

Progression personnelle sur le wargame [Bandit](https://overthewire.org/wargames/bandit/) d'OverTheWire.

## 📋 Progression

| Niveau | Writeup | Statut |
|--------|---------|--------|
| Level 0 | [📄 Voir](./lvl-0/README.md) | ✅ |
| Level 1 | [📄 Voir](./lvl-1/README.md) | ✅ |
| Level 2 | [📄 Voir](./lvl-2/README.md) | ✅ |
| Level 3 | [📄 Voir](./lvl-3/README.md) | ✅ |
| Level 4 | [📄 Voir](./lvl-4/README.md) | ✅ |
| Level 5 | [📄 Voir](./lvl-5/README.md) | ✅ |
| Level 6 | [📄 Voir](./lvl-6/README.md) | ✅ |
| Level 7 | [📄 Voir](./lvl-7/README.md) | ✅ |
| Level 8 | [📄 Voir](./lvl-8/README.md) | ✅ |
| Level 9 | [📄 Voir](./lvl-9/README.md) | ✅ |
| Level 10 | [📄 Voir](./lvl-10/README.md) | ✅ |
| Level 11 | [📄 Voir](./lvl-11/README.md) | ✅ |
| Level 12 | [📄 Voir](./lvl-12/README.md) | ✅ |
| Level 13 | [📄 Voir](./lvl-13/README.md) | ✅ |
| Level 14 | [📄 Voir](./lvl-14/README.md) | ✅ |
| Level 15 | [📄 Voir](./lvl-15/README.md) | ✅ |
| Level 16 | [📄 Voir](./lvl-16/README.md) | ✅ |
| Level 17 | [📄 Voir](./lvl-17/README.md) | ✅ |
| Level 18 | [📄 Voir](./lvl-18/README.md) | ✅ |
| Level 19 | [📄 Voir](./lvl-19/README.md) | ✅ |
| Level 20 | [📄 Voir](./lvl-20/README.md) | ✅ |
| Level 21 | [📄 Voir](./lvl-21/README.md) | ✅ |
| Level 22 | — | ⏳ |

## 🔧 Commandes apprises

| Commande | Description | Maîtrisée |
|----------|-------------|-----------|
| `ssh user@host -p port` | Connexion distante sécurisée via SSH | ✅ |
| `ssh user@host -i <clé> -p port` | Connexion SSH avec une clé privée | ✅ |
| `ssh user@host -p port <commande>` | Exécute une commande via SSH sans ouvrir de shell interactif | ✅ |
| `chmod 600 <fichier>` | Restreint les permissions : lecture+écriture pour moi seul | ✅ |
| `pwd` | Affiche le répertoire courant | ✅ |
| `ls` | Liste les fichiers et dossiers | ✅ |
| `ls -a` | Liste tous les fichiers, y compris les cachés | ✅ |
| `ls -l` | Liste les fichiers avec les détails | ✅ |
| `cat <fichier>` | Affiche le contenu d'un fichier | ✅ |
| `cat ./<fichier>` | Lit un fichier dont le nom commence par `-` | ✅ |
| `cd <dossier>` | Navigue dans un dossier | ✅ |
| `cd ..` | Remonte d'un niveau dans l'arborescence | ✅ |
| `cd -` | Retourne au répertoire précédent | ✅ |
| `file <fichier>` | Identifie le type d'un fichier | ✅ |
| `find -size <n>c` | Cherche des fichiers par taille exacte | ✅ |
| `find / -user <u> -group <g> -size <n>c` | Cherche un fichier selon plusieurs critères | ✅ |
| `2>/dev/null` | Redirige les erreurs vers la poubelle | ✅ |
| `*` (wildcard) | Remplace n'importe quelle suite de caractères | ✅ |
| `grep <mot> <fichier>` | Recherche une chaîne dans un fichier | ✅ |
| `sort <fichier>` | Trie les lignes d'un fichier | ✅ |
| `uniq -u` | Affiche uniquement les lignes uniques | ✅ |
| `cmd1 \| cmd2` | Pipe : passe l'output d'une commande à la suivante | ✅ |
| `du <fichier>` | Affiche la taille d'un fichier | ✅ |
| `strings <fichier>` | Extrait les chaînes lisibles d'un fichier binaire | ✅ |
| `base64 -d <fichier>` | Décode un fichier encodé en base64 | ✅ |
| `tr 'CHAINE1' 'CHAINE2'` | Substitue les caractères de CHAINE1 par CHAINE2 | ✅ |
| `mkdir <dossier>` | Crée un nouveau dossier | ✅ |
| `touch <fichier>` | Crée un fichier vide | ✅ |
| `mktemp -d` | Crée un dossier temporaire dans /tmp avec un nom aléatoire | ✅ |
| `cp <source> <dest>` | Copie un fichier d'un endroit à un autre | ✅ |
| `mv <ancien> <nouveau>` | Déplace ou renomme un fichier | ✅ |
| `xxd -r <in> <out>` | Reconvertit un hexdump en fichier binaire | ✅ |
| `gzip -d <fichier.gz>` | Décompresse un fichier gzip | ✅ |
| `bzip2 -d <fichier.bz2>` | Décompresse un fichier bzip2 | ✅ |
| `tar -xf <fichier.tar>` | Extrait le contenu d'une archive tar | ✅ |
| `nano <fichier>` | Éditeur de texte en terminal | ✅ |
| `nc <destination> <port>` | Envoie/reçoit des données sur le réseau via un port (Netcat) | ✅ |
| `nc -lp <port>` | Écoute sur un port TCP en mode serveur | ✅ |
| `echo "texte" \| nc -lp <port> &` | Lance nc en arrière-plan et envoie un message automatiquement | ✅ |
| `kill %<job>` | Tue un processus en arrière-plan par son numéro de job | ✅ |
| `<commande> &` | Lance un processus en arrière-plan | ✅ |
| `openssl s_client -connect <host>:<port> -quiet` | Connexion SSL/TLS silencieuse | ✅ |
| `nmap -p <plage> <host>` | Scanner de ports sur une plage donnée | ✅ |
| `diff <fichier1> <fichier2>` | Compare deux fichiers et affiche les lignes différentes | ✅ |
| `whoami` | Affiche l'utilisateur courant | ✅ |
| `./<binaire> <commande>` | Exécute une commande via un binaire setuid (droits empruntés) | ✅ |
| `cd /etc/cron.d/` | Navigue dans le dossier des tâches cron | ✅ |
| `cat /usr/bin/<script>.sh` | Lit le contenu d'un script shell | ✅ |
| `* * * * * user <cmd>` | Syntaxe cron : exécute une commande toutes les minutes | ✅ |
| `cmd > <fichier>` | Redirige la sortie d'une commande vers un fichier | ✅ |
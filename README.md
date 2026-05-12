# OverTheWire Bandit
Mon parcours d'apprentissage Linux et cybersécurité
à travers le wargame Bandit by OverTheWire.

## 📊 Progression

| Niveau | Writeup | Statut |
|--------|---------|--------|
| Level 00 | [📄 Voir](./lvl-00/README.md) | ✅ |
| Level 01 | [📄 Voir](./lvl-01/README.md) | ✅ |
| Level 02 | [📄 Voir](./lvl-02/README.md) | ✅ |
| Level 03 | [📄 Voir](./lvl-03/README.md) | ✅ |
| Level 04 | [📄 Voir](./lvl-04/README.md) | ✅ |
| Level 05 | [📄 Voir](./lvl-05/README.md) | ✅ |
| Level 06 | [📄 Voir](./lvl-06/README.md) | ✅ |
| Level 07 | [📄 Voir](./lvl-07/README.md) | ✅ |
| Level 08 | [📄 Voir](./lvl-08/README.md) | ✅ |
| Level 09 | [📄 Voir](./lvl-09/README.md) | ✅ |
| Level 10 | [📄 Voir](./lvl-10/README.md) | ✅ |
| Level 11 | [📄 Voir](./lvl-11/README.md) | ✅ |
| Level 12 | [📄 Voir](./lvl-12/README.md) | ✅ |
| Level 13 | [📄 Voir](./lvl-13/README.md) | ✅ |
| Level 14 | [📄 Voir](./lvl-14/README.md) | ✅ |
| Level 15 | [📄 Voir](./lvl-15/README.md) | ✅ |
| Level 16 | [📄 Voir](./lvl-16/README.md) | ✅ |
| Level 17 | — | ⏳ |

## 🔧 Commandes apprises

| Commande | Description | Maîtrisée |
|----------|-------------|-----------|
| `ssh user@host -p port` | Connexion distante sécurisée via SSH | ✅ |
| `ssh -i <clé> user@host -p port` | Connexion SSH avec une clé privée | ✅ |
| `chmod 600 <fichier>` | Restreint les permissions : lecture+écriture pour moi seul | ✅ |
| `nano <fichier>` | Éditeur de texte en terminal | ✅ |
| `cd -` | Retourne au répertoire précédent | ✅ |
| `pwd` | Affiche le répertoire courant | ✅ |
| `ls` | Liste les fichiers et dossiers | ✅ |
| `ls -a` | Liste tous les fichiers, y compris les cachés | ✅ |
| `ls -l` | Liste les fichiers avec les détails | ✅ |
| `cat <fichier>` | Affiche le contenu d'un fichier | ✅ |
| `cat ./<fichier>` | Lit un fichier dont le nom commence par `-` | ✅ |
| `cd <dossier>` | Navigue dans un dossier | ✅ |
| `cd ..` | Remonte d'un niveau dans l'arborescence | ✅ |
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
| `nc <destination> <port>` | Envoie/reçoit des données sur le réseau via un port (Netcat) | ✅ |
| `openssl s_client -connect <host>:<port>` | Se connecte à un service via une connexion chiffrée SSL/TLS | ✅ |
| `nmap -sV -p <plage> <cible>` | Scanne une plage de ports et détecte les services qui y tournent | ✅ |
| `openssl s_client -connect <host>:<port> -quiet` | Connexion SSL/TLS silencieuse, évite le problème KEYUPDATE | ✅ |
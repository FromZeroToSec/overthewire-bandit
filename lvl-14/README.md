# Bandit Level 14 

## 🎯 Objectif
Se connecter en bandit14 via une clé SSH (obtenue au niveau précédent), récupérer le mot de passe du niveau actuel stocké dans `/etc/bandit_pass/bandit14`, puis l'envoyer au port 30000 sur localhost pour recevoir le mot de passe du niveau suivant.

## 🧠 Raisonnement
Le niveau introduit la notion de communication réseau locale. Une fois connecté en bandit14, il faut d'abord lire le mot de passe du niveau actuel (accessible uniquement par bandit14), puis utiliser `nc` pour l'envoyer à un service qui écoute sur le port 30000 de la machine locale (localhost). Ce service vérifie le mot de passe et retourne le mot de passe du niveau suivant si c'est correct.

## 🔧 Commandes utilisées

| Commande | Syntaxe | Description |
|----------|---------|-------------|
| `ssh` | `ssh user@host -i <clé> -p <port>` | Connexion SSH avec une clé privée |
| `cat` | `cat /etc/bandit_pass/bandit14` | Lire le mot de passe du niveau actuel |
| `nc` | `nc <destination> <port>` | Envoyer/recevoir des données sur le réseau via un port |
| `ls` | `ls /etc/bandit_pass/` | Lister les fichiers de mots de passe disponibles |

## 💡 Difficultés rencontrées
- **Problème de copier-coller** : L'adresse SSH s'est transformée en lien markdown `[user@host](mailto:...)` ce qui causait des erreurs de parsing dans le terminal. Solution : retaper la commande manuellement.
- **Tiret long** : Un em dash `–` s'était substitué au tiret normal `-` dans la commande, causant l'erreur `zsh: number expected`.
- **Mauvais mot de passe envoyé** : Le premier essai avec `nc` utilisait le mot de passe de bandit13 au lieu de bandit14 → réponse "Wrong!". Il fallait d'abord lire `/etc/bandit_pass/bandit14`.

## 📚 Ce que j'ai appris
- **localhost** (`127.0.0.1`) = adresse qui désigne toujours la machine sur laquelle on est actuellement. Quand on est en SSH sur Bandit, localhost pointe vers le serveur Bandit, pas son propre PC.
- **Un port** = comme un numéro d'appartement dans un immeuble. L'IP = l'adresse de l'immeuble, le port = la porte précise à laquelle on frappe.
- **`nc` (Netcat)** = outil réseau qui permet d'envoyer et recevoir du texte via un port. Très utilisé en cybersécurité pour tester des connexions et interagir avec des services réseau.
- Les mots de passe Bandit sont toujours stockés dans `/etc/bandit_pass/banditXX` et lisibles uniquement par l'utilisateur correspondant.
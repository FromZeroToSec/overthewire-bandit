# Bandit Level 15 

## 🎯 Objectif

Envoyer le mot de passe du niveau actuel (bandit15) au port 30001 sur localhost, via une connexion chiffrée SSL/TLS, pour recevoir le mot de passe du niveau suivant.

## 🧠 Raisonnement

La logique est identique au level 14 : envoyer un mot de passe à un port local pour recevoir le suivant. La seule différence est que le port 30001 n'accepte que les connexions **chiffrées SSL/TLS** — `nc` ne suffit donc plus. Il faut utiliser `openssl s_client` qui est conçu pour établir ce type de connexion.

Étapes suivies :
1. Récupérer le mot de passe de bandit15 via `cat /etc/bandit_pass/bandit15`
2. Se connecter au port 30001 avec `openssl s_client -connect localhost:30001`
3. Attendre le `read R BLOCK` (le serveur est prêt)
4. Taper le mot de passe et appuyer sur Entrée
5. Recevoir `Correct!` et le mot de passe du niveau suivant

## 🔧 Commandes utilisées

| Commande | Syntaxe | Description |
|----------|---------|-------------|
| `cat` | `cat /etc/bandit_pass/bandit15` | Lire le mot de passe du niveau actuel |
| `openssl s_client` | `openssl s_client -connect localhost:30001` | Se connecter à un service via une connexion chiffrée SSL/TLS |

## 💡 Difficultés rencontrées

- Confusion entre le fichier `.bandit14.password` (mot de passe de bandit14) et le mot de passe de bandit15 — il fallait utiliser le bon mot de passe
- Le concept SSL/TLS était nouveau et abstrait au départ
- Beaucoup d'informations affichées lors de la connexion SSL (certificat, session TLS...) qui peuvent désorienter, mais il suffit d'attendre `read R BLOCK` pour savoir que le serveur attend notre saisie

## 📚 Ce que j'ai appris

- **SSL/TLS** = protocole de **chiffrement** des données sur le réseau — les données envoyées sont protégées, personne ne peut les lire en transit
- **`openssl s_client`** = la commande pour se connecter à un service SSL en ligne de commande (équivalent de `nc` mais avec chiffrement)
- La différence entre une connexion normale (`nc`) et une connexion chiffrée (`openssl s_client`) : même logique, outil différent
- SSL/TLS n'est pas lié à un port spécifique — c'est une configuration du serveur (ex: port 443 pour HTTPS, port 30001 ici)
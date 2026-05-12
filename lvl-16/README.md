# Bandit Level 16 

## 🎯 Objectif

Trouver quel port entre 31000 et 32000 sur localhost héberge un service SSL/TLS, puis lui envoyer le mot de passe actuel pour récupérer les credentials du niveau suivant (une clé RSA privée).

---

## 🧠 Raisonnement

Le niveau demande d'envoyer le mot de passe à un port spécifique sur localhost. Plusieurs ports sont ouverts dans la plage 31000-32000, mais il faut d'abord identifier lequel parle SSL.

J'ai utilisé `nmap` pour scanner tous les ports de la plage et détecter les services qui tournent sur chacun. Les résultats montraient plusieurs ports en `echo` (qui renvoient simplement ce qu'on leur envoie) et deux ports SSL :
- `31518` → `ssl/echo` : SSL mais renvoie ce qu'on envoie ❌
- `31790` → `ssl/unknown` : SSL avec un service inconnu ✅

Le port `31790` était le seul intrigant car son service était inconnu — c'est lui le vrai serveur. J'ai ensuite utilisé `openssl s_client` avec l'option `-quiet` pour envoyer le mot de passe via SSL et récupérer la clé RSA privée.

**Concept important découvert :** Les ports 31000-32000 ne sont accessibles que depuis `localhost` (l'intérieur du serveur), pas depuis l'extérieur. Le firewall bloque l'accès direct depuis internet. C'est pour ça qu'on doit d'abord se connecter en SSH puis scanner depuis l'intérieur.

---

## 🔧 Commandes utilisées

| Commande | Syntaxe | Explication |
|----------|---------|-------------|
| `nmap` | `nmap -sV -p 31000-32000 localhost` | Scanne les ports 31000 à 32000 sur localhost et détecte les services qui tournent sur chaque port ouvert |
| `man` | `man openssl-s_client` | Consulte la documentation de openssl s_client pour trouver les bonnes options |
| `openssl s_client` | `openssl s_client -connect localhost:31790 -quiet` | Se connecte à un service via SSL/TLS. `-quiet` désactive le mode interactif et évite le problème de KEYUPDATE |

### Options importantes

| Option | Commande | Rôle |
|--------|----------|------|
| `-sV` | `nmap` | Détecte le service/version sur chaque port ouvert |
| `-p 31000-32000` | `nmap` | Limite le scan à cette plage de ports |
| `-connect host:port` | `openssl s_client` | Spécifie la cible (format obligatoire : `host:port`) |
| `-quiet` | `openssl s_client` | Désactive le mode interactif, évite KEYUPDATE et affiche moins d'informations |

---

## 💡 Difficultés rencontrées

- **Lecture du man `nmap`** : Trouver les bonnes options `-sV` et `-p` dans la documentation.
- **Syntaxe de `openssl s_client`** : J'avais utilisé `-p 31790` séparément, mais l'option `-connect` requiert le format `host:port` directement.
- **KEYUPDATE** : En TLS 1.3, le serveur envoie un message de mise à jour des clés. Sans l'option `-quiet` (ou `-ign_eof`), `openssl` ferme la connexion avant de recevoir la réponse. L'option `-quiet` règle le problème.
- **Comprendre localhost vs ports externes** : Les ports 31000-32000 ne sont accessibles que depuis l'intérieur du serveur à cause du firewall. On ne peut pas les atteindre directement depuis son PC.

---

## 📚 Ce que j'ai appris

- **`nmap`** est un outil de scan réseau qui permet de découvrir les ports ouverts et les services qui y tournent.
- **`-sV`** ("Service Version") demande à nmap d'identifier quel service écoute sur chaque port.
- **Firewall / localhost** : certains ports sont uniquement accessibles depuis l'intérieur d'un serveur (localhost), pas depuis l'extérieur — c'est une bonne pratique de sécurité.
- **`echo`** dans les résultats nmap signifie que le service renvoie simplement ce qu'on lui envoie — c'est un piège.
- **KEYUPDATE** est un mécanisme TLS 1.3 de rotation des clés de chiffrement en cours de session. L'option `-quiet` (ou `-ign_eof`) de `openssl s_client` permet d'ignorer ce comportement.
- La réponse du bon port était une **clé RSA privée** et non un mot de passe classique — à utiliser pour le niveau suivant.
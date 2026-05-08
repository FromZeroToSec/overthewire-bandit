# Bandit Level 13

## 🎯 Objectif

Se connecter en tant que bandit14 sans mot de passe, en utilisant
une clé SSH privée (`sshkey.private`) trouvée dans le home directory
de bandit13.

## 🧠 Raisonnement

En se connectant en bandit13, on trouve deux fichiers : `HINT` et
`sshkey.private`. La clé SSH privée remplace le mot de passe pour
s'authentifier. On ne peut pas se connecter depuis le serveur bandit
lui-même (localhost bloqué), donc il faut récupérer la clé sur sa
machine locale et s'y connecter depuis là.

Étapes suivies :
1. Afficher la clé avec `cat sshkey.private` et la copier
2. Créer un fichier local avec `nano` et coller la clé (avec les lignes `-----BEGIN/END RSA PRIVATE KEY-----`)
3. Restreindre les permissions avec `chmod 600` (SSH refuse les clés lisibles par d'autres)
4. Se connecter avec `ssh -i` en précisant le chemin vers la clé

## 🔧 Commandes utilisées

| Commande | Syntaxe | Description |
|----------|---------|-------------|
| `ssh -i` | `ssh user@host -i <clé> -p <port>` | Connexion SSH avec une clé privée au lieu d'un mot de passe |
| `chmod` | `chmod 600 <fichier>` | Change les permissions : lecture+écriture pour moi seul, rien pour les autres |
| `nano` | `nano <fichier>` | Éditeur de texte en terminal pour créer/modifier un fichier |
| `cd -` | `cd -` | Retourne au répertoire précédent (comme un bouton retour) |

## 💡 Difficultés rencontrées

- Tentative de connexion SSH depuis le serveur bandit lui-même → bloqué (localhost interdit)
- Fichier de clé créé vide car `nano` avait été ouvert sur le dossier au lieu du fichier
- Clé copiée sans les lignes `-----BEGIN/END RSA PRIVATE KEY-----` → erreur libcrypto
- Permissions trop ouvertes (`0664`) → SSH refusait la clé avec `UNPROTECTED PRIVATE KEY FILE`
- Oubli du chemin complet vers le fichier dans la commande `-i`

## 📚 Ce que j'ai appris

Une **clé SSH privée** remplace le mot de passe pour s'authentifier.
Elle ne circule jamais sur le réseau — c'est plus sécurisé. SSH exige
que la clé privée ne soit accessible que par son propriétaire (`chmod 600`),
sinon il refuse de l'utiliser.

`chmod 600` signifie : moi seul je peux lire et écrire, les autres
n'ont aucun accès. Sur un serveur partagé avec plusieurs utilisateurs,
c'est essentiel pour protéger ses clés.
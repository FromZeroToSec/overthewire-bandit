# Bandit Level 06

## 🎯 Objectif

Trouver un fichier situé **somewhere on the server** (n'importe où sur le serveur) avec 3 propriétés précises :
- Owned by user **bandit7**
- Owned by group **bandit6**
- **33 bytes** de taille

## 🧠 Raisonnement

J'ai utilisé `find` depuis la racine `/` avec les 3 filtres combinés en une seule commande.
Le problème c'est que `find` retournait des dizaines de lignes "Permission denied" qui noyaient le vrai résultat.
J'ai compris que ces erreurs venaient du canal **stderr** (canal 2) et non de stdout (canal 1).
En redirigeant stderr vers `/dev/null`, j'ai pu voir uniquement le fichier trouvé.
J'avais aussi mis le mauvais groupe au départ (`bandit7` au lieu de `bandit6`), donc le fichier ne matchait pas.

## 🔧 Commandes utilisées

| Commande | Syntaxe | Description |
|----------|---------|-------------|
| `find` | `find / -user <u> -group <g> -size <n>c` | Cherche un fichier sur tout le serveur selon plusieurs critères |
| `2>/dev/null` | `commande 2>/dev/null` | Redirige les erreurs (stderr) vers la poubelle pour ne pas les afficher |
| `cat` | `cat /chemin/fichier` | Affiche le contenu d'un fichier |

## 💡 Difficultés rencontrées

- J'ai d'abord mis `-group bandit7` au lieu de `-group bandit6` → le fichier ne matchait pas les critères
- Le résultat était noyé dans des centaines de lignes "Permission denied"
- J'ai appris à distinguer **stdout** (résultats normaux) et **stderr** (erreurs) pour filtrer le bruit avec `2>/dev/null`

## 📚 Ce que j'ai appris

Linux a 3 canaux de communication pour les processus :
- **0** → stdin (entrée)
- **1** → stdout (sortie normale)
- **2** → stderr (erreurs)

`>` redirige stdout, `2>` redirige stderr. `/dev/null` est la "poubelle" du système : tout ce qu'on y envoie disparaît.
Combiner `find` avec `2>/dev/null` est une technique classique pour afficher uniquement les résultats sans le bruit des erreurs.
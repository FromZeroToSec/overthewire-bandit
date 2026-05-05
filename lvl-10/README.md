# Bandit Level 10

## 🎯 Objectif

Trouver le mot de passe dans `data.txt` qui contient
des données encodées en base64.

## 🧠 Raisonnement

`cat data.txt` affiche un texte lisible mais incompréhensible
avec des caractères A-Z, a-z, 0-9 et `==` à la fin —
signe typique du base64. Lu la doc de `base64 --help`
pour trouver l'option de décodage, puis une seule commande
a suffi.

## 🔧 Commandes utilisées

| Commande | Syntaxe | Description |
|----------|---------|-------------|
| `cat` | `cat <fichier>` | Affiche le contenu — lisible ici car texte encodé |
| `base64 -d` | `base64 -d <fichier>` | Décode un fichier encodé en base64 |

## 💡 Difficultés rencontrées

Aucun blocage — reconnaissance du pattern base64 grâce
à Wikipedia et la doc `--help` a donné directement
l'option `-d`.

## 📚 Ce que j'ai appris

Base64 est un système d'**encodage** (pas de chiffrement)
qui transforme des données en texte lisible pour les
transporter facilement. Contrairement au binaire du level 9,
le fichier est lisible avec `cat` mais son contenu reste
incompréhensible sans décodage. `base64 -d` inverse
l'opération et révèle les données originales.
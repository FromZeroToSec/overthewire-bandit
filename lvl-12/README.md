# Bandit Level 12

## 🎯 Objectif

Le fichier `data.txt` est un hexdump d'un fichier qui a été compressé plusieurs fois.
Il faut reconvertir le hexdump en binaire, puis décompresser couche par couche jusqu'à obtenir le mot de passe.

## 🧠 Raisonnement

Le fichier `data.txt` est un fichier texte (hexdump), pas directement un fichier compressé.
Avant de pouvoir décompresser quoi que ce soit, il faut d'abord le reconvertir en binaire avec `xxd -r`.

Ensuite, on répète le même processus en boucle :
1. `file <fichier>` → identifier le type de compression
2. `mv <fichier> <fichier>.<extension>` → renommer avec la bonne extension
3. Décompresser avec la bonne commande (`gzip -d`, `bzip2 -d`, ou `tar -xf`)
4. Recommencer jusqu'à tomber sur un fichier ASCII text contenant le mot de passe

On travaille dans un dossier temporaire `/tmp` car on n'a pas les droits de créer des fichiers dans le home directory.

## 🔧 Commandes utilisées

| Commande | Syntaxe | Explication |
|----------|---------|-------------|
| `mktemp -d` | `mktemp -d` | Crée un dossier temporaire dans `/tmp` avec un nom aléatoire |
| `cp` | `cp <source> <destination>` | Copie un fichier d'un endroit à un autre |
| `xxd -r` | `xxd -r <fichier_in> <fichier_out>` | Reconvertit un hexdump en fichier binaire (reverse) |
| `file` | `file <fichier>` | Identifie le type d'un fichier (gzip, bzip2, tar, ASCII...) |
| `mv` | `mv <ancien_nom> <nouveau_nom>` | Renomme (ou déplace) un fichier |
| `gzip -d` | `gzip -d <fichier.gz>` | Décompresse un fichier gzip |
| `bzip2 -d` | `bzip2 -d <fichier.bz2>` | Décompresse un fichier bzip2 |
| `tar -xf` | `tar -xf <fichier.tar>` | Extrait le contenu d'une archive tar |

## 💡 Difficultés rencontrées

- Ne pas confondre **compression** et **chiffrement** : ici on compresse, on ne chiffre pas
- Penser à renommer les fichiers avec la bonne extension avant de décompresser (gzip et bzip2 sont stricts là-dessus)
- `mv` sert aussi bien à déplacer qu'à renommer — dans le même dossier, c'est un renommage
- Il faut répéter le processus de nombreuses fois (poupées russes 🪆)

## 📚 Ce que j'ai appris

- Un **hexdump** est une représentation texte d'un fichier binaire — `file` voit du texte, pas le vrai contenu
- `xxd -r` permet de reconvertir un hexdump en fichier binaire original
- `gzip` et `bzip2` compriment **un seul fichier**, chacun avec sa propre extension et commande
- `tar` regroupe **plusieurs fichiers** en une archive, puis peut être compressé — il faut `-xf` pour extraire
- Travailler dans `/tmp` quand on a besoin de créer/modifier des fichiers sans droits dans le home
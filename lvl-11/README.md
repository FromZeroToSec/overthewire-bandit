# Bandit Level 11

## 🎯 Objectif

Trouver le mot de passe dans `data.txt` où toutes les lettres
minuscules (a-z) et majuscules (A-Z) ont été décalées de 13 positions
(chiffrement ROT13).

## 🧠 Raisonnement

ROT13 décale chaque lettre de 13 positions dans l'alphabet.
Comme l'alphabet a 26 lettres, 13 + 13 = 26 : encoder et décoder
c'est exactement la même opération.

La commande `tr` permet de substituer des caractères — parfaite
pour ROT13. Il faut lui passer deux chaînes : l'alphabet original
et l'alphabet décalé de 13. Comme `tr` lit depuis stdin, on utilise
un pipe avec `cat` pour lui passer le fichier.

- CHAINE1 : `A-Za-z` (alphabet complet, majuscules + minuscules)
- CHAINE2 : `N-ZA-Mn-za-m` (alphabet décalé de 13 pour chaque moitié)

## 🔧 Commandes utilisées

| Commande | Syntaxe | Description |
|----------|---------|-------------|
| `cat` | `cat <fichier>` | Affiche le contenu du fichier |
| `tr` | `tr 'CHAINE1' 'CHAINE2'` | Substitue les caractères de CHAINE1 par ceux de CHAINE2 |
| pipe `\|` | `cmd1 \| cmd2` | Passe l'output de cmd1 en input à cmd2 |
| combo | `cat data.txt \| tr 'A-Za-z' 'N-ZA-Mn-za-m'` | Décode le ROT13 du fichier |

## 💡 Difficultés rencontrées

- `tr` attend deux strings — sans le deuxième argument il retourne une erreur.
- `tr` lit depuis stdin par défaut : sans pipe il attend une saisie clavier (Ctrl+Z pour quitter).
- Comprendre comment écrire les deux moitiés de l'alphabet (`A-M` / `N-Z`) dans la bonne syntaxe.

## 📚 Ce que j'ai appris

ROT13 est un chiffrement par **substitution** : chaque lettre est
remplacée par celle 13 positions plus loin. Comme 13 × 2 = 26
(longueur de l'alphabet), encoder et décoder sont la même opération.

`tr` est une commande de **traduction de caractères** — elle remplace
chaque caractère d'un premier set par le caractère correspondant
dans un second set. Elle ne lit pas de fichier directement :
il faut lui passer les données via un pipe.
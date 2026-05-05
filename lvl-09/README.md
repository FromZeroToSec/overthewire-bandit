# Bandit Level 9

## 🎯 Objectif

Trouver le mot de passe stocké dans le fichier `data.txt`, un fichier
**binaire** illisible directement. Le mot de passe est l'une des rares
chaînes lisibles, précédée de plusieurs caractères `=`.

## 🧠 Raisonnement

`cat data.txt` affiche un chaos de symboles car c'est un fichier binaire,
pas fait pour être lu directement. Réflexe acquis au level 7 : d'abord `du`
pour vérifier la taille et éviter le défilement interminable. Ensuite
`strings` pour extraire les chaînes lisibles, puis `grep` via un pipe pour
filtrer uniquement les lignes contenant `=`.

## 🔧 Commandes utilisées

| Commande | Syntaxe | Description |
|----------|---------|-------------|
| `du` | `du <fichier>` | Vérifie la taille d'un fichier avant de l'ouvrir |
| `strings` | `strings <fichier>` | Extrait les chaînes lisibles d'un fichier binaire |
| `grep` | `grep "pattern"` | Recherche une chaîne précise dans un texte |
| `pipe` | `cmd1 \| cmd2` | Passe l'output d'une commande en input à la suivante |
| combo | `strings <fichier> \| grep "==="` | Filtre les strings lisibles contenant `=` |

## 💡 Difficultés rencontrées

Commande `strings` inconnue — lecture de la doc nécessaire. Première approche
en scrollant manuellement dans l'output, fonctionnel mais pas optimal.
Réflexe du pipe avec `grep` venu dans un second temps.

## 📚 Ce que j'ai appris

Un fichier **binaire** contient des données non lisibles directement par un
humain. `strings` + `grep` via un pipe est un combo puissant : `strings`
extrait les parties lisibles, `grep` cible exactement ce qu'on cherche.
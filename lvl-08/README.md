# Bandit Level 8

## 🎯 Objectif

Trouver le mot de passe dans le fichier `data.txt` qui contient des centaines de lignes.
Le mot de passe est la seule ligne qui n'apparaît qu'une seule fois dans le fichier.

---

## 🧠 Raisonnement

Avant d'ouvrir le fichier, j'ai d'abord vérifié sa taille avec `du` pour éviter de me faire
déborder par un fichier trop lourd (leçon apprise au niveau précédent).

En ouvrant avec `cat`, j'ai vu des centaines de lignes avec beaucoup de répétitions.
Impossible de trouver la ligne unique à la main.

J'ai essayé `uniq data.txt` directement mais ça n'a pas fonctionné comme attendu.
En lisant la documentation avec `uniq --help`, j'ai compris que `uniq` ne détecte
les doublons que si les lignes identiques sont **côte à côte**.
Il faut donc d'abord trier le fichier avec `sort` pour regrouper les lignes identiques,
puis passer le résultat à `uniq`.

J'ai utilisé le **pipe** `|` pour enchaîner les deux commandes en une seule opération.
Avec l'option `-u` trouvée dans la doc, `uniq` affiche uniquement les lignes qui
n'apparaissent qu'une seule fois.

---

## 🔧 Commandes utilisées

| Commande | Syntaxe | Description |
|----------|---------|-------------|
| `du` | `du data.txt` | Vérifie la taille d'un fichier avant de l'ouvrir |
| `cat` | `cat data.txt` | Affiche le contenu d'un fichier |
| `sort` | `sort data.txt` | Trie les lignes d'un fichier par ordre alphabétique |
| `uniq` | `uniq [option]` | Filtre les lignes consécutives identiques |
| `uniq -u` | `uniq -u` | Affiche uniquement les lignes qui n'apparaissent qu'une fois |
| `\|` (pipe) | `commande1 \| commande2` | Envoie le résultat de la 1ère commande vers la 2ème |
| `--help` | `uniq --help` | Affiche la documentation d'une commande |

**Commande finale :**
```bash
sort data.txt | uniq -u
```

---

## 💡 Difficultés rencontrées

- **`uniq` seul ne suffisait pas** : sans tri préalable, les doublons non-adjacents
  ne sont pas détectés. Il faut absolument `sort` avant.
- **Mauvais usage du pipe** : au début j'ai tapé `sort data.txt | uniq data.txt`,
  ce qui faisait ignorer le pipe car `uniq` relisait directement le fichier.
  Il ne faut pas passer de nom de fichier à `uniq` quand on utilise un pipe.
- **Option manquante** : `uniq` sans option supprime les doublons mais garde
  une occurrence de chaque. L'option `-u` est nécessaire pour n'afficher
  que les lignes vraiment uniques.

---

## 📚 Ce que j'ai appris

- Le **pipe `|`** est le concept clé de ce niveau : il permet de fusionner deux
  commandes en chaînant la sortie de l'une vers l'entrée de l'autre.
- `uniq` ne fonctionne que sur des lignes **adjacentes** → toujours `sort` avant.
- Lire la documentation avec `--help` permet de trouver soi-même les options
  sans chercher la réponse ailleurs.
- Vérifier la taille d'un fichier avec `du` avant de l'ouvrir est une bonne habitude.
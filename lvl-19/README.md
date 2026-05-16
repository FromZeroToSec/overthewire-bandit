# Bandit Level 19 → 20

## 🎯 Objectif

Trouver le mot de passe du niveau 20, protégé par des permissions restrictives, en utilisant un binaire spécial présent dans le home directory.

---

## 🧠 Raisonnement

En listant les fichiers du home, un binaire apparaît **surligné en rouge** dans le terminal — signe visuel que le fichier a des permissions spéciales. Faire un `cat` dessus retourne du contenu illisible (données binaires), donc on utilise `file` pour comprendre ce qu'on a affaire. Le binaire est exécutable, on l'exécute : il affiche un message qui invite à utiliser `whoami`, révélant qu'on tourne avec les droits d'un autre utilisateur. On comprend alors qu'il faut **chaîner l'exécution du binaire avec `cat`** sur le fichier password en une seule commande.

Le concept clé : le binaire possède le **bit setuid**. Il appartient à `bandit20`, donc quand on l'exécute, on emprunte temporairement les droits de `bandit20` — ce qui permet de lire son fichier password, normalement inaccessible depuis `bandit19`.

---

## 🔧 Commandes utilisées

| Commande | Syntaxe | Explication |
|---|---|---|
| `ls -la` | `ls -la` | Lister les fichiers avec permissions (repérer le binaire en rouge) |
| `file` | `file bandit20-do` | Identifier le type du fichier (binaire exécutable) |
| `whoami` | `whoami` | Vérifier l'identité de l'utilisateur courant |
| `./binaire commande` | `./bandit20-do cat /etc/bandit_pass/bandit20` | Exécuter le binaire setuid pour lire un fichier protégé |

---

## 💡 Difficultés rencontrées

- `cat` sur le binaire retourne du contenu illisible → normal, les binaires ne sont pas faits pour être lus comme du texte
- Ne pas comprendre immédiatement pourquoi le binaire fonctionnait là où `cat` seul échouerait → c'est le bit setuid qui délègue temporairement les droits du propriétaire

---

## 📚 Ce que j'ai appris

- Le **bit setuid** (`rws` dans les permissions) permet d'exécuter un fichier avec les droits de son **propriétaire**, pas de celui qui l'exécute
- Les fichiers avec permissions spéciales apparaissent en **rouge** dans le terminal
- On ne peut pas lire un binaire avec `cat` — utiliser `file` pour identifier le type avant tout
- On peut **chaîner** une commande après un binaire setuid pour l'exécuter avec les droits empruntés
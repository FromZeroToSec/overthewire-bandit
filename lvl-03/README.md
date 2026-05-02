# Bandit Level 3

## 🎯 Objectif
Trouver le mot de passe stocké dans un fichier caché dans le dossier `inhere`.

## 🧠 Raisonnement
En arrivant sur le serveur, j'ai fait `ls` pour voir ce qu'il y avait. J'ai vu un dossier `inhere` — je savais que c'était un dossier car il était affiché en bleu dans le terminal. J'ai cherché sur internet pourquoi la couleur bleue, et j'ai compris que c'est la convention Linux pour indiquer les dossiers. Du coup j'ai fait `cd inhere` pour y entrer. Une fois dedans, `ls` ne montrait rien. J'ai cherché sur la documentation Linux comment afficher les fichiers cachés et j'ai trouvé `ls -a`. Avec cette commande j'ai trouvé le fichier `...Hiding-From-You`. Pour le lire, j'ai utilisé `cat` avec `./` devant le nom du fichier, une technique apprise au niveau précédent.

## 🔧 Commandes utilisées

| Commande | Syntaxe | Description |
|----------|---------|-------------|
| `ls` | `ls` | Liste les fichiers et dossiers visibles dans le répertoire courant |
| `cd` | `cd <dossier>` | Entre dans un dossier |
| `ls -a` | `ls -a` | Liste tous les fichiers, y compris les fichiers cachés (ceux qui commencent par `.`) |
| `cat` | `cat ./<fichier>` | Affiche le contenu d'un fichier — `./` précise que c'est un fichier dans le dossier courant |

## 💡 Difficultés rencontrées
Le `ls` simple ne montrait rien dans le dossier `inhere`. Il a fallu chercher comment afficher les fichiers cachés sous Linux et découvrir l'option `-a`. De plus, le fichier commençait par des points, donc j'ai utilisé `./` devant le nom pour éviter tout problème, comme appris au niveau précédent.

## 📚 Ce que j'ai appris
Sous Linux, les fichiers cachés commencent par un `.` et ne s'affichent pas avec un `ls` simple. Il faut utiliser `ls -a` pour les voir. La couleur bleue dans le terminal indique qu'un élément est un dossier.
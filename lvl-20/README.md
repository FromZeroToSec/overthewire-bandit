# Bandit Level 19 → Level 20

## 🎯 Objectif
Utiliser le binaire setuid `suconnect` qui se connecte à un port 
localhost via TCP. S'il reçoit le bon mot de passe, il renvoie 
le mot de passe du niveau suivant.

## 🧠 Raisonnement
`suconnect` est un client TCP qui attend de recevoir un mot de 
passe depuis un serveur. Il fallait donc créer ce serveur 
nous-mêmes avec `nc` (netcat) qui écoute sur un port choisi 
et envoie automatiquement le mot de passe de bandit20.

Comme il faut lancer deux processus en même temps, on utilise 
`&` pour mettre `nc` en arrière-plan et libérer le terminal 
pour lancer `./suconnect`.

## 🔧 Commandes utilisées

| Commande | Description |
|----------|-------------|
| `./suconnect` | Exécute le binaire sans arguments pour voir son usage |
| `echo "mdp" \| nc -lp <port> &` | Lance nc en écoute sur un port, envoie le mdp automatiquement, en arrière-plan |
| `./suconnect <port>` | Connecte le binaire au port, vérifie le mdp et renvoie le suivant |
| `kill %1 %2 ...` | Tue les jobs en arrière-plan |
| `&` | Lance un processus en arrière-plan |

## 💡 Difficultés rencontrées
- Comprendre qu'il fallait créer un serveur avec `nc` avant 
  de lancer `suconnect`
- Utiliser `&` pour lancer `nc` en arrière-plan
- Utiliser `echo` avec un pipe pour envoyer automatiquement 
  le mdp à `nc`

## 📚 Ce que j'ai appris
- `nc -lp <port>` permet d'écouter sur un port TCP
- Le `&` permet de lancer un processus en arrière-plan
- Le pipe `|` envoie la sortie d'une commande vers une autre
- Un binaire qui se connecte à un port nécessite un serveur 
  qui écoute de l'autre côté
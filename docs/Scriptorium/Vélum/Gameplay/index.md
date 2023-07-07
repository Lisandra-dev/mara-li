---
date: 2023-06-24
category: Scriptorium/Vélum/Gameplay
icon: font-awesome-solid/Dice
share: true
description: Gameplay de Vélum. Tous les crédits vont à Horvot, merci à lui pour son aide !
---
Le jeu se fait au **D20**.

Le dé naturel 1 est un échec critique, le dé naturel 20 est une réussite critique.

# Statistiques

Il y a six statistiques :
- <u>Force</u> : Physique
- <u>Constitution</u> : Résistance physique, à l'effort, endurance
- <u>Agilité</u> : Discrétion, souplesse, légèreté, esquive
- <u>Psychologie</u> : Capacité à mentir, résistance mentale, à la peur, folie…
- <u>Intelligence</u> : Compréhension du monde, connaissance
- <u>Perception</u> : Intuition, instinct, capacité à voir ce qui est caché

Il y a **70** points à répartir, pour une moyenne dans chaque statistiques à **10**. Les jets se déroulent comme suit :
- Si une statistique est supérieure à 11, la statistiques agit comme un **bonus**
- Si une statistique est inférieure à 11 : La statistique agit comme un **malus**

La valeur bonus ou malus se récupère par la différence avec 11 divisé par 2 (techniquement, `(statistique - 11)/2`, arrondi au supérieur pour les chiffres pairs :
- `12` : Bonus de `+1`
- `8` : Malus de `-2`

Vous ne pouvez avoir que 20 en maximum d'une caractéristique, et 1 en minimum.
Enfin, les personnages ont droit à **50 PV**.

En fonction des malus de vos statistiques, il est possible que vos jets deviennent négatifs. Un jet négatif n'est qu'un échec "normal", mais libre à vous de l'interpréter comme vous le souhaitez.
## Jets neutres

Pour réussir un jet, le joueur a besoin de connaître la difficulté, chaque difficulté possède des paliers qui doivent être dépasser pour réussir l'action :

| Tâche      | DD  |
| ---------- | --- |
| Trivial    | 6   |
| Facile     | 8   |
| Moyen      | 10  |
| Difficile  | 13  |
| Épique     | 16  |
| Impossible | 20  |

## Pouvoirs

Les pouvoirs doivent se raccorder à une statistique qui reste au choix du joueur. Quelque exemple de pouvoir et de caractéristiques :
- Change-forme : Psychologie
- Invocation : Intelligence
- Téléportation : Agilité

# Compétence

Les compétences sont des actions spéciales qui ont besoin de **Points de Compétence (PC)** pour être lancé. Un joueur a droit à 1O PC.

Les PC sont à répartir sur 4 compétences, selon la puissance de celle-ci. Les PC sont dépensés que l'attaque touche ou non, et les PC ne se rechargent pas au court d'un combat.

Il existe, en terme de compétences possibles :
- Les *Attaques spéciales*, qui auront un boost des dégâts bruts,
- Les *Bonus*, qui donneront un bonus sur les dés, de PV, régénération…
- Les *Malus*, donnant des malus sur les dés de la/les personnes ciblées, effet de statut…

> [!info] Bonus et Malus ne s'appliquent pas sur les jets de dégâts, mais le jet d'opposition, ou de lancement de la compétence.

> [!warning] Seules les attaques spéciales et leur dégâts bruts s'appliquent sur le calcul final du jet de dés

En plus de cela, vous avez droit à une compétence passive. **Vous avez donc droit à 5 compétences dont 1 passif**.

> [!warning] Les bonus donnés par une compétence ne peuvent dépasser +5

# Combat

Les combats se déroule en tour par tour avec des jets d'opposition. Si l'attaquant ou la défense l'emporte, le joueur qui remporte la joute lance `1d8±statistiques`.
L'ordre des tours est décidé par un jet d'**agilité**. Ceux ayant les jets les plus haut commencent (en cas d'égalité, c'est celui ayant la plus haute statistique).

Un coup critique est déterminé sur un test qui surpasse son homologue de **15**. Le joueur infligeant le coup-critique infligera `(1D8)*2*±statistique`.

- La défense face à une attaque **physique** peut se faire par **constitution** ou **agilité**
- La défense face à une attaque **mentale** se fait par un jet de **psychologie**
- Dans le cas du mensonge :
	- Dire un mensonge se fait un jet de **psychologie**
	- Découvrir un mensonge se fait sur un jet d'**Intelligence**
- Dans le cas des illusions :
	- En faire : **Psychologie**
	- Les découvrir : **Perception**

De plus, dans le cas où les deux jets d'opposition sont à égalités *(par exemple, les deux joueurs font 12)*, c'est celui avec la statistique la plus élevée qui gagne.

> [!note] Si le jet de dégât est _négatif_ le résultat passe à 0. Libre au joueur de l'interpréter comme il le souhaite.
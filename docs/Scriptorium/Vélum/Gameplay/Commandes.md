---
share: true
category: Scriptorium/Vélum/Gameplay
description: Aide pour les commandes du bots
---
Le serveur s'appuie sur des commandes [du bot Vélum](https://github.com/Lisandra-dev/Velum-bot) pour lancer les jets de dés. 

Il est aussi possible d'utiliser les [slash-commands](https://support.discord.com/hc/fr/articles/1500000368501-Slash-Commands-FAQ) pour lancer les dés. 

# Jets neutres : `$r` (ou `/act`)

La commande a plusieurs syntaxes. Chaque argument de la commande peut être mis dans le désordre, sauf pour la statistique, qui doit être en premier.

> [!faq] **L'aide peut être affiché à l'aide de la commande : `$r --help`**

## Recherche de statistiques

Lorsque votre personnage est validée, vos statistiques sont enregistrés et ainsi, les bonus et malus sont calculés automatiquement. Lorsque vous jetez un dé, vous devez chercher la statistique à l'aide de son nom.

La statistique à rechercher peut être écrite en abrégée ou en entière. Les caractères accentués sont remplacés par leur équivalent sans accent. Par exemple, `agi` pour agilité et `PSY` pour psychologie.

## Caractère spéciaux

- `&` : Indique l'alias de votre personnage. Utilisable uniquement si vous avez un DC ou des PNJ avec une fiche. Équivalent à `alias` dans la commande slash.
- `#` : Ajoute un commentaire
- `>` ou `<` : Change le seuil de réussite (voir [[./index#Jets neutres|Gameplay > Jets neutres]]). Vous pouvez indiquer une valeur absolue (comme `10`) pour fixer une réussite manuelle.
- `+` : Ajoute un bonus
- `-` : Ajoute un malus

### Le commentaire `#`

Le caractère `#` permet d'ajouter un commentaire à la commande. Il doit être **accolé** au commentaire. Il est facultatif dans le cas où le commentaire est après la statistique ou s'il est à la fin de la commande.

## Exemples

- `$r force #test`
- `$r endu >Trivial &Personnage #FIGHTO`

# Attaque (`1D8`) : `$atq` (ou `/atq`)

Fonctionne comme la commande précédente, à la différence qu'il n'est pas possible d'indiquer un seuil. Cela est remplacé par "CC", pour indiquer un coup-critique, qui doublera les dégâts.

De fait, les caractères spéciaux utilisables sont les suivants :
- `&` : Indique votre personnage secondaire/PNJ (cf `alias`)
- `#` : Ajoute un commentaire
- `+` : Ajoute un bonus
- `-` : Ajoute un malus
- `CC` (ou `cc`): Indique un coup critique

# Autres commandes :

- __Voir ses statistiques__ : Utiliser les slash commandes de [Vélum](https://github.com/Lisandra-dev/Velum-bot) avec la commande `/get`. 
	- N'utiliser `alias` que si vous avez besoin de voir les stats d'un personnage secondaire ou d'un PNJ.
- Ouvrir un ticket : `/ticket open ` (avec [Vélum](https://github.com/Lisandra-dev/Velum-bot))
- Afficher la météo : `!meteo`
- Indiquer son arrivée dans un endroit : `!arrive (nom du perso)`
- Indiquer son départ : `!depart (nom du perso)`
- Calculer des bonus : `/stat` avec @[Vélum](https://github.com/Lisandra-dev/Velum-bot)

## Note à propos de l'affichage

Plutôt que d'utiliser le nom complet de la statistique, une image est utilisée dans l'embed.
Chaque image correspond à une statistique. Ainsi :
- __Force__: ![24](https://github.com/Lisandra-dev/Velum-bot/blob/master/images/force.png?raw=true)
- __Constitution__ : ![24](https://github.com/Lisandra-dev/Velum-bot/blob/master/images/constitution.png?raw=true)
- __Agilité__ : ![24](https://github.com/Lisandra-dev/Velum-bot/blob/master/images/agilite.png?raw=true)
- __Intelligence__ : ![24](https://github.com/Lisandra-dev/Velum-bot/blob/master/images/intelligence.png?raw=true)
- __Psychologie__ : ![24](https://github.com/Lisandra-dev/Velum-bot/blob/master/images/psychologie.png?raw=true)
- __Perception__ : ![24](https://github.com/Lisandra-dev/Velum-bot/blob/master/images/perception.png?raw=true)
- __Neutre__ : 😐 (dans le cas où aucune statistique est utilisée)



---
share: true
title: "Eldale Creek — Dice"
---

J'espère sincèrement que c'est pas trop l'enfer à relire QQ

DONC !

Voici ma petite fonction qui est à intégrer à YAGPDB (ici : https://learn.yagpdb.xyz/the-custom-command-interface pour pouvoir la mettre)
Petit screen de comment elle doit être intégré : ![[../assets/img/Temporaire-11-12-2022.png|Temporaire-11-12-2022.png]]
2 notes : 
- Vous pouvez changer le trigger (c'est la commande à lancer !)
- Vous pouvez changer la façon dont on le lance. Sur mon serveur de test c'est `-r` par exemple.

Il y a plusieurs façon de l'utiliser : 
- `-r`, sans rien, qui va lancer un simple d20
- `-r #commentaire` qui va lancer un dé 20 avec un commentaire
- `-r <statistique> #<commentaire>` qui va lancer un dé 20, rajouter la statistiques et mettre un commentaire
- `-r <stats> <nom de la stats>` pareil que précédemment mais sans commentaire
- `-r <statistique> <nom de la statistique> <commentaire>`

Quelques exemples :
![[../assets/img/Temporaire-11-12-2022-1.png|Temporaire-11-12-2022-1.png]]
![[../assets/img/Temporaire-11-12-2022-2.png|Temporaire-11-12-2022-2.png]]
![[../assets/img/Temporaire-12-12-2022.png|Temporaire-12-12-2022.png]]
![[../assets/img/Temporaire-11-12-2022-4.png|Temporaire-11-12-2022-4.png]]
![[../assets/img/Temporaire-11-12-2022-5.png|Temporaire-11-12-2022-5.png]]

Note, dans le cas où la statistique a plusieurs valeurs et qu'on ne veut pas mettre de commentaire, il suffit d'encadrer la statistique avec `""` 
![[../assets/img/Temporaire-12-12-2022-1.png|Temporaire-12-12-2022-1.png]]

Et pareil si l'on souhaite tout indiquer : 
![[../assets/img/Temporaire-12-12-2022-2.png|Temporaire-12-12-2022-2.png]]

Le code : 
```go
{{$args := ""}}
{{$stats := 0}}

{{try}}
	{{$args = parseArgs 0 "" 
		(carg "string" "statistique")
		(carg "string" "nom de la statistique ou #commentaire (Optionnel)")
		(carg "string" "commentaire (Optionnel)")}}
	{{$stats := or ($args.Get 0) ""}}
{{catch}}
	{{$args = parseArgs 0 "" 
		(carg "int" "statistique")
		(carg "string" "nom de la statistique ou #commentaire (Optionnel)")
		(carg "string" "commentaire (Optionnel)")}}
		{{$stats := or ($args.Get 0) 0}}
{{end}}

{{$statistiqueArgs := or ($args.Get 1) ""}}
{{$commentaire := or ($args.Get 2) ""}}
{{$comments := $commentaire}}
{{$statistique := $statistiqueArgs}}

{{if (reFind "^#" (toString $stats))}} {{/* -r #commentaire */}}
	{{$comments = reReplace "^#" (toString $stats) ""}}
	{{$stats = 0}}
	{{if ne $statistiqueArgs "" }}
		{{$comments = joinStr "" $comments " " $statistiqueArgs}}
		{{$statistique = ""}}
	{{end}}
	{{if ne $commentaire "" }}
		{{$comments = joinStr "" $comments " " $commentaire}}
		{{$statistique = ""}}
	{{end}}
	{{$comments = joinStr "" "\t*" $comments "*\n"}}
{{else if (reFind "^#" $statistiqueArgs)}} {{/* -r <int> #comments */}}
	{{$statistique = ""}}
	{{$comments = reReplace "^#" ($args.Get 1) ""}}
	{{if ne $commentaire ""}}
		{{$comments = joinStr "" $comments " " $commentaire}}
	{{end}}
	{{$comments = joinStr "" "\n\t*" $comments "*\n"}}
{{else}}
	{{if ne $commentaire ""}}
		{{$comments = joinStr "" "\t*" $comments "*\n"}}
	{{end}}
	{{if ne $statistiqueArgs ""}}
		{{$statistique = joinStr "" " [__" $statistiqueArgs "__]\n" }}
	{{end}}
{{end}}

{{$dice := randInt 1 21 }}
{{$msg := (joinStr "" $comments "```md\n# " $dice "\n Détails : (dé naturel)\n```")}}

{{ if eq $dice 1}}
	{{$msg = joinStr "" "**Échec critique**" $statistique $msg }}
	{{sendMessageNoEscape nil (complexMessage "content" $msg "reply" .Message.ID)}}
{{ else if eq $dice 20 }}
	{{$msg = joinStr "" "**Réussite critique**" $statistique $msg }}
	{{sendMessageNoEscape nil (complexMessage "content" $msg "reply" .Message.ID)}}
{{else}}
	{{$added := add $dice $stats }}
	{{$msg := (joinStr ""  $comments "```md\n# " $added "\nDétails (1d20) : [" $dice " + " $stats "]\n```")}}
	{{if lt $added 20 }}
		{{$msg = joinStr "" "**Échec**" $statistique $msg }}
		{{sendMessageNoEscape nil (complexMessage "content" $msg "reply" .Message.ID)}}
	{{else}}
		{{$msg = joinStr "" "**Réussite**" $statistique $msg }}
		{{sendMessageNoEscape nil (complexMessage "content" $msg "reply" .Message.ID)}}
	{{end}}
{{end}}
```

Oui, il est très long, mais je vais expliquer en détail ce qu'il fait pour pas que vous ayez peur de l'implémenter !

On va le découper en deux parties : 
1. La lecture des arguments 
2. Le lancé de dés en lui même

# La lecture des arguments
Le `{{try}} … {{catch}} … {{end}}` permet de récupérer les informations qui sont passés avec la fonction, qui est d'un minimum de 0 arguments, donc `-r` seul, dans mon exemple.
Il permet surtout de vérifier si le premier argument est un nombre (`int`) ou une chaine de caractère (`string`)

Ensuite, on récupère les arguments en eux même : 
- `stats` : Le premier argument, qui peut être un commentaire (`#commentaire`) ou la valeur de la statistique que l'on veut utiliser. 
- `statistiqueArgs` : Le deuxième argument, qui peut être le nom de la statistique ou un commentaire. Par défaut, en son absence, on dit qu'il est vide.
- `commentaire` : Le troisième argument sera toujours le commentaire, et sera donc mis par défaut à une chaine vide.

Pour des raisons de praticité, je double ses valeurs avec `comments` et `statistique`

Ensuite, ça fait comme suit : 
![[../assets/img/schéma fonction discord.jpg|schéma fonction discord.jpg]]

# Le lancé de dé 

![[Untitled(1).jpg]]
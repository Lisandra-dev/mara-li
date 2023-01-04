---
share: true
category: hidden
---

# Images
## Special position & format
- `+side`
- `+rside`
- `+center`
- `+tape`
- `+pin`
- `+portrait`
- `+landscape`
- `+banner`
- `+hr`
- `+right`
- `+block`
## Modifier flag
- `-left`
- `-right`
- `-fix`
- `-abs`
## Size
- `-thumb`
- `-sm`
- `-med`
- `-lg`
- `-huge`
- `-cwdith`

## Border
- `-border1` (solid black 3px) & `-border2` (solid white 3px)
- `-bradius1` : 5px
- `-bradius2` : 20px
- `-bradiustl` : top right 20px
- `-bradiusbr` : bottom right 20px
- `-bradiustr` : top right
- `-bradiusbl` : bottom left 20px
- `-bthick` : border width 5px
- `-bthin` : border width 1px

## Shadow
- `-shadow1` : darkgrey 2px
- `-glow` : darkgrey 20px
- `-nofloat` : inline block + float none


# Embed Adjustments
| Attribute  | Description                              |
| ---------- | ---------------------------------------- |
| `nlk`      | Hide the link until hovered over embed   |
| `lk-l`     | Move link to the left                    |
| `lk-clear` | Make background of the link transparent  |
| `nmg`      | Will remove margins and padding          |
| `full`     | Display the full embed                   |
| `clean`    | Removes borders/etc to hide embed design |

## Heading & Titles

| Attribute                         | Description                              |
| --------------------------------- | ---------------------------------------- |
| `nlk`     | Hide the link until hovered over embed   |
| `lk-l `  | Move link to the left                    |
| `lk-clear` | Make background of the link transparent  |
| `nmg`      | Will remove margins and padding          |
| `full`     | Display the full embed                   |
| `clean`    | Removes borders/etc to hide embed design |
| `no-h5`    | Hide all header 5s in the embedded page |
| `no-h6`    | Hide all header 6s in the embedded page |

# Custom syntax
- `**~~text~~**` : **~~text~~**
- `*~~text~~*` : *~~text~~*
- `**==text==**` : **==text==**
- `*==text==*` : *==text==*
- `**==~~text~~==**` : **==~~text~~==**
- `__*text*__` : __*text*__
- `*==~~text~~==*`: *==~~text~~==*

# Dataview snippet

1. Embed all image in a folder
```js
dv.list(app.vault.getFiles().filter(file => file.extension === "png" || file.extension === "jpg").filter(file => file.path.includes("**FOLDER HERE FDP**")).map(file => dv.fileLink(file.path) ));
```
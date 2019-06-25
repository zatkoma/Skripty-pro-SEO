
## Změnit všechny odkazy na obsah hrefu

```JavaScript
var anchors = document.getElementsByTagName("a");

for (var i = 0; i < anchors.length; i++) {
    anchors[i].innerHTML = anchors[i].href
}
```

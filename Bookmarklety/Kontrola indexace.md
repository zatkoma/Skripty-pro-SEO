# Kontrola indexace

Jednoduše si to vezme vaši URL adresu a pošle ji to do Google nebo Seznamu, záleží jak si to vyberete. :)

## Google:
```JavaScript
javascript:if(/https?:\/\/.+/.test(window.location.href)){window.open('https://www.google.com/search?q=inurl:' + encodeURIComponent(window.location.href), '_blank')}
```
## Seznam:
```JavaScript
javascript:if(/https?:\/\/.+/.test(window.location.href)){window.open('https://search.seznam.cz/?q=info:' + encodeURIComponent(window.location.href), '_blank')}
```

## Credits:

Tyto bookmarklety vytvořili kluci v Collabimu. :)

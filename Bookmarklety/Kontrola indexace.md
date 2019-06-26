# Kontrola indexace

Jednoduše si to vezme vaši URL adresu a pošle ji to do Google nebo Seznamu, záleží jak si to vyberete. :)

## Google:
```JavaScript
javascript:if(/https%3F:%5C/%5C/.%2B/.test(window.location.href))%7Bwindow.open(%27https://www.google.com/search%3Fq%3Dinurl:%27 %2B encodeURIComponent(window.location.href), %27_blank%27)%7D
```
## Seznam:
```JavaScript
javascript:if(/https%3F:%5C/%5C/.%2B/.test(window.location.href))%7Bwindow.open(%27https://search.seznam.cz/%3Fq%3Dinfo:%27 %2B encodeURIComponent(window.location.href), %27_blank%27)%7D
```

## Credits:

Tyto bookmarklety vytvořili kluci v Collabimu. :)

# Kontrola Site:

Jednoduše si vezme vaši doménu a nahodí ji to do vyhledávačů. Na vás už je doplnit pouze dotaz. :)

## v Google:
```JavaScript
javascript:if(/https%3F:%5C/%5C/.%2B/.test(window.location.href))%7Bwindow.open(%27https://www.google.com/search%3Fq%3Dsite:%27 %2B encodeURIComponent(window.location.hostname), %27_blank%27)%7D
```

## v Seznamu:
```JavaScript
javascript:if(/https%3F:%5C/%5C/.%2B/.test(window.location.href))%7Bwindow.open(%27https://search.seznam.cz/%3Fq%3Dsite:%27 %2B encodeURIComponent(window.location.hostname), %27_blank%27)%7D
```

# Zjistění majitele domény

Chcete-li zjistit rychle majitele domény, tak následující bookmarklety jsou pro jednotlivé .TLD úrovně. :)

## .cz

```JavaScript
javascript:if(/https%3F:%5C/%5C/.%2B/.test(window.location.href))%7Bwindow.open(%27https://www.nic.cz/whois/domain/%27 %2B encodeURIComponent(window.location.hostname.replace('www.','')), %27_blank%27)%7D
```

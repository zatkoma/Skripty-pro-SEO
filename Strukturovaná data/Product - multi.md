# Strukturovaná data Produkt - Multi

Máte-li na vašem webu víc variant jednoho produktu, který má různé ceny, tak doporučuji implementovat následující strukturovaná data a to Product - Multi

```JavaScript
<script type="application/ld+json">
{
  "@context": "https://schema.org/",
  "@type": "Product",
  "name": "Název produktu",
  "image": [
    "https://example.com/photos/1x1/photo.jpg",
    "https://example.com/photos/4x3/photo.jpg",
    "https://example.com/photos/16x9/photo.jpg"
   ],
  "brand": {
    "@type": "Thing",
    "name": "ACME"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.4",
    "ratingCount": "89"
  },
  "offers": {
    "@type": "AggregateOffer",
    "lowPrice": "119.99",
    "highPrice": "199.99",
    "priceCurrency": "CZK"
  }
}
</script>
```

# Strukturovaná data pro FAQ

Jestliže chcete implementovat strukturovaná data pro FAQ (dotazy), tak nasaďte následující JSON-LD. Pozor, při implementaci bude nutné změnit jednotlivé otázky a odpověďi. Pozor implementace je na vlastní nebezpečí, údajně zlepší imprese a zhorší míru proklikovosti.

```JSON
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [{
    "@type": "Question",
    "name": "Dobře položená otázka 1?",
    "acceptedAnswer": {
      "@type": "Answer",
      "text": "Vyčeprávající odpověď"
    }
  }, {
    "@type": "Question",
    "name": "Dobře položená otázka 2?",
    "acceptedAnswer": {
      "@type": "Answer",
      "text": "Vyčeprávající odpověď"
    }
  }, {
    "@type": "Question",
    "name": "Dobře položená otázka 3?",
    "acceptedAnswer": {
      "@type": "Answer",
      "text": "Vyčeprávající odpověď"
    }
  }, {
    "@type": "Question",
    "name": "Dobře položená otázka 3?",
    "acceptedAnswer": {
      "@type": "Answer",
      "text": "Vyčeprávající odpověď"
    }
  }]
}
</script>
```

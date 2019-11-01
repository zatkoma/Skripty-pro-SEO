# Stahování dat z Google Search Console

Každý občas potřebuje stáhnout nějaké data ze Search Console. Můžete vyžít jejich rozhraní, ale získáte pouze 1000 URL případně můžete využít extraktory z Marketing Mineru, které jsou však také občas omezené. Proto jsem tu pro vás připravil jednoduchý skript pro stažení dat v Rku do RStudia:

```R

library(googleAuthR)
library(searchConsoleR)

scr_auth()

sc_params_from <- "2019-01-01"
sc_params_to <- "2019-06-25"
sc_params_property <- "domena.cz"
sc_row_limit <- 100000

## Stažení stránek:
sc_page <- search_analytics(sc_params_property, 
  sc_params_from, 
  sc_params_to, 
  dimensions = c("page"), 
  searchType = "web", 
  rowLimit = sc_row_limit)
  
## Případně bez proměnných:
sc_page <- search_analytics("https://www.domena.cz, 
  "2019-09-01", 
  "2019-10-31", 
  dimensions = c("page"), 
  searchType = "web", 
  rowLimit = 100000)


## Stažení stránek + dotazů:
sc_pagequery <- search_analytics(sc_params_property, 
  sc_params_from, 
  sc_params_to, 
  dimensions = c("page", "query"), 
  searchType = "web", 
  rowLimit = sc_row_limit)
  
  

## Smazání brandových dotazů
sc_pagequery_non_brand <- sc_pagequery %>%
  filter(!str_detect(query, 'martin|žatkovič|martin žatkovič|martin zatkovic'))
  
```

# Vliv filtru země na výsledky, které vidíte v GSC

Možná jste již slyšeli o tom, že je dobré využívat filtraci v GSC. Jestli vám však vrtalo hlavou proč, tak si zkuste projet následující skript, který vám ukáže jak moc je výsledek rozdílný, když se rozhodnete stáhnout data z GSC s filtrem na zemi a bez filtru.


## Nemáte-li k dispozici knihovny:
```R
install.packages("searchConsoleR")
install.packages("googleAuthR")
```

## Data pro stránky:

```R
## Nastavení kódování
Sys.setlocale("LC_CTYPE", "en_US.UTF-8")

## Potřební knihovny
library(searchConsoleR)
library(googleAuthR)

## Přihlášení se do Search Console
scr_auth()

## Zobrazení všech webů
list_websites()

##############################  Nastavení hodnot ###############################
## Výběr datumu:
sc_params_from  <- as.character(Sys.Date() - 93)
sc_params_to    <- as.character(Sys.Date() - 3)
#sc_params_form <- "2019-07-31"
#sc_params_to   <- "2019-05-01"

## Výběr domény:
sc_params_property <- "https://www.zatkovic.cz/"

## Maximální počet dotazů:
sc_row_limit <- 100000


############## Demonstrace rozdílnosti dat s filrem na zemi a bez ############## 

## Stažení bez omezení na zemi:
sc_page <- search_analytics(
  sc_params_property, 
  sc_params_from, 
  sc_params_to, 
  dimensions = c("page"), 
  searchType = "web", 
  rowLimit = sc_row_limit)

## Stažení s omezením na Českou Republiku
sc_page_cze <- search_analytics(
  sc_params_property, 
  sc_params_from, 
  sc_params_to, 
  dimensions = c("page"), 
  searchType = "web",
  dimensionFilterExp = c("country==cze"),
  rowLimit = sc_row_limit)

## Spojení datasetů a vytvoření sloupců s rozdílem
sc_page_diff <- merge(sc_page, sc_page_cze, by="page", all = T)
sc_page_diff$clicksDiff <- sc_page_diff$clicks.x - sc_page_diff$clicks.y
sc_page_diff$impressionsDiff <- sc_page_diff$impressions.x - sc_page_diff$impressions.y
sc_page_diff$ctrDiff <- sc_page_diff$ctr.x - sc_page_diff$ctr.y
sc_page_diff$positionDiff <- sc_page_diff$position.x - sc_page_diff$position.y

sc_page_diff$clicks.x <- NULL
sc_page_diff$clicks.y <- NULL
sc_page_diff$impressions.x <- NULL
sc_page_diff$impressions.y <- NULL
sc_page_diff$ctr.x <- NULL
sc_page_diff$ctr.y <- NULL
sc_page_diff$position.x <- NULL
sc_page_diff$position.y <- NULL

sc_page_diff <- aggregate(. ~page, data=sc_page_diff, sum, na.rm=TRUE)

head(sc_page_diff)
```

## Data pro dotazy:
```R
## Nastavení kódování
Sys.setlocale("LC_CTYPE", "en_US.UTF-8")

## Potřební knihovny
library(searchConsoleR)
library(googleAuthR)

## Přihlášení se do Search Console
scr_auth()

## Zobrazení všech webů
list_websites()

##############################  Nastavení hodnot ###############################
## Výběr datumu:
sc_params_from  <- as.character(Sys.Date() - 93)
sc_params_to    <- as.character(Sys.Date() - 3)
#sc_params_form <- "2019-07-31"
#sc_params_to   <- "2019-05-01"

## Výběr domény:
sc_params_property <- "https://www.zatkovic.cz/"

## Maximální počet dotazů:
sc_row_limit <- 100000


############## Demonstrace rozdílnosti dat s filrem na zemi a bez ############## 

## Stažení bez omezení na zemi:
sc_query <- search_analytics(
  sc_params_property, 
  sc_params_from, 
  sc_params_to, 
  dimensions = c("query"), 
  searchType = "web", 
  rowLimit = sc_row_limit)

## Stažení s omezením na Českou Republiku
sc_query_cze <- search_analytics(
  sc_params_property, 
  sc_params_from, 
  sc_params_to, 
  dimensions = c("query"), 
  searchType = "web",
  dimensionFilterExp = c("country==cze"),
  rowLimit = sc_row_limit)

## Spojení datasetů a vytvoření sloupců s rozdílem
sc_query_diff <- merge(sc_query, sc_query_cze, by="query", all = T)
sc_query_diff$clicksDiff <- sc_query_diff$clicks.x - sc_query_diff$clicks.y
sc_query_diff$impressionsDiff <- sc_query_diff$impressions.x - sc_query_diff$impressions.y
sc_query_diff$ctrDiff <- sc_query_diff$ctr.x - sc_query_diff$ctr.y
sc_query_diff$positionDiff <- sc_query_diff$position.x - sc_query_diff$position.y

sc_query_diff$clicks.x <- NULL
sc_query_diff$clicks.y <- NULL
sc_query_diff$impressions.x <- NULL
sc_query_diff$impressions.y <- NULL
sc_query_diff$ctr.x <- NULL
sc_query_diff$ctr.y <- NULL
sc_query_diff$position.x <- NULL
sc_query_diff$position.y <- NULL

sc_query_diff <- aggregate(. ~query, data=sc_query_diff, sum, na.rm=TRUE)

head(sc_query_diff)
```

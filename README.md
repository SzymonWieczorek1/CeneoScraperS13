# CeneoScraperS13
## Etap 1 - pobranie opinii 
### Etap 1.1 - pobranie składowych pojedynczej opinii
- pobranie kodu pojedynczej strony z opiniami o produkcie
- wydobycie z kodu fragmentu odpowiadającego pojedynczej opinii

|Składowa|Selektor CSS|Nazwa Zmiennej|Typ danych|
|--------|------------|--------------|----------|
|Opinia|div.js_product-review|opinion||
|Identyfikator opinii|["data-entry-id"]|opinionId||
|Autor|span.user-post_author-name|author||
|Rekomendacja|span.user-post_author-recomendation >em|rcmd||
|Liczba gwiazdek|span.user-post_score-count|start||
|Treść opinii|div.user-post_text|content||
|Liczba zalet|div[class*="positives"]~div.review-feature_item|pros||
|Liczba wad|div[class*="negatives"]~div.review-feature_item|cons||
|Czy potwierdzona zakupem|div.review-pz|purchased||
|Data wystawienia|span.user-post_published > time:nth-time(1)["datetime"]|publishDate||
|Data zakupu|span.user-post_published > time:nth-time(2)["datetime"]|purchaseDate||
|Dla ilu osób przydatne|span[id^="votes-yes"]|useful||
|Dla ilu nieprzydatne|span[id^="votes-no"]|useless||

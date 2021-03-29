# CeneoScraperS13
## Etap 1 - Ekstrakcja pojedynczej opinii o produkcie
### Etap 1.1 - pobranie składowych pojedynczej opinii
- pobranie kodu pojedynczej strony z opiniami o produkcie
- wydobycie z kodu fragmentu odpowiadającego pojedynczej opinii
- zapisanie do pojedynczych zmiennych wartosci skladowych opinii
- obsluga bledow
- transformacja danych do docelowych typów

|Składowa|Selektor CSS|Nazwa Zmiennej|Typ danych|
|--------|------------|--------------|----------|
|Opinia|div.js_product-review|opinion|bs4.element.Tag|
|Identyfikator opinii|["data-entry-id"]|opinionId|str|
|Autor|span.user-post_author-name|author|str|
|Rekomendacja|span.user-post_author-recomendation >em|rcmd|bool|
|Liczba gwiazdek|span.user-post_score-count|stars|float|
|Treść opinii|div.user-post_text|content|str|
|Liczba zalet|div[class*="positives"]~div.review-feature_item|pros|list|
|Liczba wad|div[class*="negatives"]~div.review-feature_item|cons|list|
|Czy potwierdzona zakupem|div.review-pz|purchased|bool|
|Data wystawienia|span.user-post_published > time:nth-time(1)["datetime"]|publishDate|str|
|Data zakupu|span.user-post_published > time:nth-time(2)["datetime"]|purchaseDate|str|
|Dla ilu osób przydatne|span[id^="votes-yes"]|useful|int|
|Dla ilu nieprzydatne|span[id^="votes-no"]|useless|int|

## Etap 2 - Ekstrakcja  wszystkich opinii o produkcie i z pojedynczej strony
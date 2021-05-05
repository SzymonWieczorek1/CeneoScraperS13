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
- utworzenie swnika do przechowywania wszystkich skdowych pojedynczej opinii
- utworzenie listy, do ktorej beda dodawane slowniki 
reprezentujace pojedyncze opinie
- dodanie petli, w ktorej pobierane byly skladowe kolejnych opinii z pojedynczej strony

## Etap 3 - Ekstrakcja wszystkich opinii o produkcie z wszystkich stron
- dodanie petli, w ktorej:
    * pobierana jest strona z opiniami
    * dla kazdej opinii na stronie pobierane sa jej skladniki
    * sprawdzane jest, czy istnieje kolajna strona z opiniami, ktore powinny zostac pobrane
-  zapisanie wszystkich opinii o produkcie do pliku .json

## Etap 4 - Refaktoryzacja kodu
- parametryzacja identyfikatora opinii
- zdefiniowanie funkcji do ekstrakcji pojedynczych opinii
- dodanie słownika opisującego strukturę opinii wraz z selektorami potrzebnymi do ekstrakcji pojedynczych składowych
- użycie wyrażenia słownikowego (dictionary comprehension) do pobrania (i zapisania) składowych pojedynczej opinii
- rezygnacja z transformacji składowych opinii (przeniesienie tego procesu do analizy opinii)

## Etap 5 - Analiza statystyczna zbioru opinii o produkcie
- wyświetlenie listy kodów produktu, dla których zostały pobrane opinie
- wczytanie opinii o wskazanym produkcie do obiektu DataFrame
- obliczanie podstawowych statystyk
    * liczba opinii o produkcie
    * liczba opinii w których podana została lista zalet
    * liczba opinii w których podana została lista wad
    * średnia ocena produktu wyznaczona na podstawie liczby gwiazdek

## Etap 6 - Narysowanie wykresów opartych o dane ze zbioru opinii o produkcie
- wykres kołowy obrazujący udział poszczególnych wartości rekomendacji w ogólnej liczbie opinii
- wykres kolumnowy/słupkowy obrazujący częstość występowania opinii z poszczególnymi ocenami wyrażonymi liczbą gwiazdek

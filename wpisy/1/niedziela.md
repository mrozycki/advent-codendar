Kodendarz Adwentowy
===================

1. tydzień Adwentu: czarny kwadrat na białym tle
------------------------------------------------

Na przełomie lat 1914-15, rosyjski malarz Kazimierz Malewicz utworzył pierwsze na świecie dzieło nieprzedstawiające: "Czarny Kwadrat na Białym Tle". To historyczne dzieło jest teraz jednym z najdroższych dzieł sztuki.

W tym tygodniu nauczysz się pisać programy, które będą tworzyć pliki z czarno-białymi obrazkami. Zwieńczeniem Twojej pracy w tym tygodniu będzie program tworzący reprodukcję dzieła Malewicza.

## Niedziela: Obrazy PBM

W dzisiejszym zadaniu zapoznasz się z PBM - prostym formatem zapisu obrazów. Dzisiaj nie będziesz jeszcze pisać kodu.

*Portable BitMap* to prosty format zapisu czarno-białych obrazów. Obraz w tym formacie to plik tekstowy. W pierwszej linii pliku wpisujemy `P1`, co informuje program do wyświetlania obrazów o tym, że będziemy korzystać z PBM. W drugiej linii znajdują się dwie liczby oddzielone spacją: wysokość i szerokość obrazu. Pozostałe linie pliku składają się z oddzielonych spacjami zer i jedynek: 0 oznacza kolor biały, a 1 czarny.

Przykładowy obraz w PBM wygląda następująco:

```
P1
7 6
0 0 0 0 0 0 0
0 0 1 0 1 0 0
0 0 0 0 0 0 0
0 1 0 0 0 1 0
0 0 1 1 1 0 0
0 0 0 0 0 0 0
```

**Zadanie** Stwórz plik `smile.pbm` i wklej do niego przykłady obrazek powyżej. Zapisz plik. W Ubuntu możesz go otworzyć z przeglądarki plików lub z terminala przy użyciu komendy:

```
$ display smile.pbm
```

Możesz go też zamienić na plik PNG, obsługiwany przez większość systemów operacyjnych:

```
$ convert smile.pbm smile.png
```

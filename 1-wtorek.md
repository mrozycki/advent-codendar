Kodendarz Adwentowy
===================

1. tydzień Adwentu: czarny kwadrat na białym tle
------------------------------------------------

## Wtorek: Płótno

Jeżeli chcesz stworzyć obrazek bardziej skomplikowany niż jednolite tło, warto
jest zacząć od stworzenia opisu obrazu w pamięci komputera, a dopiero na końcu
taki gotowy opis wypisać na ekran.

W tym zadaniu stworzysz program, który wygeneruje obrazek z uśmiechem, taki sam
jak w niedzielnym wpisie:

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

Twój program powinien wykonać następujące kroki:

1. Stwórz tablicę dwuwymiarową 7x6, w której przechowywać będziemy stan pikseli.
```C
int obraz[7][6];
```
2. Wypełnij całą tablicę zerami.
3. Wpisz jedynki w odpowiednie miejsca tablicy. Na przykład dla lewego oka:
```C
obraz[2][1] = 1;
```
4. Wypisz nagłówek obrazka: `P1` w pierwszej linii, wymiary obrazka w drugiej.
5. Wypisz na ekran zawartość tablicy `obraz`.

**Przypomnienie** Kiedy Twój program wypisuje już odpowiedni obraz na ekran, możesz zapisać obraz do pliku używając komendy:
```
$ ./plik > obraz.pbm
```
i wyświetlić go przy użyciu komendy:
```
$ display obraz.pbm
```

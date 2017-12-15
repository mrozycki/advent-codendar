Kodendarz Adwentowy
===================

2. tydzień Adwentu: Gra w Życie
---

## Sobota: Wczytywanie z pliku

Stworzenie planszy z gliderem do testowania jest dość szybkie i nie sprawia
wielu problemów. Jest to jednak tylko jeden wzór, na dodatek dosyć prosty.
Co gdybyśmy chcieli zobaczyć wynik działania czegoś bardziej skomplikowanego,
jak *Glider Gun*? Albo zmieniać używany wzór za każdym razem?

Możemy początkową konfigurację planszy wczytać z pliku.

Załóżmy, że plik z początkowym wzorem wygląda tak:

```C
8 8
0 1 0 0 0 0 0 0
0 0 1 0 0 0 0 0
1 1 1 0 0 0 0 0
0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0
```

Najpierw wysokość i szerokość wzoru, następnie po jednej liczbie dla każdej
komórki: 1 dla żywej, 0 dla martwej.

**Zadanie** Skopiuj powyższy wzór i zapisz go do pliku `glider.txt`,
przyda się później.

Podobnie jak w przypadku wypisywania do pliku, kiedy używaliśmy `printf`, a potem
dzięki magii konsoli zapisywaliśmy wszystko do pliku zamiast na ekran,
tak teraz możemy użyć `scanf`, a potem dzięki magii konsoli wczytać wszystko
z pliku zamiast z klawiatury.

Co jednak wczyta `scanf`, jeżeli na wejściu pojawi się plik jak powyżej?
Otóż `scanf` działa na tzw. *słowach*, czyil ciągach znaków niebiałych
oddzielonych od siebie znakami białymi. Będzie on wczytywać znaki i zapisywać
je do wewnętrznego bufora tak długo, aż natrafi na spację, nową linię, tabulator
lub `EOF`. Wtedy spróbuje przekonwertować zawartość bufora do odpowiedniego
typu podanego w formacie.

To oznacza, że powyższy przykładowy plik nie musi być podzielony na 9 linii.
Mógłby składać się z 66 linii (po jednym znaku na linię), z 1 linii, 18 linii,
106 linii... Tak długo jak zawiera te same 66 liczb w tej samej kolejności,
a poza tym tylko białe znaki - `scanf` potraktuje go tak samo.

Zatem żeby wczytać plik z początkowym wzorem taki jak powyżej, należy:
1. wczytać dwie liczby: wysokość i szerokość,
2. stworzyć planszę o odpowiedniej wysokości i szerokości,
3. dla każdej kolumny *k* i każdego wiersza *w* wczytać liczbę i zapisać ją
jako stan komórki (*k*, *w*).

**Zadanie** Napisz funkcję `scan_board`, która użyje funkcji `scanf` do wczytania
danych początkowej konfiguracji planszy. Dodaj ją do wczorajszego programu
i użyj jej do wczytania wzoru startowego.

```C
struct board scan_board();
```

### Testy

Możesz przetestować swój program używając zapisanego wcześniej wzoru `glider.txt`.
Żeby przekazać go do programu, możesz wykorzystać poniższą komendę w konsoli:

```bash
$ ./program < glider.txt
```

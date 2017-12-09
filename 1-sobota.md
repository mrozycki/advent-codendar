Kodendarz Adwentowy
===================

1. tydzień Adwentu: czarny kwadrat na białym tle
------------------------------------------------

## Sobota: struktura dla płótna

Dzisiaj zakończymy refactoring kodu, tworząc strukturę dla płótna. Zrobimy
też parę zmian w innych miejscach programu, które pozwolą nam zminimalizować
ryzyko dziwnego zachowania programu spowodowanego błędami w kodzie.

Struktura będzie mieć następującą definicję:

```C
struct Canvas {
  int** pixels;
  int width;
  int height;
}; // średnik!
```

Taka struktura płótna pozwala nam na usprawnienie kilku rzeczy.

### Sprawdzanie granic płótna w `rect`

Spróbujmy czegoś takiego, nie używając jeszcze nowej struktury:

```C
int** canvas = create_canvas(100, 100);
rect(canvas, 0, 0, 100, 100, WHITE);
rect(canvas, 20, 90, 20, 20, BLACK);

// (...) wypisz obraz na ekran
```
**Zadanie** Umieść powyższy kod w swoim programie. Sprawdź co się stanie.

Wynik działania takiego kodu będzie... zaskakujący. W celu uniknięcia takich
niespodzianek, możemy funkcję `rect` zmodyfikować w taki sposób, żeby przed
rozpoczęciem rysowania sprawdzała, czy rysowany prostokąt mieści się w granicach
płótna.

```C
void rect(struct Canvas canvas, int x, int y, int width, int height, enum Color fill) {
  // Jeżeli lewy górny róg nie mieści się na płótnie, nie rysuj nic.
  if (x >= canvas.width || y >= canvas.height) return;

  // Jeżeli prawa krawędź nie mieści się na płótnie, rysuj do krawędzi płótna.
  if (x + width >= canvas.width) width = canvas.width - x;

  // Jeżeli dolna krawędź nie mieści się na płótnie, rysuj do krawędzi płótna.
  if (y + height >= canvas.height) height = canvas.height - y;

  // (...) narysuj właściwy prostokąt
}
```
**Zadanie** Zmień swoją funkcję `rect` w sposób opisany powyżej.

Teraz następujący kod nie sprawi nam już tej samej niespodzianki.
```C
struct Canvas canvas = { create_canvas(100, 100), 100, 100 };
rect(canvas, 0, 0, 100, 100, WHITE);
rect(canvas, 20, 90, 20, 20, BLACK);

// (...) wypisz obraz na ekran
```
**Zadanie** Umieść powyższy kod w swoim programie. Sprawdź co się stanie.

### Funkcja `print_pbm`

Możemy teraz też wygodnie wydzielić kod odpowiedzialny za wypisywanie pliku PBM
do osobnej funkcji:

```C
void print_pbm(struct Canvas canvas);
```
**Zadanie** Napisz funkcję `print_pbm`.

Teraz funkcja `main` programu rysującego *Czarny Kwadrat na Białym Tle* wyglądać
będzie tak:

```C
int main() {
  struct Canvas canvas = { create_canvas(100, 100), 100, 100 };

  rect(canvas, 0, 0, 100, 100, WHITE);
  rect(canvas, 20, 20, 60, 60, BLACK);
  print_pbm(canvas);

  return 0;
}
```

Dzięki schowaniu całej *czarnej magii* w funkcjach, dużo łatwiej zrozumieć co
robi cały program. Zdecydowanie łatwiej jest go też modyfikować: zmieniać rozmiar
płótna, dodawać nowe kwadraty czy prostokąty albo zmieniać kolory.

W powyższym programie można dokonać jeszcze jednego niewielkiego kroku refactoringu,
jednak jego znalezienie i wykonanie pozostawione jest jako ćwiczenie dla czytelnika ;)

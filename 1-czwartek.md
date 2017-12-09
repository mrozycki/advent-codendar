Kodendarz Adwentowy
===================

1. tydzień Adwentu: czarny kwadrat na białym tle
------------------------------------------------

## Czwartek: Refactoring

Wczorajszy program generował replikę Czarnego Kwadratu na Białym Tle.
Mogłoby się więc wydawać, że zakończyliśmy tę część projektu. Nic bardziej mylnego.

Po napisaniu pierwotnej, działającej wersji programu, przychodzi czas na
*refactoring*. Polega on na restrukturyzacji kodu w taki sposób, żeby późniejsze
zmiany były łatwiejsze i wymagały jak najmniejszej wiedzy o działaniu całego
programu.

Dobrym sposobem na rozpoczęcie refactoringu wczorajszego programu jest wydzielenie
kodu rysującego kwadrat do funkcji `rect`.

```C
void rect(int** pic, int x, int y, int width, int height, int fill_color);
```

Funkcja ta przyjmuje wskaźnik na tablicę dwuwymiarową `pic` zawierającą obraz,
współrzędne (`x`, `y`) lewego górnego rogu prostokąta, szerokość i wysokość
prostokąta oraz jego kolor. Funkcja nie zwraca żadnej wartości, za to zmienia
wartości w tabeli `pic` tak, aby w obrazie pojawił się odpowiedni prostokąt.

**Zadanie** Napisz funkcję `rect` według powyższej specyfikacji.

Teraz możesz zastąpić czarny kwadrat z poprzedniego programu wywołaniem funkcji:

```C
int **obraz = ...;
// (...)
rect(obraz, 2, 2, 6, 6, 1); // narysuj czarny kwadrat
```

Co najlepsze, początkowe wypełnienie obrazu białym kolorem również można
zastąpić wywołaniem funkcji `rect`!

```C
int **obraz = ...;
rect(obraz, 0, 0, 10, 10, 0); // wypełnij obraz białym kolorem
rect(obraz, 2, 2, 6, 6, 1); // narysuj czarny kwadrat
```

### Alokacja tablicy

Niestety, żeby dwuwymiarowe tablice o nienznaym rozmiarze przekazywać do
funkcji, musimy *zaalokować* miejsce w pamięci na tę tablicę. Kod który
to robi może wyglądać nieco strasznie:

```C
int i;
int **obraz = malloc(10 * sizeof(*obraz));
for (i = 0; i < 10; i++) {
  pixels[i] = malloc(10 * sizeof(*pixels[i]));
}
```

Ale to też możemy wyciągnąć do funkcji:

```C
int** create_canvas(int width, int height) {
  int i;
  int **canvas = malloc(height * sizeof(*canvas));
  for (i = 0; i < height; i++) {
    canvas[i] = malloc(width * sizeof(*canvas[i]));
  }

  return canvas;
}
```

W ten sposób dostajemy:
```C
int **obraz = create_canvas(10, 10);
rect(obraz, 0, 0, 10, 10, 0); // wypełnij obraz białym kolorem
rect(obraz, 2, 2, 6, 6, 1); // narysuj czarny kwadrat
```

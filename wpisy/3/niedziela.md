Kodendarz Adwentowy
===================

3. tydzień Adwentu: Życie w Obrazkach
---

## Niedziela: Rysowanie planszy

Nadszedł czas połączyć wysiłki z ostatnich dwóch tygodni i zacząć generować
obrazki z *Grą w życie*.

Bazować będziemy na programie, który powstał w poprzednim tygodniu, ale musimy
dodać do niego kilka struktur i funkcji, które powstały w tygodniu 1.
Część została nieco zmieniona, żeby lepiej pasować do tego jak wyglądają
struktury i funkcje *Gry w życie*.

```C
enum pixel { WHITE, BLACK };

struct canvas {
  enum pixel** pixels;
  int width;
  int height;
}; // średnik!

struct canvas create_canvas(int width, int height) {
  int i;
  enum pixel **pixels = malloc(height * sizeof(*pixels));
  for (i = 0; i < height; i++) {
    pixels[i] = malloc(width * sizeof(*pixels[i]));
  }

  struct canvas result = { pixels, width, height };
  return result;
}

// funkcja napisana przez Ciebie - wklej ją tutaj
void print_pbm(struct canvas canvas);
```

Dzisiejszym zadaniem jest napisać funkcję `canvas_from_board`, która z podanej
planszy *Gry w życie* stworzy czarno-biały obraz, po jednym pikselu na każde
pole planszy. Dobór kolorów dowolny ;)

```C
struct canvas canvas_from_board(struct board board);
```

### Testy

Możesz użyć poniższej funkcji `main` w swoim programie, aby wczytać `glider.txt`
z pliku, a następnie wypisać `glider.pbm` do pliku.

```C
int main() {
  struct board board = scan_board();
  struct canvas canvas = canvas_from_board(board);

  print_pbm(canvas);

  return 0;
}
```

Powyższy program uruchon przy użyciu komendy jak:

```bash
$ ./program < glider.txt > glider.pbm
```

Dla przypomnienia: plik PBM możesz wyświelić na ekranie:

```bash
$ display glider.pbm
```

Lub przekonwertować go do PNG:

```bash
$ convert glider.pbm glider.png
```

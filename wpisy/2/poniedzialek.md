Kodendarz Adwentowy
===================

2. tydzień Adwentu: Gra w Życie
---

## Poniedziałek: Struktura planszy

Tym razem rozpoczniemy od zbudowania struktury, która przechowywać
będzie stan naszej planszy.

```C
struct board {
  enum cell** cells;
  int width;
  int height;
}; // średnik!
```

W teorii plansza do *Gry w Życie* jest nieskończona w obu kierunkach. Jednak
na komputerze trochę trudno przechowuje się nieskończenie duże rzeczy. Dlatego
nasza plansza będzie jedynie udawać nieskończenie dużą. Komórki mieszczące
się w tablicy będą żywe lub martwe, w zależności od tego co mówi tablica. Pozostałe
komórki będą zawsze martwe i nie będą mogły zmienić tego stanu.

Przede wszystkim przyda się nam kuzynka naszej dobrej znajomej, `create_canvas`,
którą nazwiemy `create_board`. Tym razem, dla wygody, od razu zamkniemy stworzoną
tablicę dwuwymiarową w strukturę.

```C
struct board create_board(int width, int height) {
  int i;
  enum cell **cells = malloc(height * sizeof(*cells));
  for (i = 0; i < height; i++) {
    cells[i] = malloc(width * sizeof(*cells[i]));
  }

  return { cells, width, height };
}
```

Teraz stworzymy dwie funkcje, które ułatwią nam utrzymanie iluzji nieskończonej
tablicy: `is_alive` oraz `set_alive`.

```C
enum cell is_alive(struct board board, int x, int y);
void set_alive(struct board board, int x, int y, enum cell state);
```

Pierwsza z nich zwraca `DEAD` lub `ALIVE` w zależności od tego czy komórka o
współrzędnych (*x*, *y*) jest żywa czy martwa. Dla komórek w tablicy, wartość
powinna być odczytana z tablicy, dla pozostałych powinno być to zawsze `DEAD`.
Jest to tak zwany *getter*.

Druga z nich przyjmuje jako argument nowy stan komórki o współrzędnych (*x*, *y*).
Jej zadaniem jest zmiana stanu tej komórki w tablicy, jeżeli komórka mieści się
w tablicy. Jeżeli nie - funkcja nie powinna robić nic. Jest to tak zwany *setter*.

### Testy

Możesz przetestować działanie swoich funkcji wklejając je na dole poniższego
programu i uruchamiając go:

```C
#include <stdio.h>
#include <stdlib.h>

enum cell { DEAD, ALIVE };
struct board {
  enum cell** cells;
  int width;
  int height;
}; // średnik!

struct board create_board(int width, int height) {
  int i;
  enum cell **cells = malloc(height * sizeof(*cells));
  for (i = 0; i < height; i++) {
    cells[i] = malloc(width * sizeof(*cells[i]));
  }

  struct board result = { cells, width, height };
  return result;
}

enum cell is_alive(struct board board, int x, int y);
void set_alive(struct board board, int x, int y, enum cell state);

int tests_conducted = 0;
int tests_passed = 0;
int assert_eq(enum cell actual, enum cell expected) {
  tests_conducted ++;
  if (actual == expected) {
    printf("Test #%d passed\n", tests_conducted);
    tests_passed ++;
  } else {
    printf("Test #%d failed\n", tests_conducted);
    printf("\t> expected %s, got %s\n",
      (expected ? "ALIVE" : "DEAD"), (actual ? "ALIVE" : "DEAD"));
  }
}

int main() {
  struct board board = create_board(10, 10);

  assert_eq(is_alive(board, 0, 0), DEAD);
  assert_eq(is_alive(board, 9, 9), DEAD);
  set_alive(board, 0, 0, ALIVE);
  assert_eq(is_alive(board, 0, 0), ALIVE);
  set_alive(board, 9, 9, ALIVE);
  assert_eq(is_alive(board, 9, 9), ALIVE);

  assert_eq(is_alive(board, 3, 4), DEAD);
  assert_eq(is_alive(board, 4, 3), DEAD);
  set_alive(board, 3, 4, ALIVE);
  assert_eq(is_alive(board, 3, 4), ALIVE);
  assert_eq(is_alive(board, 4, 3), DEAD);

  assert_eq(is_alive(board, 10, 10), DEAD);
  assert_eq(is_alive(board, -1, -1), DEAD);
  set_alive(board, 10, 10, ALIVE);
  assert_eq(is_alive(board, -1, -1), DEAD);
  set_alive(board, -1, -1, ALIVE);
  assert_eq(is_alive(board, -1, -1), DEAD);
}

// tutaj wklej swój kod
```

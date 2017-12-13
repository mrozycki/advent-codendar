Kodendarz Adwentowy
===================

2. tydzień Adwentu: Gra w Życie
---

## Wtorek: Liczenie sąsiadów

Do tej pory mamy napisane poniższe funkcje:

```C
struct board create_board(int width, int height);
enum cell next_state(enum cell current, int number_of_neighbors);
enum cell is_alive(struct board board, int x, int y);
void set_alive(struct board board, int x, int y, enum cell state);
```

Dzisiejszym zadaniem będzie dodać kolejne dwie funkcje:

```C
int count_neighbors(struct board board, int x, int y);
enum cell next_state(struct board board, int x, int y);
```

Pierwsza z nich, `count_neighbors`, powinna znaleźć i zwrócić liczbę wszystkich
żywych sąsiadów komórki o współrzędnych (*x*,*y*). Pamiętaj o komórkach
znajdujących się na skos! Do sprawdzenia czy sąsiedzi żyją, polecam użyć funkcji
`is_alive`, która ułatwi obliczenia dla komórek przy krawędzi planszy
(z sąsiadami znajdującymi się poza planszą).

Druga z nich, `next_state`, jest *przeładowaniem* napisanej już wcześniej
funkcji `next_state`. Znaczy to że ma tę samą nazwę, ale różne listy argumentów.
Ma jednak takie samo zadanie - zwrócić stan podanej komórki w kolejnym pokoleniu,
tym razem jednak na podstawie planszy, a nie znanej już liczby sąsiadów. Do
napisania tej funkcji możesz (a wręcz zalecam) wykorzystać istniejące już
funkcje `count_neighbors` i `next_state(enum cell, int)`.

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

int count_neighbors(struct board board, int x, int y);
enum cell next_state(struct board board, int x, int y);

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

int assert_eq(int actual, int expected) {
  tests_conducted ++;
  if (actual == expected) {
    printf("Test #%d passed\n", tests_conducted);
    tests_passed ++;
  } else {
    printf("Test #%d failed\n", tests_conducted);
    printf("\t> expected %d, got %d\n", expected, actual);
  }
}

int main() {
  struct board board = create_board(5, 5);
  board.cells[2][1] = ALIVE;
  board.cells[3][2] = ALIVE;
  board.cells[1][3] = board.cells[2][3] = board.cells[3][3] = ALIVE;

  assert_eq(count_neighbors(board, 0, 0), 0);
  assert_eq(count_neighbors(board, 4, 4), 1);
  assert_eq(count_neighbors(board, 2, 2), 5);

  assert_eq(next_state(board, 0, 0), DEAD);
  assert_eq(next_state(board, 4, 4), DEAD);
  assert_eq(next_state(board, 2, 2), DEAD);
  assert_eq(next_state(board, 2, 4), ALIVE);
  assert_eq(next_state(board, 1, 2), ALIVE);
  assert_eq(next_state(board, 2, 1), DEAD);
  assert_eq(next_state(board, 1, 3), DEAD);
}

// tutaj wklej swój kod
```

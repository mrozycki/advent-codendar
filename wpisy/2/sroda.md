Kodendarz Adwentowy
===================

2. tydzień Adwentu: Gra w Życie
---

## Środa: nowe pokolenie

Dzisiejszym zadaniem będzie napisać funkcję `next_generation`, która
na podstawie planszy obecnego pokolenia wygeneruje nowe pokolenie.

```C
struct board next_generation(struct board current);
```

Funkcja powinna działać według następującego schematu:

1. Stwórz nową, pustą planszę, o takich samych wymiarach jak `current`.
2. Dla każdego pola planszy `current`:
  1. użyj istniejących funkcji, żeby obliczyć nowy stan tego pola,
  2. Umieść obliczony stan w odpowiednim miejscu nowej planszy.
3. Zwróć stworzoną w ten sposób nową planszę.

Napisz również funkcję `print_board`, która wypisze na ekran stan całej planszy.

```C
void print_board(struct board board);
```

Funkcja ta służy jedynie dla Twojej wygody i możliwości testowania kodu,
dokładny wygląd wypisanej planszy nie ma większego znaczenia.
Dla lepszej czytelności użyj dużych znaków, jak `X` czy `O` dla komórek żywych,
a małych znaków, jak `.` czy nawet spacja dla komórek martwych, np.:

```
.....
..O..
...O.
.OOO.
.....
```

## Testy

Poniższy program wypisze na ekran kolejne pokolenie pokazanego wyżej *glidera*.

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

struct board next_generation(struct board current);
void print_board(struct board board);

int main() {
  struct board board = create_board(5, 5);
  board.cells[2][1] = ALIVE;
  board.cells[3][2] = ALIVE;
  board.cells[1][3] = board.cells[2][3] = board.cells[3][3] = ALIVE;

  printf("Pierwotne pokolenie\n");
  print_board(board);
  printf("\n");

  struct board next_board = next_generation(board);
  printf("Kolejne pokolenie\n");
  print_board(board);
  printf("\n");

  return 0;
}

// tutaj wklej swój kod
```

Kolejne pokolenie *glidera* wygląda tak:

```
.....
.....
.O.O.
..OO.
..O..
```

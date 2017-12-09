Kodendarz Adwentowy
===================

2. tydzień Adwentu: Gra w Życie
---

## Niedziela: Reguły *Gry w Życie*

Na Wikipedii znajduje się świetny [opis](https://pl.wikipedia.org/wiki/Gra_w_%C5%BCycie)
zasad *Gry w Życie* wraz z wieloma ciekawymi przykładami. Zapoznaj się z
*Opisem reguł gry* i przejrzyj znajdujące się poniżej przykłady struktur,
w szczególności animacje.

**Zadanie** Napisz funkcję `next_state` według następującego opisu:

```C
enum cell { DEAD, ALIVE };
enum cell next_state(enum cell current, int number_of_neighbors);
```

Funkcja przyjmuje dwa argumenty: obecny stan komórki (`DEAD` lub `ALIVE`)
oraz liczbę żywych sąsiadów tej komórki (0-8). Wynikiem powinien być stan
tej komórki w następnym pokoleniu (`DEAD` lub `ALIVE`) według poniższych regul:

* jeżeli komórka jest żywa
  * jeżeli ma 2 lub 3 sąsiadów pozostaje żywa
  * w przeciwnym wypadku umiera (staje się martwa)
* jeżeli komórka jest martwa
  * jeżeli ma 3 sąsiadów rodzi się (staje się żywa)
  * w przeciwnym wypadku pozostaje martwa

Możesz przetestować poprawność swojej funkcji wklejając ją na dole
poniższego programu i uruchamiając go:

```C
#include <stdio.h>

enum cell { DEAD, ALIVE };
enum cell next_state(enum cell current, int number_of_neighbors);

int tests_conducted = 0;
int tests_passed = 0;
int test(enum cell current, int number_of_neighbors, enum cell expected_next) {
  tests_conducted ++;
  if (next_state(current, number_of_neighbors) == expected_next) {
    printf("Test #%d passed\n", tests_conducted);
    tests_passed ++;
  } else {
    printf("Test #%d failed\n", tests_conducted);
    printf("\t> %s with %d neighbours should be %s\n",
      (current ? "ALIVE" : "DEAD"), number_of_neighbors, (expected_next ? "ALIVE" : "DEAD"));
  }
}

int main() {
  test(DEAD, 3, ALIVE);
  test(ALIVE, 2, ALIVE);
  test(ALIVE, 3, ALIVE);

  test(DEAD, 0, DEAD);
  test(DEAD, 1, DEAD);
  test(DEAD, 2, DEAD);
  test(DEAD, 4, DEAD);
  test(DEAD, 5, DEAD);
  test(DEAD, 6, DEAD);
  test(DEAD, 7, DEAD);
  test(DEAD, 8, DEAD);

  test(ALIVE, 0, DEAD);
  test(ALIVE, 1, DEAD);
  test(ALIVE, 4, DEAD);
  test(ALIVE, 5, DEAD);
  test(ALIVE, 6, DEAD);
  test(ALIVE, 7, DEAD);
  test(ALIVE, 8, DEAD);

  printf("%d/%d tests passed\n", tests_passed, tests_conducted);
}

// tutaj wklej swoją funkcję
```

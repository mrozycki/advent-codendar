Kodendarz Adwentowy
===================

2. tydzień Adwentu: Gra w Życie
---

## Piątek: Czyszczenie pamięci

Zmienne, które tworzymy w programie, zajmują miejsce w pamięci kompuera -
a ta jest skończona. Pojedyncza wartość, jak `int`, `char` czy `double`
zajmować będzie raptem kilka bajtów. Ciężko będzie takimi zapełnić całą
pamięć.

Tablice mogą już jednak dość łatwo zajmować dużo miejsca, szczególnie
tablice dwuwymiarowe. Po 1000 `int`ów w jażdą stronę daje 4 megabajty. Jeżeli
chcemy stworzyć animację dla 1000 pokoleń? 1000 takich tablic daje 4 gigabajty,
a to już znaczący ułamek pamięci większości domowych komputerów.

Pamięć, której program już nie używa, powinna być zwalniana. Jeżeli tak się nie
dzieje, dostajemy *wycieki pamięci*. Dla programów, których działanie kończy
się po kilku sekundach nie są one zazwyczaj problemem - cała używana przez nie
pamięć zostanie zwolniona po zakończeniu ich działania.

Jednak dla aplikacji które działać mają dłużej, wręcz dowolnie długo, jak
systemy operacyjne, przeglądarki internetowe, edytory tekstu... wycieki pamięci
mogą prowadzić do ogromnych problemów dla użytkowników. Warto nauczyć
się prawidłowego zarządzania pamięcią na prostszych przykładach.

Programy powinny po sobie sprzątać. Zmienne lokalne są automatycznie usuwane
z pamięci, a zajęte przez nie miejsce zwalniane, na końcu funkcji w których
były stworzone - co jest już drugim powodem żeby się nimi zbytnio nie przejmować.

Za to tablice i struktury tworzone przy użyciu funkcji `malloc` i podobnych
muszą być zwolnione ręcznie. Kompilator nie wie, czy dany kawałek zaalokowanej
pamięci nie jest używany jeszcze gdzieś indziej w programie, więc nie może
usunąć go automatycznie. Programista wie, kiedy pamięć nie będzie już potrzebna,
więc może usunąć ją ręcznie.

A skoro nasze plansze tworzyliśmy przy użycio `malloc`:

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

to musimy je zwolnić przy użyciu `free`:

```C
void destroy_board(struct board board) {
  int i;
  for (i = 0; i < height; i++) {
    free(cells[i]);
  }
  free(cells);
}
```

Dodaj powyższą funkcję do swojego wczorajszego programu. Użyj jej do zwolnienia
pamięci zajętej przez poprzednie pokolenie po wygenerowaniu nowego.

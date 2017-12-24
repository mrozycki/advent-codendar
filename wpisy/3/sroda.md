Kodendarz Adwentowy
===================

3. tydzień Adwentu: Życie w Obrazkach
---

## Środa: wiele plików

Dzisiaj dopiszemy do naszego programu tworzenie i zapisywanie kilku kolejnych
pokoleń *Gry w Życie*. Jutro zajmiemy się sklejaniem ich w animacje.

Jako że w poprzednim tygodniu pisaliśmy już program który generował więcej
niż jedno pokolenie, samo generowanie wielu pokoleń nie powinno być problemem.
Nawet zapisanie ich wszystkich do pliku. Ale... no właśnie, jednego pliku.

Jeżeli za każdym razem użyjemy tej samej nazwy wywołując `print_pbm`, to
w efekcie dostaniemy tylko jeden plik, zawierający obraz wypisany przez
ostatnie wywołanie tej funkcji.

Musimy za każdym razem użyć innej nazwy, np. `plansza_001.pbm`, `plansza_002.pbm`,
`plansza_003.pbm` itd. Do wygenerowania takiej serii nazw możemy użyć metody
`sprintf`, która działa podobnie do `printf` i `fprintf`, z tą różnicą, że
wynik zapisuje do zmiennej typu `char*`.

```C
char filename[255];
sprintf(filename, "plansza_%d.pbm", 8);
printf("%s\n", filename); // wypisze "plansza_8.pbm"
```

Musimy oczywiście gdzieś zapamiętać ile plansz już wygenerowaliśmy, na przykład:

```C
struct board current_board = scan_board();
int boards_generated = 1;

while (/* nie chcemy skończyć */)
{
  char filename[255];
  sprintf(filename, "plansza_%d.pbm", boards_generated);
  print_pbm(filename, canvas_from_board(current_board));

  current_board = next_generation(current_board);
  boards_generated ++;
}
```

Dodatkowe zera w nazwie pliku (np. `plansza_001.pbm`) napisane wyżej nie były
przypadkowe. Dzięki nim kolejne nazwy pliku są ułożone w kolejności alfabetycznej.
Dzięki temu `plansza_002.pbm` znajduje się przed `plansza_010.pbm`. Bez dodatkowych
zer dostalibyśmy `plansza_10.pbm` przed `plansza_2.pbm`, a to bardzo utrudniłoby
nam jutrzejsze zadanie.

Aby otrzymać taki efekt możemy użyć w formacie `sprintf` zapisu `%03d`. Tutaj
3 oznacza, że chcemy aby nasza liczba po wypisaniu składała się z co najmniej 3 znaków,
natomiast 0 oznacza, że brakujące cyfry chcemy uzupełnić zerami.

```C
char filename[255];
sprintf(filename, "plansza_%03d.pbm", 8);
printf("%s\n", filename); // wypisze "plansza_008.pbm"
```

**Zadanie** Napisz program, podobny do tego z czwartku w zeszłym tygodniu, z tą
różnicą, że każde pokolenie wypisane na ekran powinno być również zapisywane
do kolejnego pliku `plansza_XXX.pbm`.

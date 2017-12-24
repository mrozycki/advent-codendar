Kodendarz Adwentowy
===================

3. tydzień Adwentu: Życie w Obrazkach
---

## Wtorek: Zapisywanie do pliku

*Ale przecież już zapisuję obrazki do pliku!* Problem polega na tym, że nie
z poziomu programu, ale z poziomu konsoli linuksowej. Działa do dobrze, dopóki
chcesz wypisać tylko jeden plik - ale jutro będziemy wypisywać ich wiele.

Dlatego dzisiaj stworzymy funkcję `print_pbm(char*, struct canvas)`, która
wypisze podane płótno bezpośrednio do pliku.

```C
void print_pbm(char* filename, struct canvas canvas);
```

Funkcja ta powinna zrobić 3 rzeczy:

1. Otworzyć do zapisu plik o nazwie danej przez `filename`.
2. Wypisać obraz w formacie PBM do tego pliku.
3. Zamknąć plik.

Do obsługi plików używać będziemy wbudowanego w C typu zmiennej `FILE`.
Opisany jest on w pliku nagłówkowym `stdlib.h`, stąd musimy dołaczyć go do
programu używając dyrektywy `#include`.

Wtedy możemy otworzyć plik do zapisu używając funkcji `fopen`:

```C
FILE *file = fopen("nazwa_pliku.abc", "w"); // gwiazdka przed file!
```

`fopen` otwiera plik o podanej nazwie. Jeżeli taki plik nie istnieje, podjęta
zostanie próba jego stworzenia.

Pierwszy argument tej funkcji to nazwa pliku, drugi to sposób dostępu który
chcemy uzyskać. Litera `w` (od *write*) oznacza zapis - chcemy do pliku pisać.
Gdybyśmy chcieli czytać, użylibyśmy `r`, a jeżeli oba na raz: `rw`.

**Uwaga!** Jeżeli pliku o podanej nazwie nie uda się otworzyć, `fopen` zwróci
`NULL` - wskaźnik na nic. W takiej sytuacji powinniśmy wypisać na ekran
informację o błędzie i zakończyć próbę wypisywania tekstu.

```C
if (file == NULL)
{
  printf("Nie udalo sie otworzyc pliku!\n");
  return;
}
```

`fopen` zwraca wskaźnik do *deskryptora* (trudne słowo), który to wskaźnik możemy
potem wykorzystać do operowania na pliku. Na przykład możemy do niego coś zapisać
używając `fprintf`.

```C
fprintf(file, "Hello, world!\n");
fprintf(file, "2+2*2=%d\n", 2+2*2);
```
Użycie `fprintf` jest niemal identyczne do użycia `printf`. Jedyna różnica jest
taka, że jako pierwszy argument podajemy wskaźnik do deskryptora, dopiero potem
format i resztę argumentów.

**Ciekawostka:** do odczytu z pliku możemy użyć `fscanf`, które działa dokładnie
tak samo jak `scanf`. Jedyna różnica jest taka, że jako pierwszy argument podajemy
wskaźnik do deskryptora.

Na koniec plik trzeba **zamknąć**. Cel zamykania pliku jest podwójny: po pierwsze
umożliwia otwarcie pliku przez inne programy, po drugie zwalnia pamięć zajętą
przez deskryptor.

**Zadanie:** Napisz funkcję `print_pbm`, która wypisze obraz w formacie PBM
do pliku o podanej nazwie.

```C
void print_pbm(char* filename, struct canvas canvas);
```

### Testy

Użyj programu podobnego do wczorajszego aby narysować przeskalowaną wersję
planszy i wrzucić ją bezpośrednio do pliku.

```C
int main() {
  struct board board = scan_board();
  struct canvas canvas = canvas_from_board(board, 10);

  print_pbm("plansza.pbm", canvas);

  return 0;
}
```

Zwróć uwagę, że nazwa pliku przekazana do `print_pbm` zawiera również rozszerzenie
tego pliku. Podobnie nazwa pliku przekazywana do `fopen` powinna zawierać
rozszerzenie.

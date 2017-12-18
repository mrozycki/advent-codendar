Kodendarz Adwentowy
===================

3. tydzień Adwentu: Życie w Obrazkach
---

## Poniedziałek: Skalowanie

Obrazek tworzony przez kod z wczorajszego wpisu jest bardzo mały. Każda
komórka zajmuje tylko jeden piksel. Czasami jest to pożądany wynik, na przykład
gdy chcemy zmieścić duży wzór w całości na ekranie.

Jednak przy testowaniu kodu na małych wzorach, wygodniej byłoby mieć nieco
większe komórki. Zamiast ustawiać pojedyncze piksele, możemy rysować kwadraty
używając funkcji `rect` z pierwszego tygodnia kodendarza.

Twoim dzisiejszym zadaniem będzie dopisać nową wersję funkcji `canvas_from_board`,
która oprócz planszy przyjmie jako argument *współczynnik skalowania*, to jest
szerokość i wysokość jaką powinna mieć na obrazku każda komórka. Jest to zarazem
wartość przez którą powinniśmy przemnożyć wymiary planszy aby otrzymać wymiary obrazka.

```C
struct canvas canvas_from_board(struct board board, int scale_factor);
```

Pamiętaj o ustawieniu odpowiedniej wielkości płótna. Komórka mająca współrzędne
(*x*, *y*) może zostać narysowana używając kodu podobnego do poniższego.

```C
rect(canvas, x*scale_factor, y*scale_factor, scale_factor, scale_factor, BLACK);
```

### Testy

Użyj programu podobnego do wczorajszego aby narysować przeskalowaną wersję
planszy.

```C
int main() {
  struct board board = scan_board();
  struct canvas canvas = canvas_from_board(board, 10);

  print_pbm(canvas);

  return 0;
}
```

Spróbuj użyć innych wartości współczynnika skalowania i upewnij się, że powstały
obrazek jest odpowiednio większy lub mniejszy.

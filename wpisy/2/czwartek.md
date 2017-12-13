Kodendarz Adwentowy
===================

2. tydzień Adwentu: Gra w Życie
---

## Czwartek: wiele pokoleń

Kod do generowania kolejnego pokolenia *Gry w życie* jest gotowy. Czas
napisać prosty program, który będzie wypisywał kolejne pokolenia w konsoli.
W przyszłym tygodniu zajmiemy się generowaniem obrazów z planszy,
a potem animacji.

Napisz program, który będzie działał według następującego schematu:

1. Stwórz pustą planszę. Wymiary i zawartość planszy mogą być dowolne.
2. Wypisz początkowy wygląd planszy na ekran.
3. Pobierz pojedynczy znak od użytkownika.
  1. Jeżeli był to `EOF`, zakończ działanie programu.
  2. W przeciwnym wypadku wygeneruj kolejne pokolenie, wypisz je na ekran.
4. Powtarzaj punkt 3 aż użytkownik wprowadzi `EOF`.

### Testy

Testowanie programu polecam od pokazanego wczoraj *glidera*. Tym razem polecam
jednak zacząć od większej planszy, jako że *glider* się porusza.

Jego kolejne pokolenia wyglądają tak (wypisane obok dla zachowania miejsca,
Twój program powinien wypisywać je jedno pod drugim):

```
..... ..... ..... ..... .....
..O.. ..... ..... ..... .....
...O. .O.O. ...O. ..O.. ...O.
.OOO. ..OO. .O.O. ...OO ....O
..... ..O.. ..OO. ..OO. ..OOO
```

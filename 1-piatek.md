Kodendarz Adwentowy
===================

1. tydzień Adwentu: czarny kwadrat na białym tle
------------------------------------------------

## Piątek: pozbywanie się magicznych liczb

*Magicznymi liczbami* nazywa się takie stałe liczbowe w programie, które
oznaczają coś ważnego, ale z samego kawałka kodu który ich używa nie bardzo
da się wywnioskować co.

We wczorajszym wpisie pojawił się taki kawałek kodu:

```C
int obraz[10][10];
rect(obraz, 0, 0, 10, 10, 0); // wypełnij obraz białym kolorem
rect(obraz, 2, 2, 6, 6, 1); // narysuj czarny kwadrat
```

Tutaj `0` i `1` oznaczające kolory są takimi magicznymi liczbami. Bez komentarzy
obok kodu ciężko byłoby wywnioskować co mogą oznaczać. Dużo lepiej wyglądałoby
to w takiej formie:

```C
int obraz[10][10];
rect(obraz, 0, 0, 10, 10, WHITE); // wypełnij obraz białym kolorem
rect(obraz, 2, 2, 6, 6, BLACK); // narysuj czarny kwadrat
```

Jednak jak do tej pory nie zdefiniowaliśmy co oznacza `WHITE` i `BLACK`.
Możemy zrobić to na dwa sposoby.

Pierwszy z nich to dyrektywy `define`, to znaczy:

```C
#define WHITE 0
#define BLACK 1
```

Co zadziała... ale nie jest najlepszym sposobem. Dużo lepsze jest użycie
*wyliczeń*, tzw. `enum`ów.

```C
enum Color { WHITE, BLACK };
```

Nie dosyć, że jest krótsze, to pozwala nam na lekką zmianę funkcji `rect`,
która będzie lepiej przekazywać jej ideę:

```C
void rect(int** pic, int x, int y, int width, int height, enum Color fill);
```

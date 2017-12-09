Kodendarz Adwentowy
===================

1. tydzień Adwentu: czarny kwadrat na białym tle
------------------------------------------------

## Poniedziałek: Biały Kwadrat na Białym Tle

W dzisiejszym zadaniu napiszesz program, który wygeneruje replikę innego znanego dzieła Malewicza: *Biały Kwadrat na Białym Tle*.

Twoim zadaniem jest napisać program, który wygeneruje następujący tekst:

W pierwszej linii `P1`, żeby zaznaczyć że używamy PBM. W drugiej linii dwie dziesiątki: wymiary obrazu. Następnie 10 linii, po 10 zer w każdej: 100 białych pikseli.

```
P1
10 10
0 0 0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0 0 0
```

W pierwszej kolejności skup się na wypisaniu odpowiedniego tekstu na ekran. Zapisaniem tego tekstu do pliku zajmiemy się później.

Dla przypomnienia, w konsoli Linuksa przydadzą Ci się następujące polecenia:

* `cd nazwa_katalogu` - przechodzi do katalogu `nazwa_katalogu`
* `touch plik.c` - tworzy w obecnym katalogu pusty plik o nazwie `plik.c`
* `gedit plik.c` - otwiera `plik.c` w graficznym edytorze tekstu
* `gcc plik.c -o plik` - kompiluje `plik.c` i tworzy z niego plik wykonywalny `plik`
* `./plik` - uruchamia plik wykonywalny `plik`

Kiedy już Twój program będzie gotowy i będzie wypisywać odpowiedni tekst na ekran, możesz użyć poniższego polecenia, żeby wynik programu zapisać do pliku:

```
$ ./plik > obraz.pbm
```

Uruchomi on plik wykonywalny `plik` i zapisze jego wynik do pliku `obraz.pbm`. Program nie wypisze nic na ekran - wszystko wyląduje prosto w pliku podanym po `>`.

Jeżeli chcesz sprawdzić co wygenerował Twój program, możesz użyć poniższego polecenia:

```
$ cat obraz.pbm
```

Możesz też oczywiście wyświetlić swój obraz lub przekonwertować go do PNG.

```
$ display obraz.pbm
$ convert obraz.pbm obraz.png
```

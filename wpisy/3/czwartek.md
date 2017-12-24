# Kodendarz Adwentowy

3. tydzień Adwentu: Życie w Obrazkach
---

## Czwartek: Generowanie animacji

Jeżeli do tej pory wszystkie zadania wykonane były prawidłowo, dzisiejsze
zadanie będzie jednocześnie najprostszym i najbardziej satysfakcjonującym.

Program napisany wczoraj powinien generować serię obrazków o nazwach postaci
`plansza_XXX.pbm`, gdzie `XXX` to kolejne liczby naturalne dopełnione zerami
od lewej strony tak, aby uzyskać zawsze 3 cyfry. Na przykład:
`plansza_001.pbm`, `plansza_002.pbm`, `plansza_003.pbm`, `plansza_004.pbm`,
`plansza_005.pbm`...

Teraz zamiana tej serii obrazków w plik mp4 z animacją wymaga uruchomienia
jednej komendy w linii poleceń:

```sh
$ convert -delay 100 plansza_*.pbm animacja.mp4
```

Sam program `convert` jest nam już znany. Pozwala on w bardzo prosty sposób
konwertować obrazy w różnych formatach. Wystarczy podać jedynie nazwę
pliku wejściowego (do przekonwertowania) oraz wyjściowego (wyniku konwersji).

```sh
$ convert obraz.pbm obraz.png
```

Jego możliwości są jednak znacznie większe. Dzisiaj użyjemy go do wygenerowania
pliku z filmem mp4. I tutaj podobnie, większość wymaganych informacji
to nazwy plików wejściowych (kolejnych klatek animacji) oraz nazwa pliku
wyjściowego (filmu).

```sh
$ convert plansza_*.pbm animacja.mp4
```

Jako że plików wejściowych jest wiele, używamy gwiazdki żeby opisać je wszystkie
na raz.

Musimy jednak podać jeszcze jedną informację: jak dużo czasu powinno upłynąć
pomiędzy wyświetlaniem kolejnych klatek. Informację tę podajemy po fladze `-delay`
jako liczbę setnych części sekundy (t.j. 100 oznacza jedną sekundę).

Stąd komenda z początku tego wpisu wygeneruje film, gdzie kolejne klatki
animacji wyświetlać się będą po 1 sekundzie.

```sh
$ convert -delay 100 plansza_*.pbm animacja.mp4
```

**Uwaga** Większość programów działających w linii poleceń używa dwóch rodzajów
flag (opcji): krótkich: jednoliterowych poprzedzonych jednym myślnikiem (np. `-d`),
oraz długich: jednowyrazowych poprzedzonych dwoma myślnikami (np. `--delay`).
Nieliczne programy z nieznanych mi przyczyn łamią tę konwencję używając flag
długich z pojedynczym myślikiem. Jednym z nich jest `convert`.

**Zadanie** Stwórz film z animacją *glidera*. Od Ciebie zależy jak będzie duża,
z ilu będzie się składać pokoleń oraz jak szybko będzie się wyświetlać.

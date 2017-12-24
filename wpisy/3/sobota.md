# Kodendarz Adwentowy

3. tydzień Adwentu - Życie w Obrazkach
---

## Sobota: Co dalej?

Cel założony na początku kodendarza został osiągnięty. Program, który generuje
animacje gry w życie - gotowy. Co dalej?

### Więcej animacji *Gry w Życie*

Możesz dalej rozwijać ten projekt. W jaki dokładnie sposób - to już zależy
od Ciebie. Poniżej kilka moich pomysłów wraz z podpowiedziami jak je osiągnąć.

* kolory - PBM jest jednym z rodziny 3 prostych formatów obrazów. Oprócz niego
istnieje także PGM dla obrazów w odcieniach szarości oraz PPM dla obrazów
kolorowych. Doczytaj o nich na wikipedii i stwórz kolorowe animacje!
* PNG - wspomniany wczoraj *libpng* pozwala na tworzenie plików PNG z poziomu
kodu. Można dzięki niemu zaoszczędzić sporo miejsca na tymczasowych obrazkach.
* wyświetlanie na ekranie - zamiast generować animację w pliku, może chcesz
wyświetlać ją bezpośrednio na ekranie? Dobrym sposobem będzie użycie biblioteki
*Allegro* albo *SDL*.
* szybsze generowanie kolejnego pokolenia - jeżeli 90% Twojej planszy to martwe
pola z martwymi sąsiadami, to 90% czasu potrzebnego na generowanie kolejnego
pokolenia poświęcone jest na bezsensowne obliczenia. Może istnieje jakiś sposób
na pozbycie się tych obliczeń?
* inne reguły *Gry w życie* - zasady 23/3 przedstawione w kodendarzu są
oryginalnymi zasadami użytymi przez Johna Conwaya. Istnieją jednak inne reguły
generujące równie interesujące animacje, jak 34/34. Możesz doczytać o nich
więcej na Wikipedii. Zmień swój program tak, aby plik z początkową planszą
opisywał także reguły które mają być użyte.
* zrób to samo, ale w innym języku programowania - problem z C jest taki, że
w obecnych czasach jest językiem coraz bardziej niszowym. Naucz się innego języka,
jak Java, C# czy Python, i napisz w nim to samo, a potem weź się za inne projekty.

### Więcej animacji, mniej *Gry w Życie*

Jeżeli chcesz stworzyć więcej animacji, ale znudziła Cię już *Gra w życie*,
to mam dla Ciebie kilka inspiracji:

* mrówka Langtona - inny, prostszy automat komórkowy.
* zbiór Mandelbrota - co prawda jest to statyczny obraz, ale nieskończenie
zoomowalny, co pozwala na tworzenie świetnych animacji.
* generowanie i przechodzenie labiryntów - parę słów kluczy: BFS, DFS,
algorytm Prima, algorytm Kruskala
* triangulacja Delaunaya, diagram Woronoja

### Chcę zrobić coś innego

Ale ileż można w kółko robić to samo... Może teraz coś bardziej praktycznego?

* kółko i krzyżyk - napisz prostą wersję gry w kółko i krzyżyk. Może działać
wtedy w wierszu poleceń (wszystkie potrzebne narzędzia już znasz) albo
w graficznym okienku (wtedy zainteresuj się *Allegro* lub *SDL*).
* text adventure - http://textadventures.co.uk/
* gra w statki - może nawet po sieci?
* lista rzeczy do zrobienia - trochę sztampowo, ale pozwala się wiele nauczyć.
Początkowo możesz wszystko obługiwać z wiersza poleceń, ale potem może
dodać coś w rodzaju GTK, żeby wszystko wyświetlało się w okienkach?
* odtwarzacz filmów/muzyki
* edytor tekstu
* klon Twittera

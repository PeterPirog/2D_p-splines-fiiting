
Jesteś specjalistą w zakresie analizy matematycznej, aproksymacji funkcji wielu zmiennych, constrained splines, P-splines, shape-constrained regression oraz projektowania funkcji benchmarkowych do walidacji metod numerycznych.

Twoim zadaniem jest **zaproponowanie matematycznej postaci funkcji benchmarkowej 2D** do artykułu naukowego dotyczącego aproksymacji powierzchni z użyciem constrained splines / constrained P-splines.

Na tym etapie **nie opisuj algorytmu P-splines, procedury optymalizacji, doboru liczby węzłów, macierzy bazowych, metryk błędu, implementacji ani eksperymentu numerycznego**. Cały wysiłek skoncentruj na znalezieniu dobrej funkcji testowej:

$$
z=f(x,y).
$$

Funkcja ma służyć później do walidacji jakości aproksymacji wartości funkcji oraz jej pochodnych pierwszego i drugiego rzędu, ale teraz interesuje mnie przede wszystkim **sama postać matematyczna funkcji benchmarkowej**.

---

## 1. Dziedzina funkcji

Funkcja ma być określona w kartezjańskim układzie współrzędnych na prostokątnym obszarze:

$$
x\in[a_x,b_x],
\qquad
y\in[a_y,b_y].
$$

Zakres zmiennej $x$ musi zawierać wartości ujemne i dodatnie, czyli:

$$
a_x<0<b_x.
$$

Zakres zmiennej $y$ ma obejmować wyłącznie wartości dodatnie:

$$
0<a_y<b_y.
$$

W szczególności $y>0$ w całym analizowanym obszarze.

Zaproponuj konkretne wartości przedziałów $[a_x,b_x]$ oraz $[a_y,b_y]$, tak aby funkcja miała wyraźnie różne skale zmienności w osi $x$ i w osi $y$.

---

## 2. Wymagania gładkości i analitycznych pochodnych

Funkcja powinna być co najmniej klasy:

$$
C^2,
$$

a najlepiej klasy:

$$
C^\infty.
$$

Wybierz taką postać funkcji, aby można było analitycznie wyznaczyć:

$$
f(x,y),
$$

$$
\frac{\partial f}{\partial x},
\qquad
\frac{\partial f}{\partial y},
$$

oraz:

$$
\frac{\partial^2 f}{\partial x^2},
\qquad
\frac{\partial^2 f}{\partial x\partial y},
\qquad
\frac{\partial^2 f}{\partial y^2}.
$$

Pochodne te mają później służyć jako wartości referencyjne, czyli true values, podczas walidacji aproksymacji.

---

## 3. Warunek przejścia przez zero

Funkcja musi przechodzić przez zero wzdłuż całej prostej $x=0$, czyli musi spełniać warunek:

$$
f(0,y)=0
$$

dla każdego:

$$
y\in[a_y,b_y].
$$

Nie chodzi o pojedynczy punkt zerowy, ale o całą linię zerową w dziedzinie.

Uwzględnij ten warunek w konstrukcji funkcji. Szczególnie rozważ rodziny funkcji typu:

$$
f(x,y)=xq(x,y),
$$

ale pamiętaj, że sama postać $xq(x,y)$ nie gwarantuje jeszcze monotoniczności względem $x$.

---

## 4. Warunek monotoniczności względem $x$

Funkcja ma być monotonicznie rosnąca względem zmiennej $x$, najlepiej ściśle monotoniczna. Oczekiwany warunek to:

$$
\frac{\partial f}{\partial x}(x,y)>0
$$

dla każdego punktu:

$$
(x,y)\in[a_x,b_x]\times[a_y,b_y].
$$

Jeżeli zaproponujesz funkcję postaci:

$$
f(x,y)=xq(x,y),
$$

to sprawdź warunek:

$$
\frac{\partial f}{\partial x}
=
q(x,y)+x\frac{\partial q}{\partial x}(x,y)>0.
$$

Nie wystarczy intuicyjnie stwierdzić, że funkcja jest rosnąca. Trzeba podać warunki na parametry, które gwarantują monotoniczność w całej dziedzinie.

---

## 5. Różne skale w osiach $x$ i $y$

Funkcja powinna mieć anizotropową strukturę, czyli różne skale zmienności względem $x$ i $y$.

W szczególności funkcja powinna pokazywać, że:

- zmienność względem $x$ może być monotoniczna, ale nieliniowa;
- zmienność względem $y$ może zawierać oscylacje, garby, doliny lub lokalne zmiany krzywizny;
- skala zmian w kierunku $x$ i $y$ nie powinna być taka sama;
- funkcja nie powinna być zbyt prosta ani prawie liniowa.

---

## 6. Nietrywialna geometria powierzchni

Funkcja powinna zawierać nietrywialną strukturę geometryczną powierzchni:

- nieliniowość,
- zmienną krzywiznę,
- lokalne obszary łagodnej i silniejszej zmienności,
- co najmniej jeden składnik interakcyjny zależny jednocześnie od $x$ i $y$,
- strukturę umożliwiającą sensowną ocenę pochodnych pierwszego i drugiego rzędu.

Unikaj funkcji zbyt prostych, takich jak:

$$
f(x,y)=ax,
$$

$$
f(x,y)=ax+by+c,
$$

albo czysto addytywnych postaci:

$$
f(x,y)=g(x)+h(y),
$$

jeżeli nie spełniają warunku:

$$
f(0,y)=0
$$

i nie zawierają istotnej interakcji między $x$ oraz $y$.

---

## 7. Maksimum i minimum w analizowanym zakresie

Chciałbym, aby funkcja posiadała co najmniej jedno maksimum i jedno minimum w analizowanym zakresie.

Najpierw oceń jednak, czy ten warunek jest matematycznie zgodny z globalną monotonicznością względem $x$, czyli z warunkiem:

$$
\frac{\partial f}{\partial x}>0.
$$

Jeżeli funkcja jest ściśle rosnąca względem $x$, to klasyczne wewnętrzne lokalne maksimum lub minimum pełnej funkcji 2D może być niemożliwe, ponieważ w takim punkcie musiałoby zachodzić:

$$
\nabla f=0,
$$

a to byłoby sprzeczne z:

$$
\frac{\partial f}{\partial x}>0.
$$

Nie ignoruj tej potencjalnej sprzeczności. Wyjaśnij ją krótko i zaproponuj matematycznie poprawną interpretację warunku maksimum i minimum, na przykład:

1. maksimum i minimum globalne występujące na brzegu dziedziny;
2. maksimum i minimum przekrojów:

$$
f(x_0,y)
$$

dla ustalonego $x_0$;

3. maksimum i minimum względem $y$ przy ustalonej wartości $x$;
4. maksimum i minimum składnika modulującego względem $y$;
5. grzbiety i doliny powierzchni przy zachowanej monotoniczności względem $x$;
6. punkty ekstremalnej krzywizny zamiast klasycznych ekstremów lokalnych pełnej funkcji 2D.

Zaproponuj funkcję tak, aby warunek maksimum i minimum był sformułowany matematycznie spójnie z monotonicznością względem $x$.

---

## 8. Preferowane rodziny funkcji

Rozważ w szczególności funkcje o strukturze:

$$
f(x,y)=xq(x,y),
$$

gdzie $q(x,y)$ jest dodatnią, gładką funkcją modulującą, dobraną tak, aby:

$$
f(0,y)=0
$$

oraz:

$$
\frac{\partial f}{\partial x}>0.
$$

Możesz rozważyć funkcje typu:

$$
f(x,y)
=
x\left[
c
+
\alpha \tanh(\beta x)
+
\varepsilon \sin(\omega y)
+
\eta \cos(\nu y)
+
\rho \sin(\omega y)\tanh(\beta x)
\right],
$$

ale tylko wtedy, gdy potrafisz dobrać parametry tak, aby zachować monotoniczność względem $x$.

Możesz też rozważyć funkcje typu:

$$
f(x,y)
=
T(x)
+
xA(x)O(y),
$$

gdzie:

$$
T(0)=0,
$$

oraz składnik $xA(x)O(y)$ również znika dla $x=0$.

Dopuszczalne są składniki zbudowane z funkcji:

$$
\sin,
\quad
\cos,
\quad
\tanh,
\quad
\exp,
\quad
\log(1+\exp(\cdot)),
\quad
\text{wielomianów niskiego stopnia},
\quad
\text{anizotropowych funkcji Gaussa}.
$$

Jeżeli używasz składników gaussowskich, zadbaj o to, aby funkcja nadal spełniała warunek:

$$
f(0,y)=0
$$

oraz:

$$
\frac{\partial f}{\partial x}>0.
$$

---

## 9. Oczekiwany wynik

Zaproponuj co najmniej **pięć kandydackich funkcji benchmarkowych**, ale szczegółowo omów tylko **trzy najlepsze**.

Dla każdej z trzech najlepszych funkcji podaj:

### 9.1. Jawny wzór

Podaj pełną postać:

$$
f(x,y)=\ldots
$$

### 9.2. Dziedzinę

Podaj konkretne wartości:

$$
x\in[a_x,b_x],
\qquad
y\in[a_y,b_y],
$$

przy czym:

$$
a_x<0<b_x,
\qquad
0<a_y<b_y.
$$

### 9.3. Interpretację składników

Wyjaśnij krótko:

- który składnik zapewnia przejście przez zero dla $x=0$,
- który składnik zapewnia monotoniczność względem $x$,
- który składnik odpowiada za zmienność względem $y$,
- który składnik odpowiada za anizotropię,
- który składnik odpowiada za interakcję między $x$ i $y$,
- gdzie pojawiają się garby, doliny, oscylacje lub zmienna krzywizna.

### 9.4. Weryfikację warunku zerowego

Pokaż jawnie, że:

$$
f(0,y)=0
$$

dla każdego:

$$
y\in[a_y,b_y].
$$

### 9.5. Weryfikację monotoniczności

Podaj:

$$
\frac{\partial f}{\partial x}
$$

oraz warunki na parametry, które gwarantują:

$$
\frac{\partial f}{\partial x}>0
$$

w całej dziedzinie.

### 9.6. Informację o maksimach i minimach

Wyjaśnij, w jakim sensie funkcja posiada maksimum i minimum:

- jako maksimum i minimum globalne na brzegu dziedziny,
- jako ekstrema przekrojów względem $y$,
- jako ekstrema składnika oscylacyjnego,
- jako grzbiety i doliny,
- albo jako punkty ekstremalnej krzywizny.

Nie twierdź, że funkcja ma klasyczne wewnętrzne lokalne maksimum lub minimum pełnej powierzchni, jeżeli jest to sprzeczne z monotonicznością względem $x$.

### 9.7. Dostępność pochodnych

Potwierdź, że dla zaproponowanej funkcji można analitycznie wyznaczyć:

$$
\frac{\partial f}{\partial x},
\qquad
\frac{\partial f}{\partial y},
\qquad
\frac{\partial^2 f}{\partial x^2},
\qquad
\frac{\partial^2 f}{\partial x\partial y},
\qquad
\frac{\partial^2 f}{\partial y^2}.
$$

Nie musisz bardzo szczegółowo rozwijać wszystkich długich wzorów, ale funkcja musi być tak dobrana, aby pochodne były jednoznaczne, zamknięte analitycznie i możliwe do użycia jako true values.

### 9.8. Uzasadnienie przydatności benchmarkowej

Wyjaśnij, dlaczego dana funkcja jest dobrym benchmarkiem do testowania aproksymacji:

$$
f(x,y),
$$

gradientu:

$$
\nabla f,
$$

oraz hesjanu:

$$
H_f.
$$

---

## 10. Ograniczenia odpowiedzi

Nie opisuj:

- jak dobrać liczbę węzłów P-splines,
- jak dobierać parametry wygładzania,
- jak optymalizować współczynniki,
- jak budować macierze bazowe,
- jak definiować funkcję celu,
- jak liczyć RMSE,
- jak generować dane treningowe,
- jak implementować eksperyment w Pythonie.

Skoncentruj się wyłącznie na:

$$
\text{postaci funkcji benchmarkowej}
$$

oraz jej matematycznym uzasadnieniu.

---

## 11. Wybór końcowy

Na końcu wybierz jedną funkcję jako najlepszą kandydatkę do artykułu naukowego.

Uzasadnij wybór wyłącznie z punktu widzenia właściwości matematycznych funkcji:

- spełnienia warunku $f(0,y)=0$,
- monotoniczności względem $x$,
- obecności dodatnich i ujemnych wartości $x$,
- dodatniego zakresu zmiennej $y$,
- anizotropii,
- bogactwa geometrycznego powierzchni,
- obecności maksimum i minimum w matematycznie poprawnym sensie,
- zmiennej krzywizny,
- obecności interakcji między $x$ i $y$,
- łatwości analitycznego różniczkowania,
- przejrzystości zapisu w publikacji naukowej.

Odpowiedź przygotuj w stylu naukowym, z użyciem zapisu LaTeX. Jeżeli którykolwiek z wymogów jest matematycznie sprzeczny z innym, wskaż to jawnie i zaproponuj poprawną interpretację warunku.

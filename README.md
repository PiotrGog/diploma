# Praca dyplomowa w `latex`

Do pisania pracy użyj [Overleaf](https://www.overleaf.com).

Kod oraz wygenerowany tekst można sprawdzić pod [linkiem](https://www.overleaf.com/read/ptsdvrwfwgpg#1069b1).

## 1. Definiowanie podstawowych informacji pracy
### W pliku `mgr.cls` odszukaj:
```
\newif\if@eng \@engfalse
\newif\if@lic \@licfalse
```

1. Jeśli piszesz pracę magisterską - nie zmieniaj,
2. Jeśli piszesz pracę inżynierską - zmień na:
```
\newif\if@eng \@engtrue
\newif\if@lic \@licfalse
```
3. Jeśli piszesz pracę licencjacką - zmień na:
```
\newif\if@eng \@engfalse
\newif\if@lic \@lictrue
```

### W pliku `title_page.tex` zdefiniuj odpowiednie pola:
```
\title{Polski tytuł}
\engtitle{Angielski tytuł}
\author{Autor}

\university{
	NAZWA UCZELNI\\[0mm]%
	NAZWA WYDZIAŁU%
	\vspace{-6mm}%
}

\field{Kierunek studiów}
\specialisation{Specjalizacja kierunku}

\supervisor{
	Promotor\\%
	Wydział/Katedra%
}
```

## 2. Definiowanie rozdziału (punkt_2.tex)
1. Utwórz nowy plik `nazwa_pliku.tex` w katalogu `chapters`
2. W pliku `main.tex` dodaj w `\includeonly`:
```
chapters/nazwa_pliku
```
3. Żeby dodać zawartość pliku do spisu treści, w pliku `main.tex` pod `\tableofcontents` dodaj:
```
\include{chapters/nazwa_pliku}
```
4. W pliku `nazwa_pliku.tex` zdefiniuj rozdział
```
\chapter{Nowy rozdział}
```

### Dodawanie nowego podrozdziału
W pliku `nazwa_pliku.tex` dodaj
```
\section{nazwa_podrozdziału}
```

> W celu definiowania pod-podrozdziałów, pod-pod-podrozdziałów itd. użyj komend `\subsection{nazwa podrozdziału}`, `\subsubsection{nazwa pod-podrozdziału}`.

## 3. Definiowanie rozdziału bez numeru (punkt_3.tex)
1. Utwórz nowy plik `nazwa_pliku.tex` w katalogu `chapters`
2. W pliku `main.tex` dodaj w `\includeonly`:
```
chapters/nazwa_pliku
```
3. Żeby dodać zawartość pliku do spisu treści, w pliku `main.tex` pod `\tableofcontents` dodaj:
```
\include{chapters/nazwa_pliku}
```
4. W pliku `nazwa_pliku.tex` zdefiniuj rozdział
```
\chapter*{nazwa_rozdziału}
\addcontentsline{toc}{chapter}{nazwa_rozdziału}
```
### Dodawanie nowego podrozdziału
W pliku `nazwa_pliku.tex` dodaj
```
\section*{nazwa_podrozdziału}
```

> W celu definiowania pod-podrozdziałów, pod-pod-podrozdziałów itd. użyj komend `\subsection*{nazwa podrozdziału}`, `\subsubsection*{nazwa pod-podrozdziału}`.

## 4. Dodawanie grafiki (punkt_4.tex)
[https://www.overleaf.com/learn/latex/Inserting_Images](https://www.overleaf.com/learn/latex/Inserting_Images)

1. W katalogu `figures` dodaj plik z grafiką,
2. W tekście dodaj grafikę za pomocą polecenia `\addimage`,
3. W tekście możesz odwołać się do grafiki za pomocą polecenia `\myref`

```
Na rys.\myref{odnośnik} widoczny jest przedmiot... 
\addimage{wielkość_grafiki}{figures/nazwa_pliku}{opis_grafiki}{odnośnik}
```
> `wielkość_grafiki` - dopuszczalny zakres wartości: 0.0-1.0

## 5. Dodawanie listy (punkt_5.tex)
[https://www.overleaf.com/learn/latex/Lists](https://www.overleaf.com/learn/latex/Lists)

### Lista nieuporządkowana
```
\begin{itemize}
	\item punkt_pierwszy
	\item punkt_drugi
\end{itemize}
```
rezultat:
* punkt_pierwszy
* punkt_drugi

### Lista uporządkowana
```
\begin{enumerate}
	\item punkt_pierwszy
	\item punkt_drugi
\end{enumerate}
```
rezultat:
1. punkt_pierwszy
2. punkt_drugi

## Dodawanie bibliografii i przypisów (punkt_6.tex)
[https://www.overleaf.com/learn/latex/Bibliography_management_in_LaTeX](https://www.overleaf.com/learn/latex/Bibliography_management_in_LaTeX)

W pliku `bibliography.bib` zdefiniuj pozycje, np.:
```
@article{einstein,
    author =       "Albert Einstein",
    title =        "{Zur Elektrodynamik bewegter K{\"o}rper}. ({German})
    [{On} the electrodynamics of moving bodies]",
    journal =      "Annalen der Physik",
    volume =       "322",
    number =       "10",
    pages =        "891--921",
    year =         "1905",
    DOI =          "http://dx.doi.org/10.1002/andp.19053221004",
    keywords =     "physics"
}

@book{dirac,
    title={The Principles of Quantum Mechanics},
    author={Paul Adrien Maurice Dirac},
    isbn={9780198520115},
    series={International series of monographs on physics},
    year={1981},
    publisher={Clarendon Press},
    keywords = {physics}
}

@online{knuthwebsite,
    author    = "Donald Knuth",
    title     = "Knuth: Computers and Typesetting",
    url       = "http://www-cs-faculty.stanford.edu/~uno/abcde.html",
    keywords  = "latex,knuth"
}

@inbook{knuth-fa,
    author = "Donald E. Knuth",
    title = "Fundamental Algorithms",
    publisher = "Addison-Wesley",
    year = "1973",
    chapter = "1.2",
    keywords  = "knuth,programming"
}
```

### Odniesienie do literatury
W tekście odnieś się do zdefiniowanej literatury za pomocą ich identyfikatorów:
```
\mycite{identyfikator}
```
### Przypis na dole strony
Użyj polecenia 
```
\footnote{tekst przypisu na dole strony}
```

## Modyfikacja czcionki (punkt_7.tex)
[https://www.overleaf.com/learn/latex/Font_sizes%2C_families%2C_and_styles](https://www.overleaf.com/learn/latex/Font_sizes%2C_families%2C_and_styles)
[https://www.overleaf.com/learn/latex/Bold%2C_italics_and_underlining](https://www.overleaf.com/learn/latex/Bold%2C_italics_and_underlining)

### Pogrubienie
```
\textbf{pogrubiony}
```

### Pochylenie
```
\textit{pochylony}
```

### Podkreślenie
```
\underline{podkreślony}
```

### Hiperłącze
```
\href{adres_strony}{widoczny_tekst}
```

### Cytat
```
\enquote{tekst_w_cudzysłowie}
```

Rodzaje modyfikacje można mieszać zagnieżdżając je.
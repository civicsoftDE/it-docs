# Streams

## Herleitung

Gegeben sei die mathematische Funktion $f(x) = \sin\big((x + 1)^2\big)$ mit $x \in \mathbb R | x > 0 $.

Dann könnten wir auch schreiben:

\begin{equation}\label{example_1}
\begin{array}[b]{rll}
\text{Bedingung: } x &> 0 \\\
a &= x + 1 \\\
b &= a^2 \\\
c &= \sin(b)
\end{array}
\end{equation}

In Java können wir diesen Algorithmus mithilfe von Streams abbilden. Als Parameter übergeben wir eine Liste von $x$-Werten (_Parameter_)
und erhalten als Ergebnis eine Liste von $f(x)$-Werten (_Funktionswerte_).

````java
public static List<Double> runMathFunction(List<Double> values) {
    return values.stream()
            .filter(x -> x > 0)
            .map(x -> x + 1)
            .map(x -> x * x)
            .map(Math::sin)
            .collect(Collectors.toList());
}
````

> **Hinweis**: Die Reihenfolge der `.map()`-Operationen entspricht exakt der Funktionskomposition $f(x) = \sin\big((x + 1)^2\big)$, was das Stream-Paradigma zur natürlichen Entsprechung mathematischen Denkens macht.

## Adressen

Angenommen, wir wollen eine Textdatei mit Adressen einlesen, wobei jede Zeile aus

- Postleitzahl
- Ort
- Straßenname
- Hausnummer

besteht, wie zum Beispiel:

````text
10587 Berlin Hardenbergstraße 16
69120 Heidelberg Im_Neuenheimer_Feld 368
80333 München Boltzmannstraße 3
76131 Karlsruhe Adenauerring 2
64289 Darmstadt Hochschulstraße 10
38678 Clausthal Julius-Albert-Straße 2
28359 Bremen Enrique-Schmidt-Straße 5
14482 Potsdam August-Bebel-Straße 89
13353 Berlin Luxemburger_Straße 10
````

dann können wir folgenden Algorithmus anwenden, wenn wir annehmen, dass

- je Zeile eine Adresse
- jede Adresse vier Komponenten

enthält.

**Pseudo-Code:**

\begin{equation}\label{example_2}
\begin{array}[b]{rll}
\text{Anweisung} &\text{Tupel an Umbruch trennen} \\\
\text{Bedingung} &\text{Zeilenlänge} > 0 \\\
\text{Anweisung} &\text{Abschnitte an Leerzeichen trennen} \\\
\text{Bedingung} &\text{Menge von}\ L = 4 \\\
L &= \\{x1, x2, x3, x4\\} \\\
\text{Adresse} &= createAdresse(L) \\\
\text{Ausgabe} &= \text{Erste gültige Adresse oder nichts}
\end{array}
\end{equation}

**JAVA-Code:**

````java
public static Adresse createAdresse(Scanner in) {
        return in.useDelimiter("\\R").tokens()
                .map(String::trim)
                .filter(s -> !s.isEmpty())
                .map(line -> line.split("\\s+"))
                .filter(parts -> parts.length == 4)
                .map(AddressPlay::createAdresse)
                .findFirst()
                .orElse(null);
    }

public static Adresse createAdresse(String[] parts) {
    int plz = Integer.parseInt(parts[0]);
    String city = parts[1];
    String street = parts[2];
    int streetNumber = Integer.parseInt(parts[3]);
    
    return new Adresse(plz, city, street, streetNumber);
}
````
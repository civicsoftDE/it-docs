# Logik

## Einleitung

**Beispiele für logisch nachvollziehbare Sprache**:

Differenzierbare Funktion:
$f: [a,b] \to \mathbb{R}$

$m$ ist Teiler von $m$: $m|n$

Eine Aussage $A$ ist ein sprachliches Gebilde, welches einen der beiden Wahrheitswerte **wahr** ($W$) oder
**falsch** ($F$) hat.

## Symbole

| Zeichen                     | $\LaTeX$                | Name        | Bedeutung                     |
|-----------------------------|-------------------------|-------------|-------------------------------|
| $\land$                     | \land                   | Konjunktion | Und-Verknüpfung               |
| $\overline\land$            | \overline\land          | Konjunktion | Nicht-Und-Verknüpfung         |
| $\lor$                      | \lor                    | Disjunktion | Oder-Verknüpfung (inklusiv)   |
| $\veebar$ bzw. $\dot\lor$   | \veebar bzw. \dot\lor   | Disjunktion | Oder-Verknüpfung (exklusiv)   |
| $\lnot$ bzw. $\overline{A}$ | \lnot bzw. \overline{A} | Negation    | Verneinung                    |
| $\iff$                      | \iff                    | Äquivalenz  | Übereinstimmung               |
| $\implies$                  | \implies                | Implikation | hinreichende Schlussfolgerung |

### Wahrheitstabelle

| $A$ | $B$ | $\overline{A}$ | $A \land B$ | $A \lor B$ | $A \dot\lor B$ | $A \iff B$ | $A \implies B$ |
|-----|-----|----------------|-------------|------------|----------------|------------|----------------|
| $W$ | $W$ | $F$            | $W$         | $W$        | $F$            | $W$        | $W$            |
| $W$ | $F$ | $F$            | $F$         | $W$        | $W$            | $F$        | $F$            |
| $F$ | $W$ | $W$            | $F$         | $W$        | $W$            | $F$        | $W$            |
| $F$ | $F$ | $W$            | $F$         | $F$        | $F$            | $W$        | $W$            |


## Sprache

$A \iff B$ heißt: $A$ ist äquivalent zu $B$ bzw. $B$ ist äquivalent zu $A$

**Beispiel**

- $A$: $12$ ist positiv.
- $B$: $12 $ ist durch $4 $ teilbar.
- $12 $ ist positiv **genau dann, wenn** $12 $ durch $4 $ teilbar ist.

## Regeln

### Hierarchie

1. $\lnot A$ bzw. $\overline{A}$
2. $A \land B$
3. $A \lor B$

### Allgemein

$\overline{(\overline{A})} \iff A$

$A \lor A \iff A$

$A \land A \iff A$

$A \land B \iff B \land A$

$A \lor B \iff B \lor A$

$(A \lor B) \lor C \iff A \lor (B \lor C)$

$A \land (B \lor C) \iff (A \land B) \lor (A \land C)$

$A \lor (B \land C) \iff (A \lor B) \land (A \lor C)$

### Morgan'sche Regeln

$\overline{(A \lor B)} \iff \overline{A} \land \overline{B}$

$\overline{(A \land B)} \iff \overline{A} \lor \overline{B}$

$A \implies B \iff \overline{A} \lor B$

$\overline{(A \implies B)} \iff A \land \overline{B}$

$(A \iff B) \iff ((A \implies B) \land (B \implies A))$


### Kontraposition

$(A \implies B) \iff (\overline{B} \implies \overline{A})$

**Beispiel**: Wenn es regnet ($A$), ist die Straße nass ($B$).

### NAND

#### Negation

\begin{flalign}
\overline{A} &= A \overline{\land}  A & \\\
\overline{B} &= B \overline{\land}  B &
\end{flalign}

#### Und-Verknüpfung

\begin{flalign}
A \land B &= (A \overline{\land} B) \overline{\land} (A \overline{\land} B) &&
\end{flalign}

#### Oder-Verknüpfung

\begin{flalign}
A \lor B &= (A \overline{\land} A) \overline{\land} (B \overline{\land} B) &&
\end{flalign}

## Aussageformen

Konstanten können durch Variablen ersetzt werden. Dann entsteht eine Aussageform. Werden Variablen
durch Konstanten ersetzt, entsteht eine Aussage, die wahr oder falsch ist.

**Beispiel:**

$A(x): x \geq 10$

$A(1): 1 \geq 10 \iff (F)$

### Quantoren

- $\exists Z(k) \lor N(k) \iff \exists Z(k) \lor \exists N(k)$
- $\exists Z(k) \land N(k) \implies \exists Z(k) \lor \exists N(k)$


- $\forall Z(k) \land N(k) \iff \forall Z(k) \lor \forall N(k)$
- $\forall Z(k) \lor \forall N(k) \implies \forall Z(k) \lor N(k)$

### Negation von Quantoren

#### Negation der All-Aussage

$V(m, n) :$ m ist ein Vielfaches von n

_"Jedes $m\in\mathbb{N}$ das kein Vielfaches von 5 ist, ist ein Vielfaches von 2 oder 3."_

$\forall \lnot V(m, 5) \to V(m,2) \lor V(m, 3)$

**Gegenbeispiel:**
\begin{flalign}
&\lnot\bigl( \forall \lnot V(m, 5) \to V(m,2) \lor V(m, 3) \bigr) & |\text{de-Morgan (Implizit)} \\\
\iff &\exists \lnot \bigl( V(m, 5) \lor V(m,2) \lor V(m, 3) \bigr) \\\
\iff &\exists \lnot V(m, 5) \land \lnot V(m,2) \land \lnot V(m, 3)  \\\
\end{flalign}

Zum Beispiel: $m = 7 $

##### Beispiel

Gegeben seien der Definitionsbereich $B\ \\{1,2,3,4,5,6,7,8,9\\}$ und die Aussage $P(x,y): x + y = 10 $.

Dann gilt: $\exists_y \forall_x P(x,y) \implies \forall_x \exists_y P(x, y)$

Anders ausgedrückt: _"Wenn es regnet, ist die Straße nass. Wenn es nicht regnet, kann die Straße trotzdem nass sein.
Wenn die Straße trocken ist, obwohl es regnete, stimmt etwas nicht."_

| Es regnet | Die Straße ist nass | Ergebnis |
|-----------|---------------------|----------|
| 1         | 0                   | 0        |   
| 0         | 1                   | 1        |
| 1         | 1                   | 1        |
| 0         | 0                   | 1        |

Warum kann die Straße nun nass sein, obwohl es nicht geregnet hat?
**Vielleicht hat jemand mit einem Gartenschlauch die Straße nass gemacht**.

Andersherum: **Wenn die Straße trocken ist, kann es auf keinen Fall geregnet haben.**

#### Negation der Existenz-Aussage



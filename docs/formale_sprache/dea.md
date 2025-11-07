# Deterministische endliche Automaten

## Mealy-Automaten

Ein Mealy Automat ist ein endlicher Automat, der sich durch eine Besonderheit auszeichnet: Die Ausgaben sind nicht nur vom aktuellen Zustand abhängig, sondern auch vom aktuellen Eingabewert. Dies unterscheidet ihn von anderen Automatenarten, wie dem Moore-Automaten, bei dem die Ausgabe ausschließlich vom Zustand abhängig ist.

### Formale Definition

$A=(X,Y,Z,\delta,z_0)$

- $X$ Eingabealphabet
- $Y$ Ausgabealphabet
- $Z$ Zustandsmenge
- $\phi: Z \times X \rightarrow Z \times Y$ Überführungs- und Ausgabefunktion
- $z_0$ Startzustand

### Überführungsfunktion

Zustand / Eingabe | $0$ | $1$
--------|---------|------------------
$z_0$  |   $z_0$   |      $z_1$
$z_1$   |   $z_1$  |      $z_0$

### Ausgabefunktion

Zustand / Eingabe | $0$ | $1$
--------|---------|------------------
$z_0$ |   $0$   |      $1$
$z_1$   |   $0$  |      $1$

### Impulsdiagramm

Zustand | Eingabe | Nächster Zustand | Ausgabe
--------|---------|------------------|--------
$z_0$  |   $0$   |      $z_0$      |   $0$
$z_0$   |   $1$   |      $z_1$       |   $1$
$z_1$   |   $0$   |      $z_1$       |   $0$
$z_1$   |   $1$   |      $z_0$      |   $1$

## Pumping-Lemma

Die Gültigkeit des Lemmas basiert darauf, dass es zu jeder regulären Sprache einen deterministischen endlichen Automaten gibt, der die Sprache akzeptiert. Über einem endlichen Alphabet enthält eine reguläre Sprache mit unendlich vielen Wörtern auch solche Wörter, die mehr Zeichen enthalten als der Automat Zustände hat. Zum Akzeptieren solcher Wörter muss der Automat also einen Zyklus enthalten, der dann in beliebiger Häufigkeit durchlaufen werden kann. Die Buchstabenfolge, die beim Durchlaufen des Zyklus gelesen wird, kann also entsprechend beliebig oft in Wörtern der Sprache vorkommen.

![img.png](/docs/img/pumping_lemma.png)

### Praktisches Beispiel

![img.png](/docs/img/dea_email.png)

Ausgedrückt in Formaler Sprache (BNF):

````php
email    -> local "@" domain "." tld ;
local    -> label { "." label } ;
domain   -> label { "." label } ;
label    -> letter { letter } ;
letter   -> "a" | "b" | ... | "z" | "A" | ... | "Z" ;
tld      -> "de" | "com" ;
````
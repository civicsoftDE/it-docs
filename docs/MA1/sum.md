# Summen

## Zahlensysteme

Eine Zahl $x$ des Zahlensystems der Basis $b$ lässt sich mit der Stelle $d$ als die Summe

$$ x = \sum_{i=1}^{n} d_i \cdot b^{n-i}  $$

darstellen.

### Beispiel

Die vierstellige Dezimalzahl $x = 1024_{10} $ mit $b=10$ lässt sich darstellen als:

$$ 1024 = \sum_{i=1}^{4} d_i \cdot b^{4-i} = 1 \cdot 10^3 + 0 \cdot 10^2 + 2 \cdot 10^1 + 4 \cdot 10^0 $$

Die Dezimalzahl $x = 9 $ lässt sich darstellen als vierstellige Binärzahl $1001_2$ mit $b=2 $ als:

$$ 1001 = \sum_{i=1}^4 d_i \cdot b^{4-i} = 1 \cdot 2^3 + 0 \cdot 2^2 + 0 \cdot 2^1 + 1 \cdot 2^0 $$

## Gaußsche Summenformel

### Vollständige Summen

$$ 1+2+3+\text{...}+(n-1)+n = \sum_{k=1}^{n} k = \frac{n(n+1)}{2} $$

### Teilsummen

$$
\sum_{k=10}^{100}k = \sum_{k=1}^{100}k - \sum_{k=1}^{9}k 
$$

### Gerade Zahlen

Die Summe der ersten n geraden Zahlen:

$$ 2+4+6+\text{...}+2(n-1)+2n = \sum_{k=1}^n 2k = 2 \cdot \frac{n(n+1)}{2} = n(n+1) $$

### Ungerade Zahlen

Die Summe der ersten n ungeraden Zahlen:

$$
\begin{equation}\label{uneven_nr}
\begin{array}[b]{rll}
1+3+5+\text{...}+(2(n-1)-1)+(2n-1) &= \sum_{k=1}^n (2k-1) \\\
&= 2 \sum_{k=1}^n k - \sum_{k=1}^n 1 \\\
&= (n^2+n)-n \\\
&= n^2
\end{array}
\end{equation}
$$ 

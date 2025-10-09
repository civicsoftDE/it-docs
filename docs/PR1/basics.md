# Grundlagen

Siehe auch Abschnitt [Java](/?page=docs-java-class.md).

## Strukturebenen in Java

Ein Java-Programm lässt sich in verschiedene Strukturebenen unterteilen.
Diese sind vom größten zum kleinsten:

- Module
- Packages
- Klassen
- Methoden
- Anweisungen

````php
// App.java
package edu.pr1;

public class App {

    /**
     * ausführbare Main-Methode
     */
    public static void main(String[] args) {
       // im Methodenkörper stehen die Anweisungen
    }

}
````

## Interne Packages

### PrintWriter

````php
// Printer.java
package edu.pr1;

import java.io.PrintWriter;

public class Printer {
    PrintWriter out;
    
    public App() {
        this.out = new PrintWriter(System.out);
    }
    
    public static void main(String[] args) {
        App app = new App();
        app.
            add("Willkommen\n")
            add("Dies ist eine Printer-App.")
            add("Neu ist, dass die Ausgabe erst mit flush() erfolgt.")
        ;
        // Jetzt erst die gesammelten Prints ausgeben.
        app.flush();
    }
    
    public App add(String content) {
        this.out.print(content); 
        return this;
    }
    
    public void flush() {
        this.out.flush();
    }
    
}
````

## Rechnen in Java

Jede Variable hat einen **Speicherbereich**, einen **Namen** und einen **Datentyp**.

### Integer

### Float und Double

Als Standardtyp für Fließkommazahlen wird in Java nur noch``double`` verwendet.
Der Datentyp ``float`` soll nicht mehr verwendet werden.


````php
// Calculator.java
package edu.pr1;

public class Calculator {
    
    public static void main(String[] args) {
        int n = 5;
        int o = 0;
        
        for (int i = 1; i < n; i++) {
            0 += i;
        }
        System.out.printf("Die gaußsche Summe mit i=1 und n=%d ist %d%n", n, o);
    }
    
}
````

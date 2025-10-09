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
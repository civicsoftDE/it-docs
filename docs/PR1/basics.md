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



### FancyFileWriter

````php
package pr1.helper;

import java.io.File;
import java.io.FileNotFoundException;
import java.io.PrintWriter;

/**
 * 
 */
public class FancyFileWriter {

	private PrintWriter fout;
	private String separator = System.getProperty("file.separator");
	private String targetPath = System.getProperty("user.home");
	private String targetFile;

	public FancyFileWriter(String file) {
		setTargetFile(file);
		try {
			this.fout = new PrintWriter(targetPath + separator + targetFile);
		} catch (FileNotFoundException e) {
			System.err.println("Datei kann nicht erstellt werden!");
		}
	}

	public FancyFileWriter(String path, String file) {
		setTargetFile(file);
		File subPath = new File(targetPath + separator + path);
		if (!subPath.exists()) {
			subPath.mkdirs();
		}
		targetPath = subPath.getAbsolutePath();
		try {
			this.fout = new PrintWriter(targetPath + separator + targetFile);
		} catch (FileNotFoundException e) {
			System.err.println("Datei kann nicht erstellt werden!");
		}

	}

	public PrintWriter getWriter() {
		return this.fout;
	}

	public void close() {
		this.fout.close();
	}

	private FancyFileWriter setTargetFile(String file) {
		this.targetFile = file;
		return this;
	}

}
````

### FancyPrinter

````php
package pr1.helper;

import java.io.PrintWriter;

public class FancyPrinter {

	public char frameChar = '#';
	public PrintWriter out;

	public FancyPrinter(PrintWriter out) {
		this.out = out;
	}

	public FancyPrinter(PrintWriter out, char frameChar) {
		this.out = out;
		this.frameChar = frameChar;
	}

	/**
	 * Rahmen erzeugen, der so breit ist wie der Eingabetext (mit Padding und
	 * bottom-Margin von 1).
	 * 
	 * @param out  Instanz des PrintWriters
	 * @param text Eingabetext
	 */
	public FancyPrinter printBorder(String text) {
		printBorder(text, 1);
		return this;
	}

	/**
	 * Rahmen erzeugen, der so breit ist wie der Eingabetext (mit Padding und
	 * bottom-Margin von n).
	 * 
	 * @param out           Instanz des PrintWriters
	 * @param text          Eingabetext
	 * @param marginBottomm Anzahl der Zeilenumbrüche am Ende der Ausgabe
	 */
	public FancyPrinter printBorder(String text, int marginBottom) {
		for (int i = -4; i < text.length(); i++) {
			out.print(frameChar);
		}
		for (int i = 0; i < marginBottom; i++) {
			out.printf("%n");
		}
		return this;
	}

	/**
	 * Erzeugt einen Rahmen um einen Text
	 * 
	 * @param out  Instanz des PrintWriters
	 * @param text Eingabetext
	 */
	public FancyPrinter printHeadline(String text) {
		printBorder(text);
		out.printf("%s %s %s%n", frameChar, text, frameChar);
		printBorder(text, 2);
		return this;
	}

}
````



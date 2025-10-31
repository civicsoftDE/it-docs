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

## Übung A02

`````php
/**
 * Copyright (c) 2025 Benjamin Wagner.
 *
 * This program is free software: you can redistribute it and/or modify
 * it under the terms of the GNU Lesser General Public License as published by
 * the Free Software Foundation, either version 3 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU Lesser General Public License for more details.
 *
 * You should have received a copy of the GNU Lesser General Public License
 * along with this program.  If not, see <https://www.gnu.org/licenses/>.
 */
package pr1.a02;

import java.io.PrintWriter;

import pr1.helper.FancyFileWriter;
import pr1.helper.FancyPrinter;

public class Schachbrett {
	public static PrintWriter out = new PrintWriter(System.out);

	public static void main(String[] args) {

		// Gibt schicke Überschriften aus.
		FancyPrinter printer = new FancyPrinter(out);

		// Gibt Output in Datei aus.
		FancyFileWriter fout = new FancyFileWriter("WAGNER/PR1AG/A02", "schach.txt");

		// Schicke Überschriften für die fout-Instanz
		FancyPrinter fPrinter = new FancyPrinter(fout.getWriter());

		// Konsolenausgabe
		printer.printHeadline("Schachbrett, weiß");
		printSchachbrett();
		out.println();
		printer.printHeadline("Schachbrett, schwarz");
		printSchachbrettReverse();
		out.println();
		out.flush();

		// Dateiausgabe (HOME-Verzeichnis/demo/schach.txt)
		fPrinter.printHeadline("Schachbrett, weiß");
		fout.getWriter().print(schachbrett());
		fout.getWriter().println();
		fPrinter.printHeadline("Schachbrett, schwarz");
		fout.getWriter().print(schachbrettReverse());
		fout.getWriter().println();
		fout.close();
	}

	/**
	 * Gibt eine mehrzeilige Zeichenkette mit den Bezeichnungen der Felder eines
	 * Schachbretts (A1 - H8) aus.
	 */
	public static void printSchachbrett() {
		out.print(schachbrett());
	}

	/**
	 * Gibt eine mehrzeilige Zeichenkette mit den Bezeichnungen der Felder eines
	 * Schachbretts (A1 - H8) aus Sicht des Spielers mit den schwarzen Figuren aus.
	 */
	public static void printSchachbrettReverse() {
		out.print(schachbrettReverse());
	}

	/**
	 * Erzeugt eine mehrzeilige Zeichenkette mit den Bezeichnungen der Felder eines
	 * Schachbretts (A1 - H8).
	 * 
	 * @return Ergebnis als Zeichenkette
	 */
	public static String schachbrett() {
		return schachbrett(true);
	}

	/**
	 * Erzeugt eine mehrzeilige Zeichenkette mit den Bezeichnungen der Felder eines
	 * Schachbretts (A1 - H8) aus Sicht des Spielers mit den schwarzen Figuren.
	 * 
	 * @return Ergebnis als Zeichenkette
	 */
	public static String schachbrettReverse() {
		return schachbrett(false);
	}

	/**
	 * Erzeugt eine mehrzeilige Zeichenkette mit den Bezeichnungen der Felder eines
	 * Schachbretts (A1 - H8).
	 * 
	 * @param isWhitePlayer Aus Sicht des Spielers mit den weißen Figuren
	 * @return Ergebnis
	 */
	public static String schachbrett(boolean isWhitePlayer) {

		// Variablen deklarieren und ggf. Objekte instantiieren
		StringBuilder result = new StringBuilder();
		StringBuilder rows = new StringBuilder();
		StringBuilder columns = new StringBuilder();
		char[] rowArray;
		char[] columnArray;

		// Werte vorbereiten
		for (char c = 'A'; c <= 'H'; c++) {
			columns.append(c);
		}
		for (int i = 1; i <= 8; i++) {
			rows.append(i);
		}
		if (isWhitePlayer) {
			rows.reverse();
		} else {
			columns.reverse();
		}

		// Iterierbare Arrays erzeugen
		rowArray = rows.toString().toCharArray();
		columnArray = columns.toString().toCharArray();

		// Ausgabe zusammenbauen
		for (char row : rowArray) {
			for (char column : columnArray) {
				result.append(column).append(row).append(' ');
			}

			// letztes Zeichen entfernen und Zeilenvorschub anhängen.
			result.setLength(result.length() - 1);
			result.append("\n");
		}

		// Ergebnis ausliefern
		return result.toString();
	}

	/**
	 * Erzeugt eine Zeichenkette, die die Felder eines Schachbretts darstellt.
	 * 
	 * @deprecated Funktioniert, ist aber kaum nachvollziehbar.
	 * @param isReverse Schachbrett drehen oder nicht
	 * @return Ergebnis
	 */
	public static String schachbrettAlt(boolean isReverse) {
		StringBuilder result = new StringBuilder();

		// 'A' hat den Unicode-Wert 65.
		int charStart = 65;

		// Ein Schachbrett hat 8x8 Felder
		int cells = 8;
		int cellNumber;
		char cellLetter;

		for (int k = 0; k < cells; k++) {
			for (int i = 0; i < cells; i++) {
				if (!isReverse) {

					// A1 ist unten links.
					cellNumber = cells - k;
					cellLetter = (char) (charStart + i);
					result.append(String.format("%s%d", cellLetter, cellNumber));
				} else {

					// A1 ist oben rechts.
					// oberste Zeile für k = 0: 0 + 1 == 1
					cellNumber = k + 1;

					// erste Spalte ist 'H' = 72 ==> für i = 0: 65 + 8 - 0 - 1 == 72
					cellLetter = (char) (charStart + cells - i - 1);

					// Für k = 0 und i = 0 ergibt sich oben links: H1
					result.append(String.format("%s%d", cellLetter, cellNumber));
				}
				if (cells - 1 > i) {
					result.append(" ");
				}
			}
			result.append("\n");
		}
		return result.toString();
	}

}
`````

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



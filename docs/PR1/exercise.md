# Übungen

## Übung A02

`````php
package pr1.a02;

import pr1.helper.FancyFileWriter;
import pr1.helper.FancyPrinter;
import pr1.helper.FileTarget;
import pr1.helper.Range;

import java.io.PrintWriter;

public class Schachbrett {
    public static PrintWriter out = new PrintWriter(System.out);

    public static void main(String[] args) {

        // Gibt schicke Überschriften aus.
        FancyPrinter printer = new FancyPrinter(out);

        // Gibt Output in Datei aus.
        FancyFileWriter fOut = new FancyFileWriter(FileTarget.PROJECT_DIR, "WAGNER/PR1AG/A02", "schach.txt");

        // Schicke Überschriften für die fOut-Instanz
        FancyPrinter fPrinter = new FancyPrinter(fOut.getWriter());

        // Konsolenausgabe
        printer.printHeadline("Schachbrett, weiß");
        printSchachbrett();
        out.println();
        printer.printHeadline("Schachbrett, schwarz");
        printSchachbrettReverse();
        out.println();
        out.flush();

        // Dateiausgabe (Projekt-Verzeichnis/WAGNER/PR1AG/A02/schach.txt)
        fPrinter.printHeadline("Schachbrett, weiß");
        fOut.getWriter().print(schachbrett());
        fOut.getWriter().println();
        fPrinter.printHeadline("Schachbrett, schwarz");
        fOut.getWriter().print(schachbrettReverse());
        fOut.getWriter().println();
        fOut.close();
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
        for (char c : new Range('A', 'H')) {
            columns.append(c);
        }
        for (int i : new Range(1, 8)) {
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

}
`````
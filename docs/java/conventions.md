# Code Konventionen

## Quelldateien
### Dateinamen

Dateinamen werden in **PascalCase** notiert. Z. B.: ``MyClass.java``. Jedes Wort beginnt mit einem
Großbuchstaben. Ziffern sollten nicht am Anfang stehen.

### Klassennamen

Klassennamen entsprechen dem Dateinamen (ohne Suffix). Eine Datei darf nur eine einzelne **Klasse**, **Enum** oder **Interface**
enthalten.

````java
package my.pkg;

public class MyClass {
    // Klassenrumpf
}
````

### Dateigröße

Eine Java-Klasse sollte niemals länger als 2000 Zeilen beinhalten.

Die Zeilenlänge sollte 80 Zeichen nicht überschreiten. Java-Doc-Kommentare sollten 70 Zeichen nicht
überschreiten.

## Kommentare

### Entwicklerinformationen

Jede Datei sollte mit einem einleitenden Kommentar beginnen, der Informationen über die Entwickler, die aktuelle
Version und sonstiges enthält.

````java
/*
 * MyClass
 * Version 1.0.4
 * 
 * Copyright (C) 2025 [Entwicklernamen]
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
package my.pkg;

public class MyClass {
    // Klassenrumpf
}
````

### Inlinekommentare

Vor Inline-Kommentaren sollte eine Leerzeile eingefügt werden, um den Inhalt vom restlichen Code optisch abzutrennen.

````java
package my.pkg;

public class MyClass {
    
    public static void main(String[] args) {
        int myInt = 5;
        int result;
        
        /* rechnen */
        result = myInt + 10;
        System.out.printf("%d + 10 = %d.", myInt, result);
    }
}
````

### Java-Docs

Verwende Java-Doc-Kommentare, um darzustellen, was die entsprechende Methode tut, welche Parameter benötigt werden
und was ggf. zurückgegeben wird.

````java
package my.pkg;

import java.io.PrintWriter;
import java.util.ArrayList;

public class MyClass {

    /**
     * prints each {@link ArrayList} item using its {@code toString()} method. One item per line.
     * 
     * @param out   PrintWriter instance for printing data
     * @param list  list of items to be printed
     */
    public void printListItems(PrintWriter out, ArrayList<?> list) {
        for (Object o : list) {
            out.println(o);
        }
    }
}
````


## Variablen

### Klassen- und Instanzvariablen

Klassen- und Instanzvariablen werden von **public** nach **private** deklariert:

````java
public class MyClass {
    
    /* Klassenvariablen */
    public static int myClassInt = 1;
    protected static String myClassString = "Hello World";
    private static boolean myClassBoolean = true;
    
    /* Instanzvariablen */
    public int myInt;
    protected int myProtectedInt;
    private int myPrivateInt;
}
````

### Lokale Variablen

Lokale Variablen werden direkt zu Beginn des Blocks deklariert. Vor der ersten Anweisung erfolgt eine Leerzeile.

````java
public class MyClass {
    public int myInt;
    protected int myProtectedInt;
    private int myPrivateInt;
    
    public void doAction() {
        int myLocalInt = 5;
        
        System.out.println(myLocalInt);
    }
}
````
# Eclipse IDE und IntelliJ IDE

Um ein Java-Projekt sowohl in Eclipse als auch in IntelliJ bearbeiten zu können, müssen wir zunächst ein Projekt
in Eclipse anlegen und dieses dann anschließend in IntelliJ importieren.

## Projekt in Eclipse anlegen

### Neues Projekt anlegen
![img.png](/docs/img/eclipse_new.png) 

### Ordnerstruktur

![img.png](/docs/img/eclipse_project_files.png)

Die Datei ``.project`` definiert ein Eclipse-Projekt. Diese Datei wird benötogt, damit das Projekt in Eclipse
angezeigt und bearbeitet werden kann. Die Datei ``.classpath`` definiert die Arbeitsordner wie **Source** und **Compiler-Output**.

IntelliJ nutzt allerdings andere Konfigurationsdateien. Im Folgenden wird gezeigt, wie das bestehende Eclipse-Projekt
auch in IntelliJ weiterbearbeitet werden kann.

## Projekt in IntelliJ importieren

### A: Über Kontextmenü importieren
![img.png](/docs/img/intelli_context_import.png)

Importiere das Eclipse-Projekt über den Eintrag **Open Folder as IntelliJ IDEA Project**.

### B: Über Programm importieren

Importiere das Eclipse-Projekt über den Button **Open**.

![img.png](/docs/img/intelli_direct_import.png)

### Projekt konfigurieren

Nun müssen wir die Projekt-Struktur anpassen.

![img.png](/docs/img/intelli_config.png)

#### SDK einstellen

Hier wählen wir am besten dieselbe Version wie in Eclipse. Dies können wir aber jederzeit ändern.

![img.png](/docs/PR1/sdk.png)

#### Modul erstellen

![img.png](/docs/PR1/img.png)

Wir wollen ein **Java-Modul** erstellen. Als Build-System nutzen wir **IntelliJ**. Maven und Gradle sind besondere
Modulmanager, die wir aktuell nicht verwenden.

Als JDK wählen wir hier ggf. noch die richtige Version aus.

![img_1.png](/docs/PR1/img_1.png)

### Aktualisierte Ordnerstruktur

Wie auch Eclipse hat nun IntelliJ eigene Ordner und Config-Dateien erstellt. Beide IDEs wissen nun, mit deinem Projekt umzugehen.

![img_2.png](/docs/PR1/img_2.png)

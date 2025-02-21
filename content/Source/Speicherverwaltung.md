
## Speicherverwaltung
[Erklärungsvideo Stack vs Heap](https://youtu.be/LTnp79Ke8FI?si=fA2O5RbnPNWFu2m-)

![[Attachments/Pasted image 20250101203601.png|600]]

#### Stack
- speichert Primitive Variablen (z. B. `int`, `boolean`) und lokale Variablen.
- speichert Methodenaufrufe und ihre Parameter.
- Linear organisiert und arbeitet nach dem Prinzip „Last In, First Out“ (LIFO).
- Speicher wird automatisch freigegeben, wenn der Gültigkeitsbereich verlassen wird.
- Kurzlebig bzw. Daten existieren nur, solange der zugehörige Methodenaufruf aktiv ist.
#### Heap
- speichert Instanzen von Objekten, die mit `new` erstellt werden.
- speichert Klassenvariablen, wenn sie als `static` deklariert sind.
- Dynamisch organisiert: Speicher wird manuell durch den Garbage Collector verwaltet.
- Kann große Datenmengen aufnehmen.
- Langlebig bzw. Daten existieren, solange es mindestens eine Referenz darauf gibt.

#### Garbage Collector
- Entfernt "verwaiste" Objekte, auf die keine Referenz mehr zeigt.
- Heap wird regelmäßig bereinigt.

## Call-by-Reference and Call-by-Value 
#### Call-by-Value 
Bei Übergabe eines primitiven Datentyps:
- Übergibt nur den Wert einer Variablen.
- Änderungen innerhalb der Methode wirken sich nicht auf die ursprüngliche Variable aus.

```java
public class Main {
    public static void changeValue(int zahl) {
        zahl = 100; // Änderungen betreffen nur die lokale Kopie
    }

    public static void main(String[] args) {
        int zahl = 50; // Originalwert
        changeValue(zahl);
        System.out.println(zahl); // Ausgabe: 50 (unverändert)
    }
}

```

#### Call-by-Reference
Bei Übergabe eines Objekts:
- Übergibt eine Kopie der Referenz auf ein Objekt.
- Änderungen am Objekt innerhalb der Methode sind dauerhaft, da auf dasselbe Objekt im Heap verwiesen wird.

```java
public class Main {
    public static void changeObjectName(Mitarbeiter mitarbeiter) {
        mitarbeiter.setName("Neuer Name"); // Änderungen betreffen das Originalobjekt
    }

    public static void main(String[] args) {
        Mitarbeiter mitarbeiter = new Mitarbeiter(); // Instanz im Heap
        mitarbeiter.setName("Alter Name");
        changeObjectName(mitarbeiter);
        System.out.println(mitarbeiter.getName()); // Ausgabe: Neuer Name
    }
}

```
## Static Variablen
- Wird nur einmal pro Klasse gespeichert, unabhängig von Instanzen
- Kennzeichnung im Klassendiagramm durch Unterstreichen

## Static Methoden
- Können ohne Instanz aufgerufen werden
- Arbeiten nicht mit Instanzvariablen
- Kennzeichnung im Klassendiagramm durch Unterstreichen

## Zugriff auf Objekte
- für den Zugriff auf öffentliche Methoden muss eine Referenz auf das Objekt.
- Objekte müssen mit `new` erstellt werden, um im Heap gespeichert zu werden.




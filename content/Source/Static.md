## Static vs. Nicht-Static

- Static Methoden & Variablen gehören zur Klasse, nicht zu einzelnen Objekten.
- Sie können ohne Instanz verwendet werden und arbeiten prozedural.
- Eine static Methode kann auf static Variablen und static Methoden der eigenen Klasse sowie auf protected static Methoden der darüber liegenden Klasse zugreifen.
- Um eine nicht-static Methode zu verwenden, benötigt man eine Instanz der Klasse.
- Aufruf außerhalb der Klasse: Static Methoden werden durch den Klassenname und einen Punkt vor der Methode erkennbar.
- Aufruf innerhalb der Klasse: Es ist kein `this` oder Klassenname nötig, daher ist nicht direkt erkennbar, ob die Methode `static` ist.
- Das Schlüsselwort `static` wird genutzt, wenn eine Methode keine Instanz-Variablen benötigt.
- Instanz-Methoden können auf `static` Eigenschaften und Methoden zugreifen.

| Eigenschaft   | **Static**                                                  | **Nicht-Static**                          |
| ------------- | ----------------------------------------------------------- | ----------------------------------------- |
| **Methoden**  | Arbeiten ohne Instanzvariablen                              | Brauchen Instanzvariablen                 |
| **Variablen** | Klassenvariablen (gelten für alle Objekte)                  | Instanzvariablen (pro Objekt individuell) |
| **Nutzen**    | Gemeinsame Daten speichern (z. B. Anzahl aller Mitarbeiter) | Beschreiben einzelne Objekte              |

## Code Beispiel

```java
public class Mitarbeiter {
    private int id;
    private String name;
    private static int anzahl = 0;

    public Mitarbeiter(String name) {
        this.name = name;
        anzahl++; 
        this.id = 10000 + anzahl;
    }

    public static int getAnzahl() {
        return anzahl;
    }
}
```

## Klassendiagramm

`static` Eigenschaften werden **unterstrichen**.

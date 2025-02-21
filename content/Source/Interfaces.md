## Warum Interfaces?

- Java erlaubt keine Mehrfachvererbung, um das "Diamond Problem" zu vermeiden.
- Interfaces lösen das Problem, indem sie eine Alternative zur Mehrfachvererbung bieten.
- Objekte mit völlig verschiedenen Klassen können eine gemeinsame Funktionalität haben.
## Eigenschaften von Interfaces 
- Enthalten keine Implementierung, nur Methodensignaturen (deklarieren und nicht implementieren).
- Werden mit `implements` statt `extends` eingebunden.
- Methoden sind automatisch `public` und `abstract`.
- Attribute sind immer `static` und `final`.
- Wenn man angibt, dass ein Interface verwendet wird, muss man sicherstellen, dass die Methoden  des Interface implementiert wurden.

## Code Beispiel

```java
public interface Zeichenbar {
    void zeichnen(double x, double y);
}

public class Kreis implements Zeichenbar {
    private double radius;

    public Kreis(double radius) {
        this.radius = radius;
    }

    @Override
    public void zeichnen(double x, double y) {
        System.out.println("Kreis wird bei " + x + ", " + y + " gezeichnet.");
    }
}
```

## Mehrere Interfaces gleichzeitig nutzen

```java
public class Kreis implements Zeichenbar, Fuellbar { }
```

## Default-Methoden
- Seit Java 8 können default-Methoden eine Standardimplementierung bereitstellen.
- Neue Methoden können hinzugefügt werden, ohne alle implementierenden Klassen zu ändern.

```java
public interface Movable {
    default void moveTo(double x, double y) {
        System.out.println("Bewegt zu " + x + ", " + y);
    }
}
```

## Interface vs. Abstrakte Klasse

| Feature           | **Interface**                                     | **Abstrakte Klasse**             |
| ----------------- | ------------------------------------------------- | -------------------------------- |
| **Vererbung**     | Mehrfachvererbung möglich                         | Nur Einfachvererbung             |
| **Methoden**      | Keine Implementierung (außer `default` ab Java 8) | Kann Methoden implementieren     |
| **Attribute**     | Immer `static` und `final`                        | Kann normale Attribute enthalten |
| **Konstruktoren** | Nicht erlaubt                                     | Möglich                          |

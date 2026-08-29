Ein **Konstruktor** ist eine spezielle Methode, die beim Erstellen eines Objekts automatisch aufgerufen wird.

## Merkmale
  - Haben denselben Namen wie die Klasse
  - Besitzen keinen Rückgabewert (auch kein `void`)
  - Werden nur bei der Instanzierung mit `new` aufgerufen
  - Konstruktoren nutzen Setter, um Kapselung zu gewährleisten

## Typen von Konstruktoren
#### Default-Konstruktor
Standard-Konstruktor ohne Parameter, optional, wenn keine andere Konstruktoren existieren:

```java
public class Mitarbeiter {
	...
    public Mitarbeiter() {
        setName("Max Mustermann");
        setId(10000000);
    }
    ...
}
```
Muss explizit definiert werden, wenn andere Konstruktoren vorhanden sind:

```java
public Mitarbeiter() { 

}
```
#### Konstruktor mit Wertübergabe
Setzt Eigenschaften des Objekts basierend auf den übergebenen Werten.
```java
public class Mitarbeiter {
    ...
    public Mitarbeiter(String name, int id) {
        setName(name);
        setId(id);
    }
	...
}
```

#### Kopier-Konstruktor
Erstellt ein neues Objekt, das eine Kopie eines bestehenden Objekts ist.
```java
public class Mitarbeiter {
	...
    public Mitarbeiter(Mitarbeiter mitarbeiter) {
        setName(mitarbeiter.getName());
        setId(mitarbeiter.getId());
    }
    ...
}
```

## Überladen
Überladen bedeutet, mehrere Konstruktoren oder Methoden mit demselben Namen in einer Klasse (gleichen Gültigkeitsbereich) zu definieren. Unterschiede basieren auf:
- Anzahl der Parameter
- Typen der Parameter
- Reihenfolge der Parameter


> [!info]
> Überladen kann nicht durch Rückgabetypen unterschieden werden


## Codeausschnitt
```java
public class Main {
    public static void main(String[] args) {
        // Konstruktor mit Wertübergabe
        Mitarbeiter arbeiter = new Mitarbeiter("Harry", 5555);
        // Default-Konstruktor
        Mitarbeiter bueroarbeiter = new Mitarbeiter();
        // Kopier-Konstruktor
        Mitarbeiter kopieArbeiter = new Mitarbeiter(arbeiter);
    }
}
```


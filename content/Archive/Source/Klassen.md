## Warum Objektorientierung?
Mit leistungsfähigeren Rechnern wurden Programme komplexer und unübersichtlicher, weshalb die Objektorientierung durch die Aufteilung in Klassen eingeführt wurde, um Daten zu schützen und Seiteneffekte zu vermeiden.
#### Nachteile
- Höherer interner Verwaltungsaufwand
- Geringere Ausführungsgeschwindigkeit im Vergleich zu strukturierten Programmen
- Viele Treiber und Betriebssystemkerne werden weiterhin in ANSI C geschrieben
#### Vorteile
- Kürzere Entwicklungszeiten
- Bessere Wartbarkeit
- Höhere Erweiterbarkeit
## Konzepte

#### Klassen
Eine **Klasse** ist der Bauplan, der festlegt, welche Eigenschaften (z. B. Name, Alter) und Methoden (z. B. laufen, fressen) ein Objekt haben kann.
#### Objekt
Ein **Objekt** ist eine Instanz einer **Klasse**, also ein konkretes Beispiel, das die Eigenschaften und Fähigkeiten der Klasse nutzt.

#### Getter und Setter
- Methoden, die den Zugriff auf private Attribute einer Klasse ermöglichen. 
- **Getter** lesen den Wert eines Attributs, **Setter** ändern ihn. 
- Sie schützen die Daten und kontrollieren den Zugriff darauf.
#### Eigenschaften
Variablen, die zu einer Klasse gehören und außerhalb von Methoden, aber innerhalb der Klasse deklariert sind.

#### Methoden
Funktionen oder Prozeduren, die das Verhalten einer Klasse oder eines Objekts definieren.

#### Referenz
Ein Name, der bei der Deklaration eines Objekts angelegt wird und auf die Instanz verweist.

#### Instanz
Eine konkrete Variable vom Datentyp der Klasse, die mit `new` erstellt wird (oft als Objekt bezeichnet).
#### Instanz-Variablen
Eigenschaften, die eine spezifische Instanz (ein Objekt) beschreiben.
#### Instanz-Methoden
Methoden, die mit den Instanz-Variablen eines Objekts arbeiten.

#### static-Methoden

Methoden, die unabhängig von einer Instanz aufgerufen werden können.

#### Kapselung

Ein Konzept zum Schutz von Eigenschaften und Methoden, oft mithilfe von Zugriffsmodifikatoren wie `private`:
- **private:** Schlüsselwort, das den Zugriff auf eine Eigenschaft oder Methode auf die eigene Klasse beschränkt.
- **public:** Schlüsselwort, das den Zugriff auf eine Eigenschaft oder Methode von außen erlaubt.

## Klassendiagramm
![[Archive/Attachments/Miatarbeiter 2.png|250]]
#### Eigenschaften (Attribute)
- Datentypen werden mit einem Doppelpunkt hinter dem Namen angegeben 
- `+` (öffentlich/public)
- `-` (privat/private)

#### Methoden
- Parameter sind in den Klammern mit ihrem Typ anzugeben
- Rückgabewerte werden nach den Klammern mit einem Doppelpunkt angegeben 
- Parameter ohne Namen sind nicht erlaubt.
- Parameter und Rückgabetypen sind Pflicht bei Methoden.
- Getter und Setter sind oft selbsterklärend und können im Klassendiagramm weggelassen werden

## Codeausschnitte
#### Klasse
```java
public class Mitarbeiter {
    private int id;
    private String name;

    public void setId(int id) {
        if (id < 0) {  
            id = -id;
        }
        if (id < 1000) {
            this.id = id + 1000;
        } else {
            this.id = id;
        }
    }
    
    public int getId() {
        return this.id;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return this.name;
    }

    public String toString() {
        return "ID: " + this.id + ", Name: " + this.name;
    }
}
```

#### main
```java
public class Main {
    public static void main(String[] args) {
        Mitarbeiter arbeiter = new Mitarbeiter();
        arbeiter.setName("Paul");
        arbeiter.setId(123);

        System.out.println("Der Name des Arbeiters ist: " + arbeiter.getName());
}

```
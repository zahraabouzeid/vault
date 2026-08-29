Polymorphie bedeutet, dass Objekte unterschiedliche Gestalten annehmen können und sich unterschiedlich verhalten, je nach dem, wie sie aufgerufen werden. In Java basiert Polymorphie stark auf **Vererbung**, **Abstraktion** und **dynamischem Binden (late binding)**.

## Polymorphe Objekte
Ein polymorphes Objekt ist eine Sammlung von Elementen, bei der jedes Element auf eine Instanz einer abgeleiteten Klasse zeigt. Dabei kann jede Instanz eigene spezifische Methoden implementieren, die über gemeinsame Schnittstellen oder Basisklassen verwendet werden.

```java
public class Main { 
	public static void main(String[] args) { 
		Mitarbeiter[] team = new Mitarbeiter[2]; 
		team[0] = new SchichtArbeiter("Joe", 15.5, 17); 
		team[1] = new BueroArbeiter("Anita", 2000); 
		for (Mitarbeiter mitarbeiter : team)
			System.out.println(mitarbeiter.toString()); 
		} 
	} 
}
```
#### Eigenschaften
- Haben die Referenz einer übergeordneten Klasse
- Können auf jede beliebige Instanz von abgeleiteten Klassen, die nicht abstrakt sind verweisen
- Können nur das was die Klasse der Referenz kennt

>[!info]
>Ein Container ist eine Menge von unterschiedlich gestalteten Objekten: Array, Klasse oder auch Parameter
## Prozedural vs. Objektorientiert

#### Prozedural

```java
if (mitarbeiterTyp.equals("SchichtArbeiter")) {
    System.out.println(((SchichtArbeiter) m).toString());
} else if (mitarbeiterTyp.equals("BueroArbeiter")) {
    System.out.println(((BueroArbeiter) m).toString());
} else if (mitarbeiterTyp.equals("Manager")) {
    System.out.println(((Manager) m).toString());
}
// Für jede neue Klasse: weitere Bedingung hinzufügen
```

**Nachteile:**
- Jede neue Klasse erfordert Änderungen an allen Stellen mit `if-else`
- Code ist schwer wartbar und anfällig für Fehler
- Unübersichtlich bei vielen Mitarbeitertypen

#### Objektorientiert
```java
for (Mitarbeiter m : anonym) {
    System.out.println(m.toString());
}
// Automatisch wird die korrekte toString() Methode (durch Polymorphie) aufgerufen.
```

**Vorteile:**
- Kein Bedarf, bestehende Logik zu ändern, wenn neue Klassen hinzugefügt werden
- Einfacher und übersichtlicher Code
- Wartungsfreundlich

## Late Binding
Bei **Late Binding** wird die zu verwendende Methode erst zur **Laufzeit** bestimmt, basierend auf der tatsächlichen Klasse des Objekts. Dies ist ein Kernelement der Polymorphie in objektorientierten Programmiersprachen wie Java.
#### Vorteile von Late Binding
- **Flexibilität:** Der konkrete Typ des Objekts muss nicht zur Kompilierzeit bekannt sein
- **Erweiterbarkeit:** Neue Klassen können hinzugefügt werden, ohne den bestehenden Code zu ändern

#### Nachteil
**Performance:** Es kostet Laufzeit, da die Methode erst zur Laufzeit bestimmt wird
## Abstrakte Klassen
Abstrakte Klassen dienen als Vorlage, die gemeinsame Eigenschaften und Methoden definiert, jedoch oft keine vollständige Implementierung enthält:
- **Abstrakte Methoden**: Methoden ohne Implementierung, die in abgeleiteten Klassen definiert werden müssen
- **Keine Instanziierung**: Von abstrakten Klassen können keine Objekte erstellt werden
- **Sinnvolle Verwendung**: Wenn für die Methode der Basisklasse kein allgemeiner Inhalt sinnvoll ist, z. B. eine `einkommen()` Methode für alle Mitarbeiter
- Eine Klasse mit mindestens einer abstrakten Methode ist eine abstrakte Klasse

```java
public abstract class Mitarbeiter {
    private String name;

    public abstract double einkommen(); // Abstrakte Methode
}

public class SchichtArbeiter extends Mitarbeiter {
    private double stundenSatz;
    private int stunden;

    @Override
    public double einkommen() {
        return stunden * stundenSatz;
    }
}
```

## Klassendiagramm
![[Archive/Attachments/Pasted image 20250102212957.png|300]]
- Klassenname kursiv oder mit `{abstract}`
- Abstrakte Methoden kursiv dargestellt
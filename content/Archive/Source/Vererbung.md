Vererbung ermöglicht es, eine neue Klasse (abgeleitete Klasse) auf Basis einer bestehenden Klasse (Basisklasse) zu erstellen. Dies spart Entwicklungszeit, verbessert die Lesbarkeit und Wiederverwendbarkeit von Code.
```java
public class Mitarbeiter {
    private int id;
    private String name;

    public String toString() {
        return "ID: " + id + ", Name: " + name;
    }
}

public class SchichtArbeiter extends Mitarbeiter {
    private double stundenSatz;
    private int anzahlStunden;

    public double einkommen() {
        return stundenSatz * anzahlStunden;
    }
}
```
In jedem SchichtArbeiter-Objekts ist ein Mitarbeiter-Kernobjekt.
>[!info]
> Man darf einer Referenz einer abgeleiteten (erbenden) Klasse eine Instanz einer darüber liegenden Klasse nicht zuordnen, weil die **Referenz** des Objekts bestimmt, welche **Methoden** verwendet werden dürfen. Das dahinter liegende eigentliche Objekt „**bedient“** lediglich diese **Methodenaufrufe**. Wenn das Objekt nicht **vollständig** ist, kann es die Anforderung **nicht erfüllen**.
## Darstellung
![[Archive/Attachments/Pasted image 20250101223245.png|400]]
- Die Basisklasse wird als übergeordnet dargestellt
- Unausgefülltes Dreieck als Pfeilspitze
- Der Pfeil zeigt von der abgeleiteten Klasse zur darüberstehenden Klasse (vom Kind zum Vater)
- Vererbungen sind "**ist** ein" Beziehungen 

## Sichtbarkeit
| Zugriffstyp   | Eigene Klasse | Eigenes Paket | Fremdes Paket: Abgeleitete Klasse | Fremdes Paket: Fremde Klasse |
|---------------|---------------|---------------|------------------------------------|------------------------------|
| **private (-)** | ja            | nein          | nein                               | nein                         |
| **default (~)** | ja            | ja            | nein                               | nein                         |
| **protected (#)** | ja            | ja            | ja                                 | nein                         |
| **public (+)**   | ja            | ja            | ja                                 | ja                           |

- Eigenschaften sollten immer `private` bleiben, um Kapselung zu gewährleisten.
- Methoden können `protected` gemacht werden, um sie in abgeleiteten Klassen anzupassen.
- In abgeleiteten Klassen werden Getter und Setter verwendet, um auf die privaten Eigenschaften der übergeordneten Klasse zuzugreifen.
>[!info]
>- `private`: Nur innerhalb der Klasse sichtbar.
>- `protected`: Sichtbar in der Klasse, abgeleiteten Klassen (egal welchem Paket) und im gleichen Paket.
>- `public`: Sichtbar überall.


## Konstruktoren
Konstruktoren der Basisklasse werden nicht automatisch vererbt. Abgeleitete Klassen müssen eigene Konstruktoren definieren und die Konstruktoren der Basisklasse mit `super()` aufrufen.
#### Regeln
- `super()` muss an erster Stelle im Konstruktor stehen
- Gibt es keinen Standardkonstruktor in der Basisklasse, muss ein passender Konstruktor explizit aufgerufen werden (ansonsten Syntaxerror)
```java
public class Mitarbeiter {
    public Mitarbeiter(int id, String name) {
        setID(id);
        setName(name);
    }
}

public class SchichtArbeiter extends Mitarbeiter {
    public SchichtArbeiter(int id, String name, double stundenSatz) {
        super(id, name);
        this.stundenSatz = stundenSatz;
    }
}
```

## super-Referenz
Methoden der übergeordneten Klasse können mit super (Referenz auf übergeordnete Klasse) aufgerufen werden:
```java
public class Mitarbeiter {
	public String toString(){  
		return ( "ID: " + id  + " Name: " + name);
	}
}

public class SchichtArbeiter extends Mitarbeiter{  
	@Override  public String toString(){  
		String result = super.toString()  + " Einkommen: " + einkommen();
		return result;    
	}
```

>[!info]
>super. und super(): das Erste ist eine Referenz, das Zweite ist der Konstruktoraufruf der darüberstehenden Klasse

## this vs super
#### this
- ist ein Verweis auf die eigene Objektschicht
- man kann es weglassen bei Methodenaufrufen
- wir brauchen es um namensgleiche lokale Variablen und Parameter von Instanzvariablen zu unterscheiden

#### super
- ist ein Verweis auf die innere Objektschicht
- benötigt man um Methoden mit identischen Signaturen in abgeleiteten Klassen von einander zu unterscheiden

## Redefinition
Eine Methode aus der Basisklasse wird in der abgeleiteten Klasse neu definiert, um spezifisches Verhalten zu implementieren:
```java
public class Mitarbeiter {
    public String toString() {
        return "ID: " + id + ", Name: " + name;
    }
}

public class SchichtArbeiter extends Mitarbeiter {
    @Override
    public String toString() {
        return super.toString() + ", StundenSatz: " + stundenSatz;
    }
}
```
## Überladung 
Eine Methode hat denselben Namen, aber unterschiedliche Parameter:
```java
public class Mitarbeiter {
    public void setName(String name) {
        this.name = name;
    }

    public void setName(String firstName, String lastName) {
        this.name = firstName + " " + lastName;
    }
}
```

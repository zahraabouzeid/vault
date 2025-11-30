# Unit Testing

## Test Pyramide
- **Unit Tests**: Testen einzelner Klassen, viele Tests, schnell, einfach zu debuggen => sind Bausteine von Regressionstests
- **Funktionstests**: Testen Interaktionen zwischen Klassen, mittlere Anzahl und Geschwindigkeit.
- **System Tests**: Testen des gesamten Systems aus Benutzersicht, wenige Tests, langsam, schwer zu debuggen => wenn Test fehlschlägt, man weiß nicht wo der Fehler liegt

## Was macht Code nicht schwer testbar?
- **Private Methoden** => gehören nicht zu öffentlichen Schnittstelle. Man muss sie nicht testen
- `final` Das sind Variablen die konstant bleiben, also sollen sogar einfacher zu testen sein. Was sich nicht ändert, macht das Testen nicht schwieriger
- **Lange Methoden** brauchen mehr Tests, aber sind nicht unbedingt schwer zu testen
## Was macht Code schwer testbar?
- **Mixing new with business logic**: Versteckte Abhängigkeiten durch direkte Verwendung von `new` => Dependency Injection nötig, also Abhängigkeiten als Parameter übergeben. Das Schlüsselwort `new` gehört in eine Factory Klasse und nicht in produktiven Code
- **Mixing Service and Value in one class**: Vermischung von Logik und Datenhaltung. (zb. total rechnen und gleichzeitig es in der Datenbank speichern)
- **Looking for things (Law of Demeter Verletzung)**: Lange Getter-Ketten wie `customer.getWallet().getMoney()`. (Wenn man wiele.get().get() hintereinander sieht, dh Law of Demeter wurde verletzt)
- **Doing "work" in the constructor**: Produktiver Code im Konstruktor (z.B. DB-Verbindung statt nur variablen zu setzen).
- **Global state, static variables/methods**: Keine Möglichkeit, Abhängigkeiten auszutauschen (schau Singleton)
- **Deep inheritance**: Fehler schwer lokalisierbar (also wenn viele Verebungen da sind, man weiss nicht ob der Fehler in der jetzigen oder Parent Klasse liegt)
- **Too many conditionals**: Viele Testfälle nötig, Tests müssen häufig angepasst werden. (wenn man viele verschachtelte ifs hat)

## Law of Demeter
- **Definition**: Methoden sollen nur direkt benötigte Objekte als Parameter erhalten.
- **Verletzung**: `a.getX().getY()` erfordert komplette Objekt-Kette im Test (also Looking for things, zb damit zu geld abziehst, gibst du den ganzen wallet als Objekt, das wäre falsch)

**Falsch:**
```java
class Goods {
    AccountsReceivable ar;
    
    void purchase(Customer c) {
        Money m = c.getWallet().getMoney();  // VERLETZT Law of Demeter!
        ar.recordSale(this, m);
    }
}
```

**Richtig**

```java
class Goods {
	void purchase(Money m) {
		ar.recordSale(this, m); 
	} 
}
```
## Dependency Injection (DI)
- **Definition**: Abhängigkeiten werden von außen übergeben (Konstruktor/Methoden), nicht intern erstellt.
- **Vorteil**: Trennung von Objekterstellung und Geschäftslogik, bessere Testbarkeit.
- **Beispiel**: Statt `new Database()` im Konstruktor: `public ReportGenerator(Database db)`.
**Untestbar - ohne DI:**

```java
class ReportGenerator {
    public ReportGenerator() {
        this.db = new Database("production-server");  // Hart kodiert!
    }
}
```

**Testbar - mit DI:**

```java
class ReportGenerator {
    public ReportGenerator(Database db) {  // Injiziert!
        this.db = db;
    }
}

@Test
void testReport() {
    Database mockDb = new MockDatabase();
    ReportGenerator gen = new ReportGenerator(mockDb);
    assertEquals(expected, gen.generateReport());
}
```
## Test-Doubles (bzw Friendlies)
- **Dummy**: Unbenutztes Objekt, verhindert NullPointerException.
- **Mock**: Konfigurierbar, zeichnet Aufrufe auf, gibt feste Werte zurück.
- Objekte bereits getestete Klassen

Info: **NULL in Tests**: Zeigt an, dass eine Abhängigkeit für den Test irrelevant ist.

## Seam
**Definition**: Stelle im Code, an der Verhalten geändert werden kann, ohne Code zu ändern. Man kann da zb. Sachen mit Mocks tauschen und einfacher Testen

## JUnit Grundlagen
- **Library vs. Framework**: JUnit ist ein Framework (Inversion of Control). Bei einem Framework hat das Framework die Kontrolle: es ruft deinen Code auf. Bei einem Library rufst du die Methoden auf. zb. `Math.sqrt(25)`
- **Import:**  `import org.junit.jupiter.api.*;`
- **Annotations**:
  - `@BeforeAll` (static), `@BeforeEach`  => Setup Methoden
  - , `@AfterAll` (static), `@AfterEach` => Teardown Methoden
  - `@Test`, `@Disabled`, `@DisplayName`
- **Ablauf**: BeforeAll → Für jeden Test: neue Instanz, BeforeEach, Test, AfterEach → AfterAll.
- **Assert-Methoden**: `assertTrue`, `assertEquals`, `assertNull`, `assertThrows`, `assertSame` etc.
Syntax: assert...(expected, calculated)

### JUnit Tests
- sollen erkennbaren Namen haben also zb. Mitarbeiter => MitarbeiterTest
- Ergebnisse: Grün => erfolgreich, Rot (fehlgeschlagen), Blau (mit `fail()` abgebrochen)

Info: TDD heißt Test Driven Development. Unit Tests werden zuerst geschrieben und dannach die Klassen.

### Arten von Fehlern 
Ein Fehlschlag kann zwei Gründe haben: 
1. Failures (erwartete Fehler): Testfall ist gescheitert, das heißt das getestete Verhalten entspricht nicht den Erwartungen
2. Errors (unerwartete Fehler): Kein korrekter Durchlauf des Tests – beispielsweise durch eine unerwartete Exception
## Test Coverage
- **Line Coverage**: Wie viele Codezeilen wurden ausgeführt?
- **Branch Coverage**: Wie viele Verzweigungen (if, switch) wurden getestet?
- **Hinweis**: 100% Coverage heißt nicht fehlerfreier Code.

## Best Practices (FIRST)
- **Fast**: Schnell ausführbar.
- **Independent**: Unabhängig voneinander.
- **Repeatable**: In jeder Umgebung gleich.
- **Self-validating**: Eindeutig Pass/Fail.
- **Timely**: Zeitnah geschrieben.

## Weitere Regeln
- **Teste Verhalten, nicht Implementierung** (Triple-A: Arrange, Act, Assert).
```java
@Test
void testCalculateTotal() {
    // Arrange
    ShoppingCart cart = new ShoppingCart();
    cart.addItem(new Item("Buch", 10.0));
    cart.addItem(new Item("Stift", 2.0));
    
    // Act
    double total = cart.calculateTotal();
    
    // Assert
    assertEquals(12.0, total, 0.01);
}
```
- **Single Responsibility**: Eine Testmethode, ein Verhalten. Eine Testmethode sollte nur eine Sache verifizieren.
- **Sprechende Testnamen**: z.B. `testCalculateTotalWithEmptyCart()`.
- **Vermeide komplexe Setups**: Hilfsmethoden oder Refactoring der Klasse.
```java
class CalculatorTest {
    
    @Nested
    class AdditionTests {
        @Test
        void testAddPositiveNumbers() { ... }
        
        @Test
        void testAddNegativeNumbers() { ... }
    }
    
    @Nested
    class DivisionTests {
        @Test
        void testDivideByZeroThrowsException() { ... }
        
        @Test
        void testDividePositiveNumbers() { ... }
    }
}
```
- **Keine Vererbung von Testklassen**: Komposition bevorzugen.
- **Gruppierung mit @Nested**: Tests mit gleichem Kontext zusammenfassen.

## Singleton Pattern (Erzeugungsmuster)
- **Zweck**: Sicherstellt, dass nur eine Instanz existiert.
- **Lazy Creation**: Instanz wird bei Bedarf erstellt (Thread-Probleme möglich).
```java
public final class Unsterblicher {
    private static Unsterblicher instance;
    
    private Unsterblicher() {} 
    
    public static Unsterblicher getInstance() {
        if (instance == null)  
            instance = new Unsterblicher();
        
        return instance;
    }
}
```
**Problem:** Es kann sein dass Zwei Threads gleichzeitig überprüfen ob eine Instance gibt, dabei kommt bei beiden False und erzeugen dann 2 Instanzen
**Lösung:** `public static synchronized Unsterblicher getInstance() {` (also synchronized)

- **Eager Creation**: Instanz sofort beim Laden der Klasse (threadsicher).
```java
public final class Unsterblicher {
    private static final Unsterblicher INSTANCE = new Unsterblicher();  // hier direkt erstellt
    
    private Unsterblicher() {}
    
    public static Unsterblicher getInstance() {
        return INSTANCE;
    }
}
```
- **Probleme**:
  - Globaler Zustand, schwer testbar.
  - Versteckte Abhängigkeiten.
  - Keine Dependency Injection möglich.
  - Instanz wird erstellt beim Laden, auch wenn sie vllt nicht gebraucht wird
- **Bessere Alternative**: Dependency Injection.
#### Wann welche Variante? 
- Lazy Creation verwenden wenn: 
	- Das Objekt ist groß/teuer zu erstellen 
	- Das Objekt wird möglicherweise nie gebraucht 
	- Du bist dir der Thread-Probleme bewusst 
	- Beispiel: Datenbankverbindung, die nur manchmal gebraucht wir
- Eager Creation verwenden wenn: 
	- Das Objekt wird sicher gebraucht 
	- Das Objekt ist klein/schnell zu erstellen 
	- Du willst keine Thread-Probleme 
	- Beispiel: Logger, der immer gebraucht wird
## Strategy Pattern
- **Zweck**: Kapselt Algorithmen in separate Klassen, austauschbar zur Laufzeit.
- **Komponenten**:
  - Strategy (Interface)
  - ConcreteStrategy (Implementierungen)
  - Context (verwendet Strategy)
- **Vorteile**:
  - Vermeidet Code-Duplikation.
  - Einfach erweiterbar (Open/Closed Principle).
  - Gut testbar (Strategy als Seam für Mocks).
- **Design Principles**:
  - Dependency Inversion (Abhängigkeit von Abstraktionen).
  - Composition over Inheritance.
  - Encapsulate What Varies.
  - Program to Interface, Not Implementation.
- **Tests:**
Das Strategy Pattern macht Code testbar, indem es einen Seam (Nahtstelle) schafft, an dem echte Implementierungen durch Test-Doubles ersetzt werden können

### Strategy Interface

```java
package duckSim;

public interface FlugVerhalten {
    public void fliegen();
}
````
### Concrete Strategies

```java
package duckSim;

public class Fluegelschlagen implements FlugVerhalten {
    public void fliegen() {
        System.out.println("Ich schlage mit den Flügeln und fliege!!");
    }
}
```

```java
package duckSim;

public class Gleiten implements FlugVerhalten {
    public void fliegen() {
        System.out.println("Ich gleite durch die Luft!!");
    }
}
```

```java
package duckSim;

public class NichtFliegen implements FlugVerhalten {
    public void fliegen() {
        System.out.println("Ich kann nicht fliegen.");
    }
}
```

```java
package duckSim;

public class RaketenAntriebsFliegen implements FlugVerhalten {
    public void fliegen() {
        System.out.println("Ich fliege mit RRRAKKKETEN-ANTRIEB!");
    }
}
```

### Context (abstrakte Basisklasse)

```java
package duckSim;

public abstract class Ente {
    private String name;
    private FlugVerhalten flugVerhalten;
 
    public Ente(String name, FlugVerhalten fv) {
        setName(name));
        setFlugVerhalten(fv);
    }
 
    public void setFlugVerhalten(FlugVerhalten fv) {
        flugVerhalten = fv;
    }
 
    abstract void anzeigen();
 
    public void tuFliegen() {
        flugVerhalten.fliegen();
    }
 
    public void schwimmen() {
        System.out.println("Alle Enten schwimmen, auch Holzenten!");
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

<div style="page-break-after: always;"></div>

### Konkrete Klassen

```java
package duckSim;

public class StockEnte extends Ente {
 
    public StockEnte(String name) {
        super(name, new Fluegelschlagen());
    }
 
    public void anzeigen() {
        System.out.println("Ich bin eine echte Stockente");
    }
}
```

```java
package duckSim;

public class MoorEnte extends Ente {
 
    public MoorEnte(String name) {
        super(name, new Gleiten());
    }
 
    public void anzeigen() {
        System.out.println("Ich bin eine echte Moorente");
    }
}
```

```java
package duckSim;

public class GummiEnte extends Ente {
 
    public GummiEnte(String name) {
        super(name, new NichtFliegen());
    }
 
    public void anzeigen() {
        System.out.println("Ich bin eine Gummi-Ente");
    }
}
```
### Main

#### MainEntenSimulator.java

```java
package duckSim;

import java.util.ArrayList;

public class MainEntenSimulator {
 
    public static void main(String[] args) {
 
        ArrayList<Ente> meineEntchen = new ArrayList<Ente>();
        
        meineEntchen.add(new StockEnte("MeinStockEnte"));
        meineEntchen.add(new GummiEnte("MeinGummiEnte"));
        meineEntchen.add(new MoorEnte("MeinMoorEnte"));

        for(Ente e: meineEntchen) {
            System.out.print("Ich bin " + e.getName() + ". ");
            e.anzeigen();
            e.tuFliegen();
        }
        
        // Verhalten zur Laufzeit ändern
        meineEntchen.get(3).setFlugVerhalten(new RaketenAntriebsFliegen());
        
        for(Ente e: meineEntchen) {
            System.out.print(e.getName() + " macht jetzt: ");
            e.tuFliegen();
        }
    }
}
```


## Refactoring Hinweise
- **Zu viele Konstruktorparameter**: Klasse aufteilen, Facade Pattern (noch nicht gelernt), Builder (auch noch nicht) oder Parameter Object verwenden.
- **Schnittstelle fordert Standard-Konstruktor**: Adapter-Pattern (Wrapper). (auch noch nicht)

## Design Principles
- Open Closed Principle: Offen für Erweiterung aber geschlossen für Änderung
- Dependency INVERSION (immer vom Interface abhängen)
- Composition over Inheritance: Man muss nicht immer Vererbung machen, wo Komposition besser ist
- Encapsulate What Varies: Sachen die sich ändern von Konstante Sachen trennen
- Program to Interface, not to Implemntation (dann kannst du eine zweite Klasse die den selben Interface implemntiert einbauen, und mit der urprungliche tauschen ohne dass du alle andere Sachen anpassen musst)

## Moodle

#### Unit Testing (Übung)
- Dependency Injection macht das Testen einfach => Wahr
- Eine Test-Methode sollte nur eine Sache testen, kann aber dafür mehrere Asserts verwenden => Wahr 
- **Merken:** Die Law of Demeter sagt aus, dass **Methoden** mit ihren **Parametern** nach den **Argumenten** fragen, die sie **direkt** für ihre Aufgabe benötigen

- Was ist ein friendly: 
	- Mock-Objekte
	- Objekte bereits getesteter Klassen
	- Dummy Objekte, welche NULL Pointer Exceptions verhindern

- Unit Tests:
	- Die IDE kann aus allen JUnit-Tests einen "Coverage-Report" erstellen.
	- Sie sind die Bausteine von "Regressionstests".
	- Sie sollten nach jeder fertigen Code-Modifikation laufen.
	- Werden automatisch ausgewertet.
	- Sie sind schnell.
- Sachen die Unit Tests schwierig machen:
- Wählen Sie alle Punkte aus, die Unit-Testen schwierig machen.
	- mixing Service and Value in one class
	- static methods, that call other methods 
	- too many conditionals 
	- doing "work" in the constructor 
	- looking for things
	- mixing new with business logic
	- deep inheritance
	- global state 

- Wenn man beim Testen NULL übergibt, dann sagt das aus, dass dieser Teil für diesen Test nicht relevant ist => Wahr
- Gute Test-Methodennamen beschreiben, was getestet wird => Wahr
- Objekterstellung gehört in **Factory Klassen**

#### Unit Testing (SLÜ)
- Testet aus Sicht des Users => Systemtests (Scenariotest)
- Schlägt dieser Test fehl, kann man nur mit sehr viel Aufwand den Fehler lokalisieren.  => Systemtests (Scenariotest)
- Sie sind sehr schnell => Unit Tests
- Sie sind sehr groß  => Systemtests (Scenariotest)
- Gelingt dieser Test so ist man sehr sicher, dass die Anwendung funktoniert  => Systemtests (Scenariotest)
- Die ganze Anwendung Wird in der Gesamtheit getestet  => Systemtests (Scenariotest)
- Die Abhängigkeiten zwischen einzelnen Klassen (meist in
- einem package) werden getestet => Funktionstests (Functional tests)
- Testet immer nur eine Klasse => Unit Tests
- Sie sind unzuverlässig  => Systemtests (Scenariotest)
--- 
- SRP Steht für **single responsibility principle** und bedeutet
	- Klassen sollten **nur eine Verantwortung übernehmen**
	- Test Methoden sollten immer nur einen **Sachverhalten Testen**
---
- Dependency Injection erschwert das Testen => FALSCH
---

- Welche der folgenden Sachverhalte erschweren das Testen mit JUnit? korrekt sind: 
	- Mischung von Serviceaufgaben und Stammdatenverwaltung in einer Klasse 
	- static Methoden (die keine "leaf-Methoden Sind) 
	- deep inheritance (tiefe Vererbungsstrukturen) 
	- Verletzung der "Law of Demeter" 
	- "business-logic" (produktiver Code) im Konstruktor 
	- Zu viele Verzweigungen in einer Methode
	- Objekterstellung mit new innerhalb von Methoden. 
	- globale Variablen
---
- **Merke:** Law of Demeter unterstützt das Testen, indem Signaturen durch Parameter nach dem fragen, was direkt zum Erfüllen der Aufgabe wird.
---
- Eine Test Methode darf nur eine assert Methode enthalten => Falsch

- Wähle alle Antworten aus, die auf Regressionstests zutreffen.
	- Sie sind Bestandteil von "continuous integration". 
	- In der Regel werden sie mit Unit-Tests durchgeführt. 
	- Sie überprüfen, ob neuer Oder geänderter Code Fehler in bereits bestehendem und getesteten Code bewirken. 
---
- Test-Methodennamen müssen auf jeden Fall kurz gehalten werden, aber den Namen der zu testenden Klasse enthalten => FALSCH
---
- Markieren Sie alle richtigen Vervollständigungen des folgenden Satzes "Das Schlüsselwort new gehört": richtig sind:
	- in eine Factory Klasse 
	- nicht in produktiven Code
---
- Das SRP sagt aus, dass eine Test-Klasse nur eine Test-Methode enthalten sollte => FALSCH
---
- Was ist ein friendly. Wähle jede Antwort, die zutrifft.
	- Objekte bereits getesteter Klassen 
	- Mock-Objekte 
	- Dummy-Objekte, welche NIJLL-Pointer-Exceptions verhindern 

## SLÜ Singleton
- Das Singleton Pattern verhindert die Vererbung => Wahr
- Das Singleton Pattern ist eine Art globale Variable => Wahr
- Die Law of Demeter sagt aus, dass **Methoden** mit ihren **Parametern** nach den Argumente fragen, die sie **direkt** für ihre Aufgabe benötigen.
- Um eine Singleton-Klasse (nach dem Entwurfsmuster programmiert) zu testen, muss man dependency injection in den Konstruktor einbauen => FALSCH
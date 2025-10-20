# JUnit
## Was ist JUnit

- **Framework zum Testen von Java-Programmen**
- Ermöglicht schnelles Schreiben von **Unit-Tests**
- **Unit-Test**: Test einzelner Programmteile (Module) – in der OOP meist Test einzelner **Klassen und Methoden**

## Warum sollte man JUnit verwenden

- **Regressionstesten**: Tests nach jeder Codeänderung, um **Integrität** des Programms sicherzustellen und **Seiteneffekte** zu vermeiden.
- **Test-driven development (TDD)**: Erst Tests schreiben, dann implementieren. Verhindert das Übersehen von Testfällen.

## Der JUnit-Test – Funktionsweise

- **JUnit-Tests** sind eigenständige **Java-Klassen**.
- Sollen **erkennbare Namen** tragen, z. B. `LogicController` → `LogicControllerTest`.
- Sinnvolle Trennung in der Ordnerstruktur, z. B. `/src/mitarbeiter` (Programmcode) → `/src/tests/mitarbeiter` (Testklassen).
- **Testklassen** enthalten speziell gekennzeichnete Methoden.
- Kernstück: **@Test-annotierte Methoden** stellen einzelne Testfälle dar.

### Mögliche Testergebnisse

- **grün**: Test gelingt.
- **rot**: Test misslingt.
- **blau**: wenn `fail()` aufgerufen wird (kein korrekter Durchlauf).

**Misslingen** hat zwei Gründe:
1. **Failures** (erwartete Fehler): Testfall gescheitert.
2. **Errors** (unerwartete Fehler): kein korrekter Durchlauf.
Erwartete Fehler werden über die Klasse **AssertionError** realisiert.

## Annotation von Methoden

- **JUnit verwendet Java-Annotations**, vor die Methoden geschrieben werden.
- **Setup-Methoden**:
    - `@BeforeAll`: wird vor allen Tests (statisch) aufgerufen.
    - `@BeforeEach`: wird vor jedem Test aufgerufen.
- **Teardown-Methoden**:
    - `@AfterAll`: wird nach allen Tests (statisch) aufgerufen.
    - `@AfterEach`: wird nach jedem Test aufgerufen.
- **@Disabled**: markiert ignorierte Methoden (nicht im Testlauf enthalten).
- **@Test**: wichtigste Annotation, deklariert einen Testfall. Testmethoden sind **void**, haben **keine Parameter** und können beliebig viele Bedingungen prüfen.
## Ablauf eines Tests

1. `@BeforeAll`-Methoden ausführen.
2. Instanz der Testklasse erzeugen.
3. `@BeforeEach`-Methoden ausführen.
4. `@Test`-Methode ausführen.
5. `@AfterEach`-Methoden ausführen.
6. `@AfterAll`-Methoden ausführen.
7. Instanz wieder freigeben.

**Hinweis**: Die Reihenfolge der Tests ist **nicht vorhersehbar** (JUnit scheint alphabetisch nach Methodennamen vorzugehen).

## Assertmethoden

- Zweck: Überprüfung der Ergebnisse der getesteten Klasse.
- **assertTrue(boolean condition)**
- **assertNull(Object object)**
- **assertEquals(TYPE expected, TYPE actual)**
- **assertEquals(double expected, double actual, double delta)**
- **assertArrayEquals(TYPE[] expected, TYPE[] actual)**
- **assertSame(Object expected, Object actual)**
- **assertThrows(Class expectedType, Executable executable)**
- Jede Variante existiert auch mit `String message` als zusätzlicher Parameter.

**assertThrows** prüft, ob eine bestimmte **Exception** (z. B. `IllegalArgumentException.class`) ausgelöst wird, wenn die übergebene Methode (Lambda oder anonyme Klasse) aufgerufen wird.

## Test-Beispiel

### Zu testende Klasse

`BueroArbeiter` (Beispielcode vollständig in der Präsentation enthalten).

### Testklasse (Ausschnitte)

```java
@BeforeEach
void setUp() throws Exception {
    bmGood = new BueroArbeiter(5234, "Erna", 2000);
}

@Test
void testIfIDisAdaptedCorrectly() {
    bmBad = new BueroArbeiter(1111, "Al", 3000);
    assertEquals(5111, bmBad.getID(), "ID 1111 was not adapted correctly");
    bmBad = new BueroArbeiter(0, "Al", 3000);
    assertEquals(5000, bmBad.getID(), "ID 0 was not adapted correctly");
}

@Test
void testIfMinimumWage300IsGuaranteed() {
    assertThrows(IllegalArgumentException.class,
        () -> bmBad = new BueroArbeiter(5111, "Al", 299),
        "The wage of 299 was accepted. It should be greater than 300.");
    bmBad = new BueroArbeiter(5111, "Al", 3000);
    bmBad.setFestgehalt(300);
    assertEquals(300, bmBad.getFestgehalt(),
        "The wage of 300 was not accepted, but it should have been.");
    assertThrows(IllegalArgumentException.class,
        () -> bmBad.setFestgehalt(299),
        "The wage of 299 was accepted. It should be greater than 300.");
}
```

### Testausführung in Eclipse

- **Erfolgsfall**: Alle Tests grün.
- **Fehlerfall**: Ausgabe von Fehlern mit Zeilenangaben.

## Coverage

- **Zweig-Abdeckung** als Teil von **White Box Tests**.

## Richtlinien für gute JUnit-Tests (FIRST-Principles)

- **F**ast
- **I**solated / Independent
- **R**epeatable
- **S**elf-validating
- **T**imely

### Wert von Testcode

- Erlaubt Änderungen an der **Software-Architektur**, ohne das Verhalten zu beschädigen.
- Gute Tests dienen als **Dokumentation**:
    - Wie Klassen verwendet werden.
    - Erwartete Daten.
    - Exceptions und Systeminteraktionen.
    - Kundenerwartungen.

### Regeln nach Tobias Goeschel

1. **Teste Verhalten, nicht Implementation**
    - Triple-A-Prinzip: **Arrange** (Vorbedingungen), **Act** (Aktion), **Assert** (Ergebnis).
2. **Single Responsibility Principle (SRP)** für Tests: Jede Testmethode überprüft genau eine Sache.
3. **Sprechende Namen** für Testmethoden.
4. **Vermeide komplexe Konfigurationen**.
5. **Keine Vererbung** von Testklassen (Wiederverwendung über Komposition).
6. **Tests nach Kontext gruppieren**, z. B. interne Klassen mit gleichem Setup.

## Extra: Testen von Konsolen-Output

- Einsatz von **ByteArrayOutputStream**, `System.setOut` und `System.setErr`, um Ausgaben zu prüfen.


# The Clean Code Talks: Unit Testing (Miško Hevery)

## Mr. Testable vs. Mr. Untestable

Unterschied zwischen **testbarem** und **schwer testbarem** Code.

## Ursachen für schwer testbaren Code

- Häufig vermutete Gründe (falsch): viele private Methoden, `final`-Keyword, lange Methoden.
- **Tatsächliche Probleme**:
    - Vermischung von **Objekterzeugung** mit **Logik**    
    - Suchen von Objekten
    - Arbeit im Konstruktor
    - **Globaler Zustand**
    - **Singletons**
    - **Static Methods**
    - Tiefe Vererbung
    - Zu viele Bedingungszweige
    - Vermischung von **Service** und **Value Objects**
    - Vermischung von Verantwortlichkeiten

## Zentrale Aussage
Es gibt kein Geheimnis für das Schreiben von Tests, nur für **testbaren Code**.
## Progression des Testens

1. **Scenario/Large Tests**:
    - Ganze Anwendung simuliert Benutzeraktionen.
    - **Langsam** und **flaky**, hohe Anfangsabdeckung, aber schwierig für Randfälle.
    - Fehler schwer reproduzierbar, Debugger nötig.

2. **Functional/Medium Tests**:    
    - Test von Subsystemen mit simulierten externen Abhängigkeiten.
    - **Schneller**, weniger fehleranfällig, erleichtert das Reproduzieren von Fehlern.

3. **Unit/Small Tests**:
    - Test einzelner Klassen in Isolation.
    - **Sehr schnell**, keine Flakiness, einfach zu reproduzieren.

- Alle Testebenen sind **wichtig**, aber kleinere Tests brauchen **mehr Anzahl**, da sie weniger abdecken.
## Beispiel: Flashlight-Test

- Wahrscheinlichkeit für Fehler:
    - Flashlight 100 %
    - Light Bulb 50 %
    - Battery 45 %
    - Switch 4 %
    - Connectors 1 %

## Unit Testing einer Klasse

- **Test Driver** ruft **Class Under Test** auf.
- Objekte können
    - **instanziiert**
    - **übergeben**
    - **global** sein.
- Wichtig: **Trennung von Objektgraph-Konstruktion und Business-Logik**.

## Tipps für testbaren Code

- **Trick 1: Ask for things**
    - Keine direkte Instanziierung.
    - Keine Arbeit im Konstruktor.
    - Abhängigkeiten injizieren.
- **Trick 2: Avoid Global Mutable State**
    - Schlechte vs. gute Singletons.
- **Trick 3: Avoid Deep Inheritance Hierarchies**
    - Komposition statt Vererbung.
    - Polymorphismus statt verschachtelter Bedingungen.

# Law of Demeter (Miško Hevery)

## Grundidee
- **Law of Demeter (LoD)**: Ein Objekt darf nur mit direkt benötigten Objekten sprechen.
- Beispiel: An der Kasse **25 $** zahlen:
    - Richtig: 25 $ geben.
    - Falsch: Wallet geben und Kassierer holt Geld.
## Verletzung des LoD

- Beispielcode `Goods.purchase(Customer c)` ruft `c.getWallet().getMoney()` auf.
- Test erfordert komplexe Objekte (Customer, Wallet, Money), um an das Geld zu kommen.

## Korrekte Einhaltung

- Methode `purchase(Money m)` erhält direkt das benötigte Objekt `Money`.
- Test wird einfacher und klarer.

## Prinzipien

- Keine Kettenaufrufe wie `a.getX().getY()`.
- Kein `serviceLocator.getService()`.
- **Dependency Injection** statt Suchen von Abhängigkeiten.
- **Hollywood Principle**: „Don’t call us, we’ll call you.“

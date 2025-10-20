# Singleton Pattern

## Ziel

- Es darf **nur eine Instanz** eines Objekts im gesamten Programm geben.  
- „Es kann nur einen geben.“

## Implementierungstechniken

### Lazy Creation

```java
public final class Unsterblicher {
    private int geburtsjahr;
    private int anzahlLeben;
    private static Unsterblicher instance;
    private Unsterblicher() {}
    public static Unsterblicher getInstance() {
        if (instance == null)
            instance = new Unsterblicher();
        return instance;
    }
}
```

- Instanz wird bei Bedarf erzeugt.
- **Problematisch bei Threads**.

### Eager Creation

```java
public final class Unsterblicher {
    private int geburtsjahr;
    private int anzahlLeben;
    private static final Unsterblicher INSTANCE = new Unsterblicher();
    private Unsterblicher() {}
    public static Unsterblicher getInstance() {
        return INSTANCE;
    }
}
```

- Vorteil: **kein synchronized** nötig.

## Kritik: Singleton als Anti-Pattern

- Ersetzt **globale Variablen** → führt zu **prozeduralem Programmieren**.    
- **Keine Datenkapselung**.
- **Versteckte Abhängigkeiten**, da **Dependency Injection** nicht möglich.
- **Testen kompliziert**, Mocking erschwert.
- **Erweiterungen schwierig**.
- Keine **Vererbung** möglich (privater Konstruktor).
- Overhead für **Threadsicherheit** und **dynamische Bibliotheken**.
- Exzessive Nutzung führt zu höherer Laufzeit ohne Gewinn.
- In Java nicht vollständig garantiert, da `static`-Variablen nur **pro ClassLoader** einzigartig sind.
## Quellenhinweise

- Diskussionen auf StackOverflow, gameprogrammingpatterns.com, Blog jalf.dk, Wikipedia.
- Zitat: _„I can't think of a single situation where a singleton is the right solution.“_ – jalf.dk.

# The Clean Code Talks: Global State and Singletons (Miško Hevery & Jonathan Wolter)

## Global State

- **Definition**: Zustand, der sich über die Lebensdauer der JVM erstreckt und nicht von einzelnen Objekten kontrolliert wird.
- Probleme:
    - **Flakiness**: Mehrfachausführungen können unterschiedliche Ergebnisse liefern.
    - **Testreihenfolge beeinflusst Ergebnis**.
    - **Parallelisierung unmöglich**.
- Beispiele: `System.currentTime()`, `new Date()`, `Math.random()`.
## Singleton – Good vs. Bad

- Häufige Fehlannahme: **Application Global = JVM Global**.
- In Tests ist wichtig: **Application Global ≠ JVM Global**.

### Schlechter Singleton

```java
class AppSettings {
    private static AppSettings instance = new AppSettings();
    private Object state1, state2, state3;
    private AppSettings() { ... }
    public static AppSettings getInstance() {
        return instance;
    }
}
```

- Tests können **internen Zustand** nicht isoliert prüfen.
- Interner Zustand wird **global zugänglich**.
- Problem: **static instance** mit transitivem globalem Verhalten („Static Cling“).

### Besserer Ansatz

```java
class App {
    AppSettings settings;
    App(AppSettings settings) {
        this.settings = settings;
    }
    int method() {
        return settings.doX();
    }
}
```

- **Dependency Injection** erlaubt einfache Tests.

## Deceptive API

- Eine API, die **nicht offenlegt**, welche Abhängigkeiten sie tatsächlich benötigt.
- Beispiel: `CreditCard.charge()` benötigt in Wirklichkeit `CreditCardProcessor`, verrät es aber nicht.
- Folge: **NullPointerExceptions**, „spooky action at a distance“.
### Lösung

- **Dependency Injection** erzwingt korrekte Initialisierungsreihenfolge **zur Compile-Zeit**.
- Jede Schicht kann isoliert getestet werden.

## Review

- **Global state ist die Wurzel aller Testprobleme**.
- Tests können globalen Zustand nicht kontrollieren.
- **Singletons** kapseln oft globalen Zustand und verschärfen diese Probleme.
- Nur Singletons, die ihre **Singleton-ness** selbst erzwingen, sind kritisch.

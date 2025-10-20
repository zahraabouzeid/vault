# LS22B – Singleton Pattern und Global State

## 1. Singleton Pattern

### Grundidee
„Es darf nur einen geben.“ Das Muster stellt sicher, dass **nur eine Instanz** einer Klasse existiert und global zugreifbar ist.

### Implementierungsvarianten

#### Lazy Creation
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
- Instanz wird bei Bedarf erzeugt.
- Nicht thread-sicher.

#### Eager Creation
```java
public final class Unsterblicher {
    private static final Unsterblicher INSTANCE = new Unsterblicher();
    private Unsterblicher() {}
    public static Unsterblicher getInstance() {
        return INSTANCE;
    }
}
```
- Instanz wird sofort erzeugt.
- Kein `synchronized` nötig.

### Kritikpunkte (Singleton als Anti-Pattern)
- Ersetzt **globale Variablen**, führt zu versteckten Abhängigkeiten und prozeduralem Stil.
- Erschwert **Dependency Injection**, Mocking und Unit-Tests.
- **Private Konstruktoren verhindern Vererbung.**
- Erhöhte Komplexität bei Threads und dynamischen Bibliotheken.
- In Java nicht absolut sicher (ClassLoader können mehrere Instanzen erzeugen).
- Übermäßiger Einsatz kann Performance verschlechtern.

---

## 2. The Clean Code Talks – Global State and Singletons (Misko Hevery)

### Global State – Hauptproblem
- Identische Operationen liefern unterschiedliche Ergebnisse (**nicht-deterministisch**).
- Tests werden **flaky**: Ergebnisse hängen von Ausführungsreihenfolge oder paralleler Ausführung ab.
- Beispiele: `System.currentTime`, `new Date()`, `Math.random()` (Seed als versteckter Zustand).

### Singletons als globaler Zustand
- Klassisches Singleton (`private constructor`, `static getInstance`) bindet Objekte an die JVM-Laufzeit.
- Das globale Instanzfeld macht alle abhängigen Objekte **transitiv global**.
- Tests können Objekte weder sauber instanziieren noch deren Zustand kontrollieren oder zurücksetzen.
- Workarounds wie spezielle Setter für Tests untergraben das Muster.

### Beispiele für Risiken
- APIs mit **versteckten Abhängigkeiten**: z. B. `CreditCard.charge(100)` benötigt intern `CreditCardProcessor`, `OfflineQueue`, `Database`.
- Fragile Initialisierungen im `main()`; kleine Änderungen können Systeme lahmlegen.

### Empfehlungen
- **Dependency Injection**: Jede Klasse deklariert explizit ihre Abhängigkeiten im Konstruktor.
- So wird die **Reihenfolge der Initialisierung beim Kompilieren geprüft** und Tests werden reproduzierbar.

### Wichtige Unterscheidung
- **Singleton (großes S)**: klassisches Muster mit privatem Konstruktor und globalem Instanzfeld (**problematisch**).
- **singleton (kleines s)**: Objekt wird nur einmal erzeugt, **ohne** erzwungenen globalen Zustand (**unproblematisch**).

### Fazit
- Globaler Zustand ist für ca. 90 % aller Testprobleme verantwortlich.
- Singletons sind „global state in sheep’s clothing“ und sollten zugunsten von Dependency Injection vermieden werden.

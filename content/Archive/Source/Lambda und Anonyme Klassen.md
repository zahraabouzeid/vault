## Was ist eine innere Klasse?
Eine innere Klasse ist eine Klasse, die innerhalb einer anderen Klasse definiert wird. Sie hat besondere Eigenschaften:
- **Zugriff auf alle Member** der äußeren Klasse (auch private)
- **Keine static-Member** (außer bei static nested classes)
- **Benötigt Instanz** der äußeren Klasse (außer static nested classes)

**Beispiel:**
```java
class Smartphone {
    private String modell = "Galaxy S21";
    
    // Innere Klasse
    class Akku {
        void ladeStatus() {
            System.out.println("Ladezustand für " + modell); // Zugriff auf äußeres Feld
        }
    }
}
```

## 2. Arten innerer Klassen

#### a) Statische Nested Class
**Eigenschaften:**
- Mit `static` deklariert
- Kein Zugriff auf nicht-statische Member der äußeren Klasse
- Wird wie eine normale Klasse verwendet

**Wann verwenden?**
Für logisch zusammengehörige Klassen, die unabhängig von Instanzen sind.

**Beispiel:**
```java
class Mathematik {
    static class Rechner {
        static int quadrat(int x) {
            return x * x;
        }
    }
}

// Aufruf:
int ergebnis = Mathematik.Rechner.quadrat(5);
```

#### b) Nicht-statische Innere Klasse (Member Inner Class)
**Eigenschaften:**
- Hat Zugriff auf alle Member der äußeren Klasse
- Benötigt Instanz der äußeren Klasse

**Wann verwenden?**
Für enge Kopplung, z.B. bei Event-Handlern oder Iteratoren.

**Beispiel:**
```java
class Auto {
    private String kennzeichen;
    
    class Motor {
        void starten() {
            System.out.println(kennzeichen + ": Motor startet");
        }
    }
}

// Verwendung:
Auto meinAuto = new Auto();
Auto.Motor motor = meinAuto.new Motor();
```

#### c) Methoden-lokale Innere Klasse
**Eigenschaften:**
- Innerhalb einer Methode definiert
- Nur innerhalb der Methode sichtbar
- Zugriff nur auf final/effectively final lokale Variablen

**Wann verwenden?**
Für sehr spezifische, einmalige Implementierungen.

**Beispiel:**
```java
class Spiel {
    void starte() {
        class SpielRegeln {
            void zeigeRegeln() {
                System.out.println("Spielregeln...");
            }
        }
        
        new SpielRegeln().zeigeRegeln();
    }
}
```

#### d) Anonyme Innere Klasse
**Eigenschaften:**
- Kein Klassenname
- Wird bei Instanziierung definiert
- Implementiert ein Interface oder erweitert eine Klasse

**Wann verwenden?**
Für kurze, einmalige Implementierungen (vor Java 8).

**Beispiel:**
```java
button.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent e) {
        System.out.println("Button wurde geklickt");
    }
});
```

## 3. Lambda Expressions (ab Java 8)
**Eigenschaften:**
- Kurzschreibweise für funktionale Interfaces
- Kein eigener Scope wie anonyme Klassen
- Keine eigenen Methoden oder Felder möglich

**Wann verwenden?**
Für einfache Implementierungen funktionaler Interfaces.

**Beispiel:**
```java
// Vorher mit anonymer Klasse:
button.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent e) {
        handleClick();
    }
});

// Nachher mit Lambda:
button.addActionListener(e -> handleClick());
```

## 4. Vergleichstabelle

| Feature                | Innere Klasse | Anonyme Klasse | Lambda |
|------------------------|---------------|----------------|--------|
| Name                   | Ja            | Nein           | Nein   |
| Konstruktor            | Ja            | Nein           | Nein   |
| Mehrere Methoden       | Ja            | Ja             | Nein   |
| Zugriff auf äußere Variablen | Ja (alle) | Ja (nur final) | Ja (nur final) |
| Funktionales Interface benötigt | Nein | Nein | Ja |


## Wann was verwenden?

| Situation | Empfehlung | Beispiel |
|-----------|------------|----------|
| Mehrfache Verwendung | Innere Klasse | Custom Event-Handler |
| Einmalige Implementierung | Anonyme Klasse | Einmaliger Comparator |
| Funktionales Interface | Lambda | ActionListener |
| Komplexe Logik (>1 Methode) | Anonyme Klasse | Adapter mit mehreren Methoden |
| Zugriff auf äußere Felder | Nicht-statische innere Klasse | Iterator-Implementierung |

## Wichtige Begriffe

| Begriff                | Erklärung                              | Beispiel                        |
| ---------------------- | -------------------------------------- | ------------------------------- |
| Effectively final      | Variable die nicht mehr geändert wird  | Lokale Variablen in Lambdas     |
| Shadowing              | Verdeckung gleichnamiger Variablen     | Innere vs. äußere name-Variable |
| Funktionales Interface | Interface mit einer abstrakten Methode | Runnable, ActionListener        |


Hier ist die ausführliche Zusammenfassung zu **Interfaces in Java**, basierend auf Frau Rollins’ Präsentation **„LS5 B Interfaces“**:

---

## 🎭 **Interfaces in Java – die elegante Lösung für Vielseitigkeit**

---

### ❌ Problem in anderen Sprachen: **Mehrfachvererbung (C++)**

- In Sprachen wie C++ können Klassen **mehrere Oberklassen erben**.
    
- Das führt zu **Konflikten**: z. B. welche `setName()` Methode wird aufgerufen?
    
- → **Diamond Problem** ("Black Diamond Problem"): zwei Basisklassen vererben die gleiche Methode an eine Klasse – Mehrdeutigkeit entsteht.
    

---

### ✅ **Java sagt: Keine Mehrfachvererbung, aber…**

- ...wir haben **Interfaces**! 💡
    
- Damit kann eine Klasse **mehrere Fähigkeiten (Interfaces)** implementieren, **ohne** Mehrdeutigkeiten.
    

---

### 📦 **Was ist ein Interface?**

- Ein Interface ist eine **reine Vertragsschnittstelle** – es enthält **nur Methodenköpfe**, keinen Code.
    
- Methoden sind **automatisch `public` und `abstract`**.
    
- Interfaces haben **keine Konstruktoren** oder Zustände (Attribute).
    

---

### 🛠️ **Beispiel: Zeichenbar und Fuellbar**

```java
public interface Zeichenbar {
    void zeichnen(double x, double y);
}

public interface Fuellbar {
    void fuellen(int farbe);
}
```

```java
class Kreis extends Figur2D implements Zeichenbar, Fuellbar {
    private double radius;

    public void zeichnen(double x, double y) {
        // Code zum Zeichnen an Position x, y
    }

    public void fuellen(int farbe) {
        // Code zum Füllen mit Farbe
    }
}
```

---

### 🧠 **Key Facts**

|Eigenschaft|Interface|Abstrakte Klasse|
|---|---|---|
|Attribute|❌ keine|✅ möglich|
|Methoden|nur Methodenköpfe (keine Bodies)|kann Methodenkörper haben|
|Konstruktoren|❌ keine|✅ möglich|
|Mehrfachverwendbar|✅ mehrere Interfaces möglich|❌ nur eine Klasse erweiterbar|
|Modifizierer|Methoden sind automatisch: `public abstract`||

---

### 🔐 **Syntax & Besonderheiten**

- `implements` statt `extends`
    
- Mehrere Interfaces per Komma getrennt
    
- Interface selbst steht in **eigener Datei**
    
- **kein Code in Interfaces!** Nur "Was muss die Klasse können?"
    

---

### 🧪 **Typische Klausuraufgaben**

- **Interface entwerfen** für eine Funktionalität (z. B. `Speicherbar`, `Druckbar`, `Verleihbar`)
    
- Eine Klasse implementiert mehrere Interfaces
    
- UML-Diagramm: gestrichelte Pfeile mit offener Spitze
    
- Begründen, warum man Interfaces statt abstrakter Klassen nutzt
    

---

### 💬 Frau Rollins’ Takeaways

> "Interfaces sind der Java-Weg, die Vielseitigkeit von Objekten zu ermöglichen – ohne sich im Erbendschungel zu verlieren."

---

Als Nächstes analysiere ich **„LS5 C Generics, Collections und Maps“** – das wird direkt super relevant für ca. 80 % der Kannliste. 🧠📚⚔️ Ich melde mich gleich wieder!
Hier ist die erste **vollständige Zusammenfassung** zum Thema **`static` in Java**, basierend auf Frau Rollins' Präsentation **„LS5 A static“**:

---

## 🧠 **Thema: `static` – Klassenvariablen und -methoden**

### 🔍 **Worum geht’s?**

Wenn **eine Information für alle Objekte einer Klasse** gleich ist (z. B. ein Zähler), soll diese **nicht mehrfach pro Objekt gespeichert werden**, sondern **einmal zentral** – in einer sogenannten `static` Variable.

---

### 🧩 **Beispiel-Szenario: Mitarbeiter**

- Jeder neue Mitarbeiter bekommt eine eindeutige ID.
    
- Die ID soll automatisch hochzählen.
    
- Dafür braucht man einen Zähler – aber **nicht pro Objekt!**
    
- Lösung: **`static int anzahl`**
    

---

### 🧱 **Unterschied: `static` vs. nicht-`static`**

|Merkmal|`static`|nicht-`static`|
|---|---|---|
|Speicherort|einmalig in der **Klasse**|in jedem **Objekt**|
|Zugriff|über **Klasse oder Objekt**|nur über **Objekt**|
|Beispiel-Variable|`private static int anzahl;`|`private String name;`|
|Beispiel-Methode|`public static int getAnzahl()`|`public String getName()`|
|Verwendung in UML|**unterstrichen**|normal|
|Zugriff durch Methoden|`static` Methoden → nur auf `static` Daten|nicht-`static` → auch auf Objektattribute|

---

### ✅ **Code-Beispiel**

```java
public class Mitarbeiter {
    private int id;
    private String name;
    private static int anzahl = 0;

    public Mitarbeiter(String name) {
        this.name = name;
        anzahl++; // wird bei jedem neuen Objekt erhöht
        this.id = 10000 + anzahl;
    }

    public static int getAnzahl() {
        return anzahl;
    }

    // Getter & Setter für name & id (ohne setAnzahl!)
}
```

---

### 🧠 **Wichtig für die Klausur**

- `static` Variablen: **Zentral für alle Objekte** (z. B. Zähler, Konfiguration)
    
- `static` Methoden: **arbeiten ohne Objekt**, also ohne `this`
    
- **Kein Zugriff auf Objektattribute** in `static` Methoden!
    
- UML: `static` = **unterstrichen**
    
- Korrektes Setzen im Konstruktor, **kein setAnzahl() notwendig**
    

---

### 🧪 Typische Klausurfrage

> Gib ein Klassendiagramm an, das eine `static` Variable enthält (z. B. `+getAnzahl() : int`)  
> oder  
> Ergänze eine Klasse so, dass IDs automatisch vergeben werden und `getAnzahl()` korrekt funktioniert.

---

Als Nächstes: **LS5 B Interfaces** – ich bin dran! 🧩✨
Hier ist die Zusammenfassung zur vierten Präsentation: **„T DS0 – Dynamische Arrays“**, mit Fokus auf Speicher, Arrays und wie man sie manuell vergrößert. 📦💾

---

## 🧮 **Dynamische Arrays in Java**

---

### 🧠 **Was ist ein Array?**

- Ein Array ist ein **statischer Speicherbereich**: einmal erstellt, ist die **Größe fix**.
    
- → Wenn du mehr Elemente brauchst, musst du ein **neues, größeres Array erstellen**.
    

---

### 💡 **Beispiel: Eingabe von Zahlen unbekannter Länge**

```java
int size = 0, anz = 0, step = 10;
Integer[] array = null, temp = null;
int zahl;

do {
    zahl = tool.nextInt();

    // Array voll? Dann vergrößern!
    if (anz >= size) {
        temp = new Integer[size + step];
        for (int i = 0; i < array.length; i++) {
            temp[i] = array[i];
        }
        array = temp;
        size += step;
    }

    array[anz++] = zahl;

} while (zahl != 0);
```

---

### 🧩 **Variablen im Beispiel**

|Variable|Bedeutung|
|---|---|
|`size`|aktuelle Größe des Arrays|
|`anz`|Anzahl der tatsächlich gespeicherten Werte|
|`step`|wie stark das Array bei Bedarf wächst|
|`array`|das eigentliche Integer-Array|
|`temp`|Zwischenspeicher für das neue Array|

---

### 🧠 **Wichtig zu verstehen: Heap vs. Stack**

- **Stack**: für lokale Variablen und Methodenaufrufe
    
- **Heap**: für Objekte, also auch Arrays, die mit `new` erzeugt wurden
    
- `new Integer[size]` legt ein neues Array im **Heap** an
    
- das alte Array wird bei `array = temp;` durch das neue ersetzt (das alte wird von der Garbage Collection eingesammelt)
    

---

### 📌 **Merkmale dynamischer Arrays**

- Vergrößerung erfolgt **manuell**
    
- Muss alte Werte **kopieren**
    
- Speicherplatz wächst in **Blöcken** (`step`)
    
- **nicht effizient**, aber **wichtiges Grundverständnis**
    

---

### 🔬 **In der Klausur denkbar:**

- Codeanalyse: Wo wird das Array vergrößert?
    
- Welche Variablen regeln was?
    
- Eigenes dynamisches Array implementieren
    
- Vorteile/Nachteile erklären gegenüber z. B. `ArrayList`
    

---

**Nächstes Thema:** `T DS1 – Verkettete Listen`  
→ Jetzt geht’s an die typischen Datenstrukturen aus der Theorieprüfung – let’s go! 🔗🧠
Hier ist die Zusammenfassung zu **„T DS1 – Verkettete Listen“**, also dem Klassiker unter den Datenstrukturen. 🔗💡

---

## 🧩 **Verkettete Listen (Singly Linked Lists)**

---

### 🧠 **Was ist das?**

- Eine **verkettete Liste** besteht aus einzelnen **Knoten (Nodes)**.
    
- Jeder Knoten hat:
    
    - einen **Datenbereich** (z. B. `String name`, `int id`)
        
    - einen **Verweis auf das nächste Element**
        

---

### 🧱 **Struktur**

```java
class Node {
    String data;
    Node next;
}
```

- Das **erste Element** nennt man **Kopf** (head)
    
- Das **letzte Element** verweist auf `null`
    

---

### 🔁 **Traversieren / Durchlaufen**

```java
Node aktuell = head;
while (aktuell != null) {
    System.out.println(aktuell.data);
    aktuell = aktuell.next;
}
```

---

### ➕ **Einfügen eines neuen Elements (z. B. an Position 2)**

1. Speicherplatz für neues Element anlegen
    
2. Neues Element zeigt auf das aktuelle 2. Element (`neu.next = alt2`)
    
3. Das bisherige 1. Element zeigt auf das neue Element (`alt1.next = neu`)
    

---

### ➖ **Löschen eines Elements (z. B. das 2.)**

1. Das 1. Element wird angepasst: `alt1.next = alt2.next`
    
2. Das 2. Element ist „verloren“ und kann von der Garbage Collection entfernt werden
    

---

### 🔍 **Suchen eines Elements**

- Man durchläuft die Liste von vorne:
    

```java
Node aktuell = head;
while (aktuell != null && !aktuell.data.equals("H")) {
    aktuell = aktuell.next;
}
```

---

## ⚖️ **Vergleich mit Arrays**

|Merkmal|Array|Verkettete Liste|
|---|---|---|
|Größe|fix|dynamisch|
|Einfügen / Löschen|aufwendig (verschieben)|einfach (Zeiger ändern)|
|Zugriff auf i-tes Element|direkt (Index)|langsam (durchlaufen)|
|Speicherverteilung|zusammenhängend|verteilt im Speicher (Heap)|

---

### 📐 **UML-Hinweis**

- Beziehungen wie `1 → *` (ein Element zeigt auf beliebig viele Nachfolger)
    
- `getNext()` / `setNext()` Methoden wichtig fürs Navigieren und Verknüpfen
    

---

### 🧪 **Klausur-Kandidaten**

- **Einfach verkettete Liste zeichnen**
    
- **Einfügen/Löschen in Pseudocode oder Java**
    
- **Zugriffslogik erklären**
    
- **Klassendiagramm mit `Node` und `next`**
    

---

**Next stop:** Kontrollfragen & Lösungen – ich prüfe, ob da wichtige Wiederholungen oder neue Inhalte für die Zusammenfassung drin sind. 🎯📘
Ich hab die **Kontrollfragen** durchgesehen – und sie sind Gold wert! 🔥 Sie bestätigen und vertiefen viele der Inhalte aus den Präsentationen. Hier kommt eine strukturierte Übersicht aller Fragen mit den passenden Antworten als **Wiederholung & Festigung für die Klausur**:

---

## 📌 **Kontrollfragen & Antworten – kompakt zusammengefasst**

---

### 🔷 **`static`**

**1. Auf was kann eine `static` Methode zugreifen?**  
→ Nur auf **`static` Variablen und Methoden**, nicht auf Objektattribute.

**2. Kann eine Instanz-Methode `static` Eigenschaften nutzen?**  
→ Ja, weil `static` Eigenschaften für alle Objekte existieren.

**3. Kann eine Instanz-Methode `static` Methoden nutzen?**  
→ Ja.

**4. Was haben `static` Methoden und `static` Variablen gemeinsam?**  
→ Sie gehören der **Klasse**, nicht dem Objekt.

**5. Wie wird `static` im Klassendiagramm dargestellt?**  
→ Durch **Unterstreichung**.

**6. Warum erkennt man innerhalb der Klasse nicht, ob etwas `static` ist?**  
→ Weil man Methoden auch ohne Klassennamen aufruft – es wirkt gleich.

**7. Wie erkennt man **außerhalb** der Klasse, ob eine Methode `static` ist?**  
→ Man sieht es am **Aufruf mit Klassenname**: `Klasse.methode()` statt `objekt.methode()`.

**8. Was braucht man in `main()`, um eine **nicht-static Methode** zu nutzen?**  
→ Ein Objekt: `MeinTyp ding = new MeinTyp(); ding.methode();`

**9. Wann benutzt man `static`?**  
→ Wenn etwas **für alle Objekte** gilt (z. B. ein Zähler, Hilfsmethoden, Konstanten).

---

### 🔷 **Generics, Collections, Maps**

**10. Warum sind Generics gut?**  
→ Sie sorgen für **Typsicherheit**, vermeiden Casts & Laufzeitfehler.

**11. Wann verwendet man `List`?**  
→ Wenn **Reihenfolge wichtig ist** oder **Duplikate erlaubt** sind.

**12. Wann verwendet man `Set`?**  
→ Wenn **keine Duplikate** erlaubt sein sollen.

**13. Wann verwendet man `Map`?**  
→ Wenn man **Schlüssel-Wert-Paare** speichern will.

**14. Welcher Container für **schnellen Zugriff auf Positionen**?**  
→ `ArrayList`.

**15. Welcher Container für **häufiges Einfügen/Löschen in der Mitte**?**  
→ `LinkedList`.

**16. Welcher Container für **Sortierung + Eindeutigkeit**?**  
→ `TreeSet`.

**17. Welcher Container für **Eindeutigkeit + schnellen Zugriff**?**  
→ `HashSet`.

---

### 🔷 **Interfaces**

**18. Warum gibt es Interfaces?**  
→ Um **Mehrfachvererbung zu simulieren**, Klassen verschiedene Fähigkeiten zu geben.

**19. Wie viele Interfaces kann eine Klasse implementieren?**  
→ **Beliebig viele**.

**20. Von wie vielen Klassen kann eine Klasse erben?**  
→ **Genau einer**.

**21. Wann nimmt man eher eine **abstrakte Klasse** als ein Interface?**  
→ Wenn **gemeinsamer Code oder Attribute** gebraucht werden.

**22. Wann ist ein Interface besser?**  
→ Wenn **nur Verhalten** (Methoden) beschrieben werden sollen.

**23. Wie zeigt man, dass eine Klasse ein Interface verwendet?**  
→ `implements`.

**24. Unterschied Interface vs. Vererbung im UML-Diagramm?**  
→ Interface: **gestrichelter Pfeil mit leerer Spitze**  
→ Vererbung: **durchgezogener Pfeil mit leerer Spitze**

---

Falls du magst, kann ich jetzt noch in die restlichen Dokumente (z. B. Figurenaufgabe mit Factory und Generics) reinschauen und daraus die letzten großen Zusammenfassungen bauen – dort steckt bestimmt die Praxis für den Code-Teil der Klausur drin. Willst du das? 💻📐
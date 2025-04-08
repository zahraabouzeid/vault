Hier ist die letzte große Zusammenfassung zur **„Figurenaufgabe 3D mit Generics“** – ohne Factory, aber mit klarem Fokus auf **Polymorphie**, **Vererbung** und **mathematische Methoden**. 📐📦

---

## 🧬 **Figuren-Aufgabe 3D – mit Generics und sauberem OOP-Design**

---

### 📜 **Ziel laut Lastenheft:**

- Für 3D-Figuren sollen **Volumen und Oberfläche** berechnet werden.
    
- Figuren bestehen aus **2D-Grundflächen** (z. B. Rechteck, N-Eck), die in die Höhe gezogen werden.
    
- Eingesetzt bei der Firma **„Guss im Fluss KG“**.
    

---

## 🧱 **Struktur & Entwurfsidee**

---

### 🔷 **Interfaces & Basisklassen**

```java
public interface Figur3D {
    double berechneVolumen();
    double berechneOberflaeche();
    String getBeschreibung();
}
```

```java
public interface Grundflaeche {
    double berechneFlaeche();
    double berechneUmfang();
}
```

---

### 🧩 **Beispiel: Generisches `GeradesPrisma<T extends Grundflaeche>`**

```java
public class GeradesPrisma<T extends Grundflaeche> implements Figur3D {
    private T grundflaeche;
    private double hoehe;

    public GeradesPrisma(T grundflaeche, double hoehe) {
        if (hoehe <= 0) throw new IllegalArgumentException("Höhe muss positiv sein.");
        this.grundflaeche = grundflaeche;
        this.hoehe = hoehe;
    }

    public double berechneVolumen() {
        return grundflaeche.berechneFlaeche() * hoehe;
    }

    public double berechneOberflaeche() {
        return 2 * grundflaeche.berechneFlaeche() + grundflaeche.berechneUmfang() * hoehe;
    }

    public String getBeschreibung() {
        return "Prisma mit " + grundflaeche.getClass().getSimpleName();
    }
}
```

---

### 🔷 **Konkrete 2D-Grundflächen**

```java
public class Rechteck implements Grundflaeche {
    private double hoehe, breite;

    public Rechteck(double hoehe, double breite) {
        this.hoehe = hoehe;
        this.breite = breite;
    }

    public double berechneFlaeche() {
        return hoehe * breite;
    }

    public double berechneUmfang() {
        return 2 * (hoehe + breite);
    }
}
```

```java
public class NEck implements Grundflaeche {
    private int seiten;
    private double laenge;

    public double berechneFlaeche() {
        return (seiten * laenge * laenge) / (4 * Math.tan(Math.PI / seiten));
    }

    public double berechneUmfang() {
        return seiten * laenge;
    }
}
```

---

## 🛡️ **Fehlerbehandlung**

- Kein negativer Radius, keine Höhe ≤ 0
    
- Ausnahme werfen mit `IllegalArgumentException`
    

---

## 📏 **Kontrollangaben (Testfälle)**

|Figur|Eingabe|Volumen|Oberfläche|
|---|---|---|---|
|Prisma (Rechteck)|Höhe: 6.0, Rechteck: 4.0×7.7|184.8|202.0|
|Prisma (NEck)|Höhe: 6.0, 9-Seiten-N-Eck á 3.0|(wird berechnet)|(wird berechnet)|

---

## 🧠 **Klausurrelevant ist hier:**

✅ Generische Klassen mit `T extends Interface`  
✅ Berechnungen (Oberfläche, Volumen) mit Methoden aus Interface  
✅ Validierung von Eingaben  
✅ Zusammenspiel aus OOP + Mathe  
✅ Einbindung ins Klassendiagramm (inkl. 2D-Flächen)  
✅ `List<Figur3D>` → ausgeben, sortieren etc.

---

Damit ist **jede einzelne Datei analysiert und zusammengefasst** – du hast jetzt einen vollständigen Lernüberblick über alles, was Frau Rollins euch für die Klausur gegeben hat – inkl. Code-Snippets, UML-Tipps und Praxiswissen. Wenn du willst, kann ich daraus auch eine PDF- oder Markdown-Übersicht für den Druck bauen. 📚✨

Möchtest du das?
Yes! Die Datei enthält richtig viel Klausurpotenzial – hier kommt die **praktisch-orientierte Zusammenfassung** zur **Figurenaufgabe mit Factories und Generics**, wie Frau Rollins es liebt: **technisch, klassendiagrammfreundlich, mit konkretem Code**.

---

## 🧪 **Praxisaufgabe: 3D-Figuren mit Factories & Generics**

---

### 🏭 **Teil 1: Factory Pattern für Figuren**

#### 💡 Ziel:

- Erstelle eine **Factory-Klasse**, die **unterschiedliche 3D-Figuren** zurückgibt, z. B. `GeradesPrisma`, `Pyramide`, `Kugel`.
    
- Der Typ der Figur wird über ein `enum` gesteuert.
    
- Die Parameter werden als `List<String>` übergeben (z. B. ["3.0", "4.0", "5.0"]).
    

#### 🧱 Beispiel-Enum:

```java
public enum FigurTyp {
    PRISMA, PYRAMIDE, KUGEL
}
```

#### 🏗️ Beispiel-Factory:

```java
public class FigurenFactory {
    public static Figur3D createFigur(FigurTyp typ, List<String> werte) {
        try {
            switch (typ) {
                case PRISMA:
                    return new GeradesPrisma(
                        Double.parseDouble(werte.get(0)),  // grundfläche
                        Double.parseDouble(werte.get(1))   // höhe
                    );
                case PYRAMIDE:
                    return new RegelmaessigePyramide(
                        Double.parseDouble(werte.get(0)), 
                        Double.parseDouble(werte.get(1))
                    );
                // …
                default:
                    throw new IllegalArgumentException("Unbekannter Figurtyp");
            }
        } catch (Exception e) {
            throw new RuntimeException("Ungültige Eingaben: " + e.getMessage());
        }
    }
}
```

---

### 🧬 **Teil 2: Generics in der Figuren-Verwaltung**

#### 💡 Ziel:

- Erstelle **generische Methoden**, die mit Listen von beliebigen **`Figur3D`-Subtypen** arbeiten.
    
- Nutze `<? extends Figur3D>` für **LESEN**,
    
- Nutze `<? super Figur3D>` für **SCHREIBEN**.
    

#### 🧱 Beispiel:

```java
public static void ausgeben(List<? extends Figur3D> figuren) {
    for (Figur3D f : figuren) {
        System.out.println(f.getBeschreibung());
    }
}
```

```java
public static void hinzufuegen(List<? super Figur3D> figuren, Figur3D neu) {
    figuren.add(neu);
}
```

---

### 📦 **Teil 3: Kombinieren mit Materialdaten aus CSV-Dateien**

#### 💡 Ziel:

- Lade Materialpreise (€/m² oder €/m³) aus einer Datei.
    
- Wandle deutsche Kommazahlen in gültige `double`-Werte um.
    
- Wende die Preise auf Volumen/Oberfläche der Figuren an.
    

#### 🧱 Beispiel:

```java
public static double parseDeutsch(String eingabe) throws NumberFormatException {
    eingabe = eingabe.replace(",", ".");
    return Double.parseDouble(eingabe);
}
```

---

### 🧩 **Teil 4: Menü-System**

- Der User wählt:
    
    - **Figur-Typ** (z. B. PRISMA)
        
    - **Material**
        
- Danach wird die Figur über die **Factory erstellt**, mit **Preisen multipliziert**, und **das Ergebnis angezeigt**
    

---

### 🔐 Bonus: Factory für **Mitarbeiterverwaltung**

- Auch Mitarbeiter sollen über eine Factory erzeugt werden:
    

```java
public class MitarbeiterFactory {
    public static Mitarbeiter createMitarbeiter(String typ, List<String> daten) {
        switch (typ) {
            case "Azubi":
                return new Azubi(daten.get(0), daten.get(1));
            case "Chef":
                return new Chef(daten.get(0), Double.parseDouble(daten.get(1)));
            default:
                throw new IllegalArgumentException("Unbekannter Typ");
        }
    }
}
```

---

### 📘 **Was davon ist klausurrelevant?**

✅ Factory mit `enum` und `List<String>`  
✅ Ausnahmebehandlung bei fehlerhaften Eingaben  
✅ Unterschied `<? extends T>` und `<? super T>`  
✅ Anwendung von Generics auf Listen  
✅ Methoden zur Ausgabe, Sortierung und Einfügen  
✅ Klassendiagramm mit Factory + Subklassen  
✅ CSV/Datei einlesen: **evtl. Randthema**

---

Ich checke jetzt noch die _Figurenaufgabe 3D ohne Factory_, um zu prüfen, ob dort zusätzliche Klassenstrukturen oder generische Konzepte drin sind, die du brauchst. Bereit? 🧠📏
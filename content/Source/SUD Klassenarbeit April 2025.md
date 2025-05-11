![[Attachments/Pasted image 20250504234427.png]]
## Aufgabe 1 Factory-Klasse und Exception-Handling

#### a) 
**Implementieren Sie für Schiffs-Klassenhierarchie eine Factory-Klasse, welche Motorschiffe und Segelschiffe erstellt. Gehen Sie davon aus, dass der Methode, welche die Schiffe erstellen soll, ein Schiffstyp als enum und eine mit den zum Erstellen der Schiffe erforderlichen Argumenten übergeben werden. Um int und double aus der ArrayList<String> zu parsen, setzen Sie `Integer.parseInt()` und `Double.parseDoub1e()` ein.**
**- Falls die Anzahl der mitgelieferten Werte nicht ausreicht, um ein Objekt zu erstellen, soll in jedem Fall eine `NoSuchE1ementException` geworfen werden. Dabei sollen die Exceptions nicht in der Methode selbst abgefangen werden, sondern erst da, wo die Schiffe erstellt werden. Die 'message' sollen, abhängig von der fehlenden Information, wie folgt lauten:**
**- "Damit kann man kein Motorschiff erzeugen. "**
**- "Damit kann man kein Segelschiff erzeugen. "**
**- "Das Schiff gibt es noch nicht. "**

`SchiffTyp.java`
``` java 
public enum SchiffTyp {  
    MOTORSCHIFF, SEGELSCHIFF, UNBEKANNT  
}
```

`SchiffFactory.java`
```java
public class SchiffFactory {  
    public static Schiff createSchiff(SchiffTyp typ, ArrayList<String> args) throws NoSuchElementException {  
        switch (typ) {  
            case MOTORSCHIFF:  
                if (args.size() != 5) {  
                    throw new NoSuchElementException("Damit kann man kein Klassen.Motorschiff erzeugen.");  
                }  
                return new Motorschiff(  
                    args.get(0),  
                    new GPS(Double.parseDouble(args.get(1)), Double.parseDouble(args.get(2))),  
                    Double.parseDouble(args.get(3)),  
                    Integer.parseInt(args.get(4)  
                )  
            );  
  
            case SEGELSCHIFF:  
                if (args.size() != 4) throw new NoSuchElementException("Damit kann man kein Klassen.Segelschiff erzeugen.");  
                return new Segelschiff(  
                    args.get(0),  
                    new GPS(Double.parseDouble(args.get(1)), Double.parseDouble(args.get(2))),  
                    Integer.parseInt(args.get(3)  
                )  
            );  
  
            default:  
                throw new NoSuchElementException("Das Schiff gibt es noch nicht.");  
        }  
    }  
}
```
#### b)
**Erstellen Sie auszugsweise eine main-Methode, die auch in einer anderen Klasse und einem anderen package stehen kann (Klassenstruktur nicht erforderlich), welche vier Objekte mit Hilfe der Factory-Klasse erstellt. Es sollen dabei ein gültiges Objekt und drei unzulässige Objekte (je eins pro Fehlermeldung) versucht werden zu erzeugen. Die "message' der Exceptions sollen im Fehlerfall ausgegeben werden.**

`Main.java`
```java
public class Main {  
    public static void main(String[] args) {  
        String schiffName = "";  
  
        try {  
            // Gültiges Motorschiff  
            schiffName = "Sayler";  
            ArrayList<String> args1 = new ArrayList<>();  
            args1.add(schiffName);  
            args1.add("50.45");  
            args1.add("10.30");  
            args1.add("5000.0");  
            args1.add("2000");  
            Schiff schiff1 = SchiffFactory.createSchiff(SchiffTyp.MOTORSCHIFF, args1);  
  
            // Ungültiges Motorschiff (PS fehlt)  
            schiffName = "Shipknot";  
            ArrayList<String> args2 = new ArrayList<>();  
            args2.add(schiffName);  
            args2.add("50.0");  
            args2.add("10.0");  
            args2.add("8000.0");  
            SchiffFactory.createSchiff(SchiffTyp.MOTORSCHIFF, args2);  
  
            // Ungültiges Segelschiff (Segelanzahl fehlt)  
            schiffName = "Seapultura";  
            ArrayList<String> args3 = new ArrayList<>();  
            args3.add(schiffName);  
            args3.add("60.0");  
            args3.add("30.0");  
            SchiffFactory.createSchiff(SchiffTyp.SEGELSCHIFF, args3);  
  
            // Ungültiger Schiffstyp (null Schiffstyp)  
            schiffName = "Parkwave Dive";  
            ArrayList<String> args4 = new ArrayList<>();  
            args4.add(schiffName);  
            SchiffFactory.createSchiff(SchiffTyp.UNBEKANNT, args4);  
  
        } catch (NoSuchElementException e) {  
            System.out.println("Fehler bei Schiff \"" + schiffName + "\": " + e.getMessage());  
        }  
    }  
}
```
## Aufgabe 2 Generische Datenstrukturen verwenden
#### a)
**Implementieren Sie eine Klasse Hafen mit folgenden Containern (Datenstrukturen):**
**- Die Klasse soll einen geeigneten Container schiffelmHafen für alle Schiffe, die sich aktuell im Hafen befinden, enthalten. Der Container soll schnell im Einfügen und Löschen an jeder Position sein und sortiert werden können.**
**- Die Klasse soll zudem einen Container bekannteSchiffe für Schiffe enthalten. Dabei sollen keine Schiffe doppelt eingefügt werden können. Die Reihenfolge ist dabei unerheblich, aber Schiffe, die gesucht werden, sollen schnell gefunden werden können.**
**- Ein weiterer Container ankerP1aetze hat die Aufgabe mit Angabe des Ankerplatzes das dort liegende Schiff zu ermitteln. Der Ankerplatz ist eine einfache Ganzzahl und eindeutig. Der Container soll beim Hinzufügen eines Schiffs gemäß der Ankerposition sortieren.**

`Hafen.java`
```java
public class Hafen <T extends Schiff> {  
    private LinkedList<T> schiffeImHafen;  
    private HashSet<T> bekannteSchiffe;  
    private TreeMap<Integer, T> ankerPlaetze;  
} 
```
#### b)
**Fügen Sie der Klasse Hafen eine stallg Methode hinzu, welche einer beliebigen Collection ein beliebiges Schiff hinzufügt.**

```java
public static void addSchiff(Collection<? super Schiff> collection, Schiff schiff) {  
    collection.add(schiff);  
}  
```

#### c)
**Fügen Sie der Klasse Hafen eine weitere Static Methode hinzu, welche ein Schiff aus einer beliebigen Collection entfernt.**
```java
public static void removeSchiff(Collection<? super Schiff> collection, Schiff schiff) {  
    collection.remove(schiff);  
}  
```

## Aufgabe 3 Objekte sortierbar machen

#### a)
**Implementieren Sie die Möglichkeit, dass Schiffe nach Namen sortiert werden können.**
`Schiff.java`
```java
public abstract class Schiff implements Comparable<Schiff> {  
    ...
    @Override  
    public int compareTo(Schiff other) {  
        return this.name.compareTo(other.name);  
    }  
    ...
}
```
#### b)
**Implementieren Sie zusätzlich die Möglichkeit, Schiffe nach Geschwindigkeit (speed) zu sortieren.**
`SchiffSpeedComparator.java`
```java
public class SchiffSpeedComparator implements Comparator<Schiff> {  
    @Override  
    public int compare(Schiff s1, Schiff s2) {  
        return Integer.compare(s1.getSpeed(), s2.getSpeed());  
    }  
}
```
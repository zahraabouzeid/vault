Design Patterns (Entwurfsmuster) sind wiederkehrende, bewährte Lösungsansätze für typische Architektur und Konstruktionsprobleme in der Softwareentwicklung. Sie beschreiben auf einer abstrakten Ebene, wie Klassen und Objekte zusammenwirken sollten, bieten aber keinen fertigen Code. Der Vorteil ist, dass man erprobte Strukturen nutzt, um den Code wartbar, flexibel und erweiterbar zu gestalten.

## Kompositum-Muster  
Das Kompositum-Muster ist ein ==**Strukturmuster**==, mit dem man Baumstrukturen von Objekten so modelliert, dass einzelne Objekte (Blätter) und Gruppen von Objekten (Komposita) über dasselbe Interface angesprochen werden können.

## 1. Interface 
Ein Interface in Java legt fest, welche Methoden eine Klasse bereitstellen muss, ohne die konkrete Implementierung vorzugeben. Es ist sozusagen ein Vertrag oder eine Schablone, die bestimmt, wie verschiedene Klassen angesprochen werden können. 

**Beispiel:**
```java
public interface LegoBauteil {
    double getPreis();
}
```

Jedes Bauteil ob einfacher Stein oder komplexes Gebilde implementiert `getPreis()`

## 2. Leafklasse
Eine Leaf-Klasse ist eine konkrete Implementierung des Interfaces, die keine weiteren Unterobjekte enthält. Sie steht für ein einzelnes, nicht weiter unterteilbares Element im Kompositum-Baum.

**Beispiel:**
```java
public class Legostein implements LegoBauteil {
    private final double preis;
    public Legostein(double preis) { this.preis = preis; }
    @Override
    public double getPreis() { return preis; }
}
```
Ein `Legostein` hält nur seinen eigenen Preis und gibt ihn zurück.
## 3. Komposita
Eine Komposita ist ebenfalls eine Implementierung des Interfaces, kann aber beliebig viele andere Objekte aufnehmen sowohl Leafs als auch weitere Kompositas. Sie bündelt also mehrere Bauteile zu einer größeren Einheit und leitet Operationen (wie `getPreis()`) an ihre enthaltenen Kinder weiter. 

**Beispiel:**

```java
import java.util.ArrayList;
import java.util.List;

public class FertigBauteil implements LegoBauteil {
    private final List<LegoBauteil> teile = new ArrayList<>();

    public void add(LegoBauteil teil) { teile.add(teil); }
    public void remove(LegoBauteil teil) { teile.remove(teil); }

    @Override
    public double getPreis() {
        double summe = 0;
        for (LegoBauteil teil : teile)
            summe += teil.getPreis();
        return summe;
    }
}
```
`FertigBauteil` die Komposita und kann sowohl einzelne Steine als auch ganze Baugruppen enthalten. Ein `FertigBauteil` enthält beliebig viele `LegoBauteil` Instanzen und summiert deren Preise rekursiv
## Anwendung
Um den Gesamtpreis einer Lego-Stadt zu berechnen, sammelt man alle `LegoBauteil` (Legosteine und Fertigbauteile) in einer Liste und ruft `getPreis()` auf jedem Element auf. Dank des Kompositum-Musters summiert die Stadt ihre Kosten automatisch, egal wie tief die Verschachtelung ist.
```java
public class LegoStadtDemo {
    public static void main(String[] args) {
        // Einzelne Steine
        Legostein stein1 = new Legostein(1.50);
        Legostein stein2 = new Legostein(2.00);

        // Fertigbauteil (z. B. ein Haus aus mehreren Steinen)
        FertigBauteil haus = new FertigBauteil();
        haus.add(stein1);
        haus.add(stein2);

        // Noch ein Fertigbauteil (z. B. eine Brücke)
        FertigBauteil bruecke = new FertigBauteil();
        bruecke.add(new Legostein(3.00));
        bruecke.add(new Legostein(2.50));

        // Die ganze Stadt besteht aus Häusern, Brücken und ggf. Einzelsteinen
        FertigBauteil stadt = new FertigBauteil();
        stadt.add(haus);
        stadt.add(bruecke);
        stadt.add(new Legostein(0.75)); // z. B. ein einzelner Stein als Deko

        // Berechnung Gesamtpreis der Stadt:
        double gesamtpreis = stadt.getPreis();
        System.out.printf("Der Gesamtpreis der Lego-Stadt beträgt: %.2f Euro%n", gesamtpreis);
    }
}
```
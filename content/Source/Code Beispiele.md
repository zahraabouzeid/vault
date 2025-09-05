## 1. Kompositum-Muster 

### LegoBauteil.java
```java
public interface LegoBauteil {
    double getPreis();
    void setPreis(double preis);
    String getName();
    void setName(String name);
    void anzeigen(String einrueckung);
}
```

### Legostein.java
```java
public class Legostein implements LegoBauteil {
    private String name;
    private double preis;

    public Legostein(String name, double preis) {
        this.name = name;
        this.preis = preis;
    }

    @Override
    public double getPreis() {
        return preis;
    }

    @Override
    public void setPreis(double preis) {
        this.preis = preis;
    }

    @Override
    public String getName() {
        return name;
    }

    @Override
    public void setName(String name) {
        this.name = name;
    }

    @Override
    public void anzeigen(String einrueckung) {
        System.out.println(einrueckung + getName() + ": " + getPreis() + "€");
    }
}
```

### FertigBauteil.java
```java
import java.util.ArrayList;
import java.util.List;

public class FertigBauteil implements LegoBauteil {
    private String name;
    private final List<LegoBauteil> teile = new ArrayList<>();

    public FertigBauteil(String name) {
        this.name = name;
    }

    @Override
    public double getPreis() {
        return teile.stream().mapToDouble(LegoBauteil::getPreis).sum();
    }

    @Override
    public void setPreis(double preis) {
        throw new UnsupportedOperationException("Preis wird aus Teilen berechnet");
    }

    @Override
    public String getName() {
        return name;
    }

    @Override
    public void setName(String name) {
        this.name = name;
    }

    public List<LegoBauteil> getTeile() {
        return new ArrayList<>(teile);
    }

    public void add(LegoBauteil teil) {
        teile.add(teil);
    }

    public void remove(LegoBauteil teil) {
        teile.remove(teil);
    }

    @Override
    public void anzeigen(String einrueckung) {
        System.out.println(einrueckung + getName() + " (Gesamt: " + getPreis() + "€)");
        teile.forEach(teil -> teil.anzeigen(einrueckung + "  "));
    }
}
```

### LegoStadt.java
```java
public class LegoStadt {
    public static void main(String[] args) {
        Legostein stein1 = new Legostein("Grundstein", 1.50);
        Legostein stein2 = new Legostein("Fenster", 2.00);
        Legostein stein3 = new Legostein("Tür", 3.00);
        
        FertigBauteil haus = new FertigBauteil("Haus");
        haus.add(stein1);
        haus.add(stein2);
        haus.add(stein3);
        
        FertigBauteil bruecke = new FertigBauteil("Brücke");
        bruecke.add(new Legostein("Pfeiler", 4.00));
        bruecke.add(new Legostein("Platte", 3.50));
        
        FertigBauteil stadt = new FertigBauteil("Lego-Stadt");
        stadt.add(haus);
        stadt.add(bruecke);
        stadt.add(new Legostein("Laterne", 0.75));
        
        stadt.anzeigen("");
        System.out.printf("Gesamtpreis: %.2f€\n", stadt.getPreis());
        
        // Änderung mit Setter
        stein1.setPreis(2.00);
        System.out.println("\nNach Preisanpassung:");
        stadt.anzeigen("");
    }
}
```

## 2. Observer Pattern (Pull Modell)

### Observer.java (Interface)
```java
public interface Observer {  
    void aktualisieren();  
}
```
- **Zweck**: Definiert die Schnittstelle für alle Beobachter
- **Methode**: `aktualisieren()` wird aufgerufen wenn sich Daten ändern
### Subject.java (Interface)
```java
public interface Subject {  
    void registriereBeobachter(Observer o);  
    void entferneBeobachter(Observer o);  
    void benachrichtigeBeobachter();  
}
```
**Verwaltet** Observer (hinzufügen/entfernen/benachrichtigen)
### WetterDaten.java (Concrete Subject)
```java
import java.util.ArrayList;  
import java.util.List;  
  
public class WetterDaten implements Subject {  
  
    private double temperatur;  
    private double feuchtigkeit;  
    private double luftdruck;  
    private List<Observer> beobachter;  
  
    public WetterDaten(double t, double f, double l) {  
        this.beobachter = new ArrayList<>();  
        this.setTemperatur(t);  
        this.setFeuchtigkeit(f);  
        this.setLuftdruck(l);  
    }  
  
    public void setTemperatur(double temperatur) {  
        if (temperatur >= -90 && temperatur <= 60) {  
            this.temperatur = temperatur;  
            benachrichtigeBeobachter();  
        }  
    }  
  
    public void setFeuchtigkeit(double feuchtigkeit) {  
        if (feuchtigkeit >= 0 && feuchtigkeit <= 100) {  
            this.feuchtigkeit = feuchtigkeit;  
            benachrichtigeBeobachter();  
        }  
    }  
  
    public void setLuftdruck(double luftdruck) {  
        if (luftdruck >= 100 && luftdruck <= 1050) {  
            this.luftdruck = luftdruck;  
            benachrichtigeBeobachter();  
        }  
    }  
  
    public double getFeuchtigkeit() {  
        return feuchtigkeit;  
    }  
  
    public double getTemperatur() {  
        return temperatur;  
    }  
  
    public double getLuftdruck() {  
        return luftdruck;  
    }  
  
    @Override  
    public void registriereBeobachter(Observer o) {  
        beobachter.add(o);  
    }  
  
    @Override  
    public void entferneBeobachter(Observer o) {  
        beobachter.remove(o);  
    }  
  
    @Override  
    public void benachrichtigeBeobachter() {  
        WetterInfo info = new WetterInfo(temperatur, feuchtigkeit, luftdruck);  
        beobachter.forEach(o -> o.aktualisieren(info));  
    }  
}
```

- **Hält** die Wetterdaten (Temperatur, Feuchtigkeit, Luftdruck)
- **Implementiert** Subject-Interface
- **Benachrichtigt** Observer bei Änderungen (via `messwerteGeaendert()`)
### AktuelleBedingungen.java (Concrete Observer)
```java
class AktuelleBedingungen implements Observer {
    private final WetterDaten wetterDaten;

    public AktuelleBedingungen(WetterDaten wetterDaten) {
        this.wetterDaten = wetterDaten;
    }

    @Override
    public void aktualisieren() {
            wetterDaten.getTemperatur(), 
            wetterDaten.getFeuchtigkeit());
    }
}
```
- **Zeigt** aktuelle Messwerte an
- **Pull-Modell**: Holt sich Daten bei update()
### WetterVorhersage.java
```java
public class WetterVorhersage implements Observer {

    private double letzterLuftdruck = 1013;
    private double aktuellerLuftdruck;
    private final WetterDaten wetterDaten;

    // Konstruktor mit Übergabe des Subjects
    public WetterVorhersage(WetterDaten wetterDaten) {
        this.wetterDaten = wetterDaten;
    }

    @Override
    public void aktualisieren() {
        this.letzterLuftdruck = this.aktuellerLuftdruck;
        this.aktuellerLuftdruck = subject.getLuftdruck();
        // Hier kannst du weitere Logik einbauen (Anzeige, Vorhersage usw.)
    }
}
```
- **Berechnet** Vorhersage basierend auf Luftdruck
- **Pull-Modell**: Holt sich Daten bei update()
## 3. Observer Pattern (Push Modell)
### Observer.java (Push-Variante)
```java
public interface Observer {  
    void aktualisieren(WetterInfo info);  
}
```

### Subject.java (unverändert)
```java
public interface Subject {  
    void registriereBeobachter(Observer o);  
    void entferneBeobachter(Observer o);  
    void benachrichtigeBeobachter();  
}
```

### WetterInfo.java (Daten-Transfer-Objekt)
```java
public class WetterInfo {  
    private final double temperatur;  
    private final double feuchtigkeit;  
    private final double luftdruck;  
  
    public WetterInfo(double temp, double feucht, double druck) {  
        this.temperatur = temp;  
        this.feuchtigkeit = feucht;  
        this.luftdruck = druck;  
    }  
  
    // Getter  
    public double getTemperatur() { return temperatur; }  
    public double getFeuchtigkeit() { return feuchtigkeit; }  
    public double getLuftdruck() { return luftdruck; }  
}
```
### WetterDaten.java (Push-Implementierung)
```java
import java.util.ArrayList;  
import java.util.List;  
  
public class WetterDaten implements Subject {  
  
    private double temperatur;  
    private double feuchtigkeit;  
    private double luftdruck;  
    private List<Observer> beobachter;  
  
    public WetterDaten(double t, double f, double l) {  
        this.beobachter = new ArrayList<>();  
        this.setTemperatur(t);  
        this.setFeuchtigkeit(f);  
        this.setLuftdruck(l);  
    }  
  
    public void setTemperatur(double temperatur) {  
        if (temperatur >= -90 && temperatur <= 60) {  
            this.temperatur = temperatur;  
            benachrichtigeBeobachter();  
        }  
    }  
  
    public void setFeuchtigkeit(double feuchtigkeit) {  
        if (feuchtigkeit >= 0 && feuchtigkeit <= 100) {  
            this.feuchtigkeit = feuchtigkeit;  
            benachrichtigeBeobachter();  
        }  
    }  
  
    public void setLuftdruck(double luftdruck) {  
        if (luftdruck >= 100 && luftdruck <= 1050) {  
            this.luftdruck = luftdruck;  
            benachrichtigeBeobachter();  
        }  
    }  
  
    public double getFeuchtigkeit() {  
        return feuchtigkeit;  
    }  
  
    public double getTemperatur() {  
        return temperatur;  
    }  
  
    public double getLuftdruck() {  
        return luftdruck;  
    }  
  
    @Override  
    public void registriereBeobachter(Observer o) {  
        beobachter.add(o);  
    }  
  
    @Override  
    public void entferneBeobachter(Observer o) {  
        beobachter.remove(o);  
    }  
  
    @Override  
    public void benachrichtigeBeobachter() {  
        WetterInfo info = new WetterInfo(temperatur, feuchtigkeit, luftdruck);  
        beobachter.forEach(o -> o.aktualisieren(info));  
    }  
}
```

### AktuelleBedingungen.java
```java
public class AktuelleBedingungen implements Observer {  
    private double temperatur;  
    private double feuchtigkeit;  
  
    @Override  
    public void aktualisieren(WetterInfo info) {  
        this.temperatur = info.getTemperatur();  
        this.feuchtigkeit = info.getFeuchtigkeit();  
    }  
}
```

### WetterVorhersage.java
```java
public class WetterVorhersage implements Observer {  
    private double letzterLuftdruck = 1013;  
    private double aktuellerLuftdruck;  
  
    @Override  
    public void aktualisieren(WetterInfo info) {  
        this.letzterLuftdruck = info.getLuftdruck();  
        this.aktuellerLuftdruck = info.getLuftdruck();  
    }  
}
```
## 4. GUI mit Swing 

```java
import javax.swing.*;  
import java.awt.*;  
import java.awt.event.*;  
  
public class WetterStationGUI extends JFrame implements Observer {  
  
    private JLabel tempLabel;  
    private JLabel feuchtLabel;  
    private JLabel druckLabel;  
    private JLabel vorhersageLabel;  
    private boolean fahrenheit = false;  
    private boolean darkMode = false;  
  
    private double temperatur;  
    private double feuchtigkeit;  
    private double luftdruck;  
    private double letzterLuftdruck = 1013;  
  
    public WetterStationGUI(WetterDaten daten) {  
        super("Wetterstation Aachen");  
        daten.registriereBeobachter(this);  
  
        setSize(400, 300);  
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);  
        setLayout(new GridLayout(5, 1));  
  
        tempLabel = new JLabel();  
        feuchtLabel = new JLabel();  
        druckLabel = new JLabel();  
        vorhersageLabel = new JLabel();  
  
        JButton toggleEinheit = new JButton("Wechsle °C / °F");  
        JButton toggleDarkMode = new JButton("Dark Mode");  
  
        toggleEinheit.addActionListener(e -> {  
            fahrenheit = !fahrenheit;  
            updateAnzeige();  
        });  
          
        toggleDarkMode.addActionListener(new ActionListener() {  
            @Override  
            public void actionPerformed(ActionEvent e) {  
                darkMode = !darkMode;  
                updateStyle();  
            }  
        });  
  
        add(tempLabel);  
        add(feuchtLabel);  
        add(druckLabel);  
        add(vorhersageLabel);  
        add(toggleEinheit);  
        add(toggleDarkMode);  
  
        updateAnzeige();  
        setVisible(true);  
    }  
  
    private void updateAnzeige() {  
        double temp = fahrenheit ? temperatur * 9 / 5 + 32 : temperatur;  
        String einheit = fahrenheit ? "°F" : "°C";  
  
        tempLabel.setText("Temperatur: " + String.format("%.1f", temp) + einheit);  
        feuchtLabel.setText("Feuchtigkeit: " + String.format("%.1f", feuchtigkeit) + "%");  
        druckLabel.setText("Luftdruck: " + String.format("%.1f", luftdruck) + " hPa");  
  
        if (luftdruck > letzterLuftdruck) {  
            vorhersageLabel.setText("Vorhersage: Verbesserung");  
        } else if (luftdruck < letzterLuftdruck) {  
            vorhersageLabel.setText("Vorhersage: Verschlechterung");  
        } else {  
            vorhersageLabel.setText("Vorhersage: Gleichbleibend");  
        }  
    }  
  
    private void updateStyle() {  
        Color bg = darkMode ? Color.DARK_GRAY : Color.WHITE;  
        Color fg = darkMode ? Color.WHITE : Color.BLACK;  
  
        getContentPane().setBackground(bg);  
        Component[] comps = getContentPane().getComponents();  
        for (Component c : comps) {  
            c.setBackground(bg);  
            c.setForeground(fg);  
        }  
    }  
  
    @Override  
    public void aktualisieren(WetterInfo info) {  
        letzterLuftdruck = this.luftdruck;  
        this.temperatur = info.getTemperatur();  
        this.feuchtigkeit = info.getFeuchtigkeit();  
        this.luftdruck = info.getLuftdruck();  
        updateAnzeige();  
    }  
  
    public static void main(String[] args) {  
        WetterDaten daten = new WetterDaten(20, 65, 1013);  
        new WetterStationGUI(daten);  
  
        new Thread(() -> {  
            try {  
                while (true) {  
                    Thread.sleep(2000);  
                    daten.setTemperatur(10 + Math.random() * 15);  
                    daten.setFeuchtigkeit(40 + Math.random() * 30);  
                    daten.setLuftdruck(990 + Math.random() * 40);  
                }  
            } catch (InterruptedException e) {  
                e.printStackTrace();  
            }  
        }).start();  
    }  
}
```
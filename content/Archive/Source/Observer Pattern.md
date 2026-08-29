## 1. Definition
Das Observer Pattern ist ein ==**Verhaltensmuster**==, das eine **einseitige Abhängigkeit** zwischen Objekten herstellt:  
- Ein **Subject** (Observable) verwaltet Zustandsänderungen.  
- **Observer** werden automatisch benachrichtigt, sobald sich der Zustand des Subjects ändert.  

**Zweck**: Lose Kopplung, dynamische Kommunikation zwischen Objekten ohne direkte Abhängigkeiten.  

## 2. Komponenten

| **Rolle**    | **Beschreibung**                                                | **Beispiel (Wetterstation)**                |
| ------------ | --------------------------------------------------------------- | ------------------------------------------- |
| **Subject**  | Kernobjekt, das Zustände verwaltet und Observer benachrichtigt. | `WetterDaten` (misst Temperatur/Luftdruck). |
| **Observer** | Empfängt Updates vom Subject (via Interface).                   | `AktuelleBedingungen`, `StatistikAnzeige`.  |

## 3. Kommunikationsmethoden
**a) Pull-Modell**  
- Observer **holen** sich Daten aktiv vom Subject (z. B. via Getter).  
- **Nachteil**: Subject wird durch häufige Abfragen belastet.  

**Beispiel**:  
```java  
public void update() {  
    System.out.println("Temperatur: " + wetterDaten.getTemperatur());  
}  
```  

**b) Push-Modell**  
- Subject **sendet** Daten direkt mit (z. B. als `InfoObjekt`).  
- **Vorteil**: Effizienter, da kein Typecasting nötig (mit Generics).  

**Beispiel**:  
```java  
public void update(WetterInfo info) {  
    System.out.println("Temperatur: " + info.getTemperatur());  
}  
```  

## 4. Entwurfsprinzipien
- **Lose Kopplung**: Subject kennt Observer nur über Interface.  
- **Hollywood-Prinzip**: *"Don’t call us, we’ll call you!"* Observer registrieren sich und warten auf Updates.  
- **Inversion of Control**: Subject steuert die Benachrichtigungen.  

## 5. Vor- und Nachteile

| **Vorteile**                                | **Nachteile**                                                     |
| ------------------------------------------- | ----------------------------------------------------------------- |
| Flexibel (Observer hinzufügen/entfernen).   | **Aktualisierungskaskaden**: Unnötige Updates.                    |
| Wiederverwendbar (für Events).              | **Thread-Sicherheit**: `ConcurrentModificationException` möglich. |
| Entkoppelt (keine direkten Abhängigkeiten). | **Fehleranfällig**: Lange `update()` Methoden blockieren.         |

**Lösung für Threads**:  
```java  
private Set<Observer> observers = new ConcurrentSkipListSet<>();  
```  

## Beispiel-Code (Push-Modell mit Generics)
**Subject**:  
```java  
public class WetterDaten extends Subject<WetterInfo> {  
    private float temperatur;  
    public void setTemperatur(float temp) {  
        this.temperatur = temp;  
        notifyObservers(new WetterInfo(temp));  
    }  
}  
```  

**Observer**:  
```java  
public class AktuelleBedingungen implements Observer<WetterInfo> {  
    @Override  
    public void update(WetterInfo info) {  
        System.out.println("Neue Temperatur: " + info.getTemperatur());  
    }  
}  
```

| Aspekt                 | Push-Modell                           | Pull-Modell (deine Originalversion) |
| ---------------------- | ------------------------------------- | ----------------------------------- |
| **update() Parameter** | Empfängt alle relevanten Daten        | Keine Parameter, muss Daten holen   |
| **Datenzugriff**       | Direkt via Parameter                  | Muss Getter des Subjects aufrufen   |
| **Flexibilität**       | Subject entscheidet was gesendet wird | Observer entscheidet was er braucht |
| **Code in Observer**   | Einfacher, direkter Zugriff           | Mehr Kontrolle über Datenabfrage    |
## 7. Anwendungsfälle  
- **GUI-Komponenten**: Buttons Event-Handler.  
- **Echtzeit-Systeme**: Börsenticker → Aktualisierungen.  
- **Spiele**: Minecraft-Chat, Achievements.  
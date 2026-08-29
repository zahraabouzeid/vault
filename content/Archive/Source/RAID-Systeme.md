## RAID (Redundant Array of Independent Discs)
- Schnellerer Datenzugriff
- Größere Speicherkapazität
- Erhöhung der Ausfallsicherheit

**JBOD (Just a Bunch Of Disks)**
- Verbund von Festplatten
- Daten werden nacheinander auf die Festplatten geschrieben
## RAID 0 (Striping)
## RAID 0 (Striping) 
### Vorteile 
- Kapazitätsvergrößerung: Mehrere physikalische Festplatten erscheinen als eine logische Festplatte. 
- Schnellerer Datenzugriff. 
### Nachteile 
- Keine Redundanz. 
### Bei 2 Festplatten 
![RAID 0 mit 2 Festplatten|200](Archive/Attachments/Pasted%20image%2020241201191343.png) 
### Bei mehr als 2 Festplatten 
![RAID 0 mit mehr als 2 Festplatten|300](Archive/Attachments/Pasted%20image%2020241201192100.png) 
### Verfügbarkeit 
Bei 3 Festplatten, bei denen die Wahrscheinlichkeit, dass eine Platte nicht ausfällt, 99% beträgt: 
- Wahrscheinlichkeit, dass keine davon ausfällt: 0.99 x 0.99 x 0.99 = 97.0299%. 
- Ausfallwahrscheinlichkeit:  2.9701%. 
- Der Ausfall ist um den Faktor 3 größer geworden.
## RAID 1 (Mirroring)
### Vorteile
- Redundanz 
### Nachteile
- Nettodatenkapazität verkleinert sich auf 50% 
- i.d.R. langsamer als RAID 0

![200](Archive/Attachments/Pasted%20image%2020241201192932.png)
### Verfügbarkeit
Bei 2 Festplatten, bei denen die Wahrscheinlichkeit, dass eine Platte nicht ausfällt, 99% beträgt: 
- wenn beide Platten ausfallen ist der GAU erreicht.
- Wahrscheinlichkeit, dass beide Festplatten ausfallen: 0,01 x 0,01 = 0.0001%
- Ausfallwahrscheinlichkeit ist um Faktor 100 kleiner geworden

## Parität
### Ungerade Parität:  
Anzahl der 1-en inkl. Paritätsbit ist eine ungerade Anzahl.  
#### Beispiel:
Daten: 
`0 1 1 0 1`   
`1 0 1 1 0`
`0 0 0 0 1`
   
Übertragung:  
`0 1 1 0 1` → **Kein Fehler** (Anzahl der 1-en ist ungerade).  
`1 1 1 1 1` → **Kein Fehler** (Anzahl der 1-en ist ungerade).  
`0 0 0 0 0` → **Fehler** (Anzahl der 1-en ist gerade).  

### Gerade Parität:  
Anzahl der 1-en inkl. Paritätsbit ist eine gerade Anzahl.
#### Beispiel:
Daten:
`0 1 1 0 0`
`1 0 1 1 1`
`0 0 0 0 0`

Übertragung:  
`0 1 1 0 0` → **Kein Fehler** (Anzahl der 1-en ist gerade).  
`1 0 1 1 1` → **Kein Fehler** (Anzahl der 1-en ist gerade).  
`0 0 0 0 1` → **Fehler** (Anzahl der 1-en ist ungerade).  
## RAID 5 (Parität)
Nur eine Festplatte darf ausfallen.
### Bei drei Festplatten
![400](Archive/Attachments/Pasted%20image%2020241201194858.png)
### Bei mehr als 3 Festplatten
![400](Archive/Attachments/Pasted%20image%2020241201195330.png)
## RAID 6
![400](Archive/Attachments/RAID%206.png)
- ähnlich wie bei Raid 5 werden Paritätsinformationen erzeugt und auf die Festplatten des Raid verteilt 
- Es werden 2 Paritätsblöcke (Redundanz) erstellt und jeweils auf 2 Festplatten verteilt
- \>= 4 Festplatten nötig
## RAID 10
![400](Archive/Attachments/RAID%2010.png)

## RAID 50
![400](Archive/Attachments/RAID%2050.png)

## RAID 60
![400](Archive/Attachments/RAID%2060.png)

## Spare (Hot) Festplatte
- ein unbenutztes Reservelaufwerk.
- fällt ein Laufwerk innerhalb des RAID-Verbundes aus, wird es durch das Reservelaufwerk ersetzt, und die Redundanz wird schnellstmöglich wiederhergestellt.
- während der Rebuild-Phase hat man allerdings keine Redundanz. 
- zur Vermeidung dieses Problems kann ein RAID 6 statt RAID 5 verwendet werden, da hier zwei Paritätsplatten vorhanden sind.
## Hardware RAID
- das Zusammenwirken der Speichermedien wird von dem RAID-Controller organisiert.
- der Hardware-RAID-Controller befindet sich in physischer Nähe der Speichermedien.
- er kann im Gehäuse des Computers enthalten sein oder in einem eigenen Gehäuse (Disk-Array), in dem auch die Festplatten untergebracht sind.
- RAID-Controller-Karte wird in das Motherboard oder den PCIe-Steckplatz des Computers eingesteckt.
- RAID wird bei externen Systeme wie DAS, SAN oder auch NAS implementiert.
- Hardware RAID Implementierungen verfügen über eigene eingebettete CPUs, sie nutzen große, zusätzliche Cache-Speicher und bieten somit höchsten Datendurchsatz und entlasten dabei gleichzeitig den Hauptprozessor.
- diese Art von RAID ist in der Regel teurer als Software-RAID, da zusätzliche Hardwarekomponenten benötigt werden.
## Software RAID
- das Zusammenwirken der Festplatten wird komplett softwareseitig organisiert.
- die meisten modernen Betriebssysteme sind dazu in der Lage.
- die einzelnen Festplatten sind in diesem Fall entweder über einfache Festplattencontroller am Computer angeschlossen oder es werden externe Storage-Geräte wie Disk-Arrays an den Computer angeschlossen.
- die Festplatten werden ohne RAID-Controller als sogenannte JBODs in das System integriert, dann wird per Software-RAID.
- Software-RAID kann kostengünstiger sein, da keine spezielle Hardware erforderlich ist. Es kann auch auf Standard-Hardware laufen.
- Die Leistung von Software-RAID kann von der CPU-Auslastung des Systems beeinflusst werden, insbesondere bei intensiven RAID-Operationen.
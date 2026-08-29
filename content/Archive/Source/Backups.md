- Backups schützen von Datenverlust. 
- **Datensicherung** ist der Schutz der Daten durch Backups.
- **Datensicherheit** ist der Schutz der Daten vor unbefugtem Zugriff und anderen Bedrohungen.
## Ursachen für Datenverluste
- Hardware Problem
- Menschl. Fehler
- Computer Virus
- Software Problem
- Naturkatastrophen

## Sicherungsverfahren 

### Backup
Sicherung von Daten durch Kopieren auf ein alternatives Medium, um sie im Falle von Verlust oder Beschädigung wiederherstellen zu können.

### Spiegelung
Echtzeit-Duplizierung von Daten, um Redundanz zu schaffen und Ausfallsicherheit zu gewährleisten.

### Image
Erstellung eines exakten Abbildes eines Datenträgers oder einer Partition, das sämtliche Daten und Strukturen in einer Datei speichert.

### Archivierung
Langfristige Aufbewahrung von Daten auf stabilen, kostengünstigen Medien, meist für historische oder rechtliche Zwecke, um sie bei Bedarf wieder zugänglich zu machen.

## Backup-Konzepte
### Vollständiges Backup / Vollsicherung
![400](Archive/Attachments/Pasted%20image%2020241201214452.png)
#### Vorteile
Alle Dateien liegen komplett vor und können leicht wieder gefunden werden.
#### Nachteile
Bei häufiger Sicherung ist Ihr Speicherbedarf enorm.
### Differenzielle Backups
![400](Archive/Attachments/Pasted%20image%2020241201215738.png)
#### Vorteile
Für die Wiederherstellung eines Standes benötigen Sie (nur) das eine differentielle Backup von dem betreffenden Datum und das letzte davor liegende Vollbackup.
#### Nachteile
Eine geänderte Datei wird bis zum nächsten Vollbackup in jedem diff. Backup erneut gesichert, auch wenn sie nicht weiter bearbeitet wurde. → unnötig belegter Speicherplatz.
### Inkrementelle Backups
![400](Archive/Attachments/Pasted%20image%2020241201220249.png)
### Vorteile
Da jeder Dateistand nur einmal gesichert wird, ist der Speicherbedarf optimal niedrig.
### Nachteile
Für einen kompletten Datenbestand ist das letzte Vollbackup & alle seither erzeugten inkrementellen Backups erforderlich.
### Das Generationenprinzip
![400](Archive/Attachments/Pasted%20image%2020241201220404.png)
## Backup Medien
- Magnetbänder 
- Optische Medien 
- Festplatten
### Backup Systeme
- Bandlaufwerk 
- Jukebox 
- Festplatten Storages
# Nebenläufigkeit
## Definition
- Nebenläufigkeit trennt „Was“ von „Wann“ und verbessert Durchsatz und Struktur.
- Beispiel: Webanwendungen nutzen asynchrone Verarbeitung zur Effizienzsteigerung.

## Herausforderungen
- Nebenläufigkeit erhöht die Komplexität im Vergleich zu Single-Thread-Programmen.
- Probleme wie Race Conditions, Deadlocks und Debugging erschweren die Umsetzung.

## Mythen über Nebenläufigkeit
- Nebenläufigkeit verbessert nicht immer die Leistung.
- Nebenläufige Programme erfordern oft völlig andere Designs.
## Defensive Programmierprinzipien
- **Single-Responsibility-Prinzip**: Nebenläufige Logik von anderen Komponenten trennen.
- Datenkapselung und minimaler Zugriff auf gemeinsam genutzte Daten.
- Nutzung von Datenkopien zur Fehlervermeidung.
- Threads sollten möglichst unabhängig agieren.
## Best Practices
- Kritische Abschnitte im Code so klein wie möglich halten.
- Synchronisation nur sparsam einsetzen.
- Nutzung von Tools wie `java.util.concurrent` für threadsichere Datenstrukturen und Locks.

## Klassische Nebenläufigkeitsprobleme

| **Problem**                  | **Beschreibung**                                                                                   |
| ---------------------------- | -------------------------------------------------------------------------------------------------- |
| **Gebundene Ressourcen**     | Feste Anzahl von Ressourcen wie Datenbankverbindungen oder Puffer, die von Threads geteilt werden. |
| **Gegenseitiger Ausschluss** | Nur ein Thread kann gleichzeitig auf gemeinsame Daten oder Ressourcen zugreifen.                   |
| **Verhungern (Starvation)**  | Langsame Threads werden blockiert, da schnelle Threads bevorzugt behandelt werden.                 |
| **Deadlock**                 | Threads warten endlos, da jeder auf Ressourcen wartet, die von anderen Threads blockiert werden.   |
| **Livelock**                 | Threads behindern sich gegenseitig, machen aber keine Fortschritte, da sie ständig reagieren.      |
**Erzeuger-Verbraucher**
- Erzeuger fügen Produkte in eine begrenzte Queue ein, Verbraucher entnehmen sie.
- Problem: Queue kann voll oder leer sein.
- Lösung: Signale zwischen Erzeuger und Verbraucher.

**Leser-Schreiber**

- Leser lesen, Schreiber aktualisieren eine gemeinsame Ressource.
- Problem: Ungleichgewicht kann Verhungern oder Stau verursachen.
- Lösung: Leser und Schreiber priorisieren und balancieren.

**Philosophenproblem**

- Philosophen konkurrieren um begrenzte Ressourcen (Gabeln).
- Problem: Deadlocks und Blockaden durch Ressourcenkonflikte.
- Lösung: Effiziente Ressourcenzuweisung.

## Threaded-Code testen

- Testen von nebenläufigem Code ist komplex und oft schwer reproduzierbar.
- **Empfehlung**: Behandeln Sie selten auftretende Fehler immer als potenzielle Threading-Probleme.

#### Schritte zum Testen

1. **Nonthreaded-Code zuerst zum Laufen bringen**: Sicherstellen, dass der Code ohne Threads fehlerfrei funktioniert.
2. **Threaded-Code modular und anpassbar machen**: Threads sollten keine fixen Abhängigkeiten haben.
3. **Mehr Threads als Prozessoren nutzen**: Belastungstests mit höherer Thread-Zahl zur Identifikation von Schwachstellen.

#### Wichtige Teststrategien
- Code auf unterschiedlichen Plattformen ausführen
- Tools verwenden, um absichtlich Deadlocks und Race Conditions zu simulieren
- Code instrumentieren

## Konzepte
#### Locking
Mechanismus, der den Zugriff auf eine gemeinsam genutzte Ressource durch mehrere Threads regelt, sodass nur ein Thread die Ressource gleichzeitig verwenden kann, um Datenkorruption zu vermeiden.

#### Synchronisation  
Technik, um Threads so zu koordinieren, dass sie in einer bestimmten Reihenfolge arbeiten oder aufeinander warten, um Konflikte zu vermeiden und konsistente Ergebnisse sicherzustellen.
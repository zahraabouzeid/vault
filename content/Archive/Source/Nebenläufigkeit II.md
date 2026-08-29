## A.1 Client/Server-Beispiel
- Einfache Client/Server-Architektur, Server wartet auf Client-Anfragen.
- Problem: sequentielle Verarbeitung limitiert den Durchsatz.
- Ursache für Engpässe: I/O- oder CPU-bound Tasks.
- Lösung: Threads hinzufügen.
- Nachteile: unbegrenzte Thread-Erstellung, vermischte Verantwortlichkeiten.
- Verbesserung durch saubere Trennung: Verbindung, Verarbeitung, Thread-Management, Shutdown.
- Anwendung des **Single-Responsibility-Prinzips**.
- Neue Struktur: `ClientConnection`, `ClientRequestProcessor`, `ClientScheduler`.
- `ClientScheduler` ist ein funktionales Interface .
## A.2 Mögliche Ausführungspfade
- Beispiel: einfache Methode `++lastIdUsed`.
- Bei mehreren Threads gibt es viele Ausführungspfade.
- Java-Code → 8 Bytecode-Zeilen → bei 2 Threads bis zu **12.870 Pfade**.
- Synchronisation (`synchronized`) reduziert Pfade (z. B. auf 2 für 2 Pfade).
- Eine atomare Operation ist eine Operation die nicht unterbrochen werden kann.
- Laut JVM-Spezifikationen eine 32 Bit Zuweisung (wie int) ist atomar und darf nicht unterbrochen werden. Jedoch eine 64 Bit Zuweisung (wie long) ist nicht atomar, denn laut JVM-Spezifikation erfordert die Zuweisung zu einem 64-Bit-Wert zwei 32-Bit-Zuweisungen. Zwischen der ersten und der zweiten 32-Bit-Zuweisung könnte ein anderer Thread dazwischengehen und einen der Werte ändern
- ++-Operator ist **nicht atomar**, da er aus mehreren Bytecode-Operationen besteht.
- Frame: Jeder Methodenaufruf erfordert ein Frame. Das Frame enthält die Rückkehradresse, die Parameter, die an die Methode übergeben wurden, und die lokalen Variablen, die in der Methode definiert werden. Es handelt sich um eine Standardtechnik, um einen Aufruf-Stack (call stack) zu definieren. Sie wird in modernen Sprachen verwendet, um grundlegende Funktions- oder Methodenaufrufe, inklusive rekursiver Aufrufe, zu ermöglichen.
- Lokale Variable: Alle Variablen, deren Geltungsbereich auf die Methode beschränkt ist. Alle nicht-statischen Methoden verfügen über wenigstens eine Variable, this, die das gegenwärtige Objekt repräsentiert, das Objekt, das die (in dem gegenwärtigen Thread) letzte Nachricht empfangen hat, die den Aufruf der Methode ausgelöst hat. 
- Operanden-Stack: Viele Anweisungen in der Java Virtual Machine haben Parameter. Der Operanden-Stack ist der Ort, an dem diese Parameter abgelegt werden. Der Stack hat eine Standard-UFO-Struktur (last-in, first-out).
- Wichtig um in Threads programmieren zu können: 
	- wo Objekte/Werte gemeinsam genutzt werden
	- welcher Code Probleme bei nebenläufigen Lese/Update-Operationen auslösen kann
	- wie Sie solche Probleme der nebenläufigen Programmierung vermeiden können.
## A.3 Lernen Sie Ihre Library kennen
- Empfehlung: Verwendung von `Executor` und `Future` aus `java.util.concurrent`.
- Vorteile: saubere Trennung, skalierbarer Threadpool, Ergebnisverwaltung per Future.
- **Nicht-blockierende Ansätze** mit `AtomicInteger`, `compareAndSwap` (CAS).
- CAS ist oft performanter als `synchronized`.
- Vorsicht bei nicht thread-sicheren Klassen wie `SimpleDateFormat`, JDBC, `HashMap`.
- Lösungsmöglichkeiten:
    - clientbasiertes Locking (mit `synchronized`)
    - serverbasiertes Locking (z. B. `ConcurrentHashMap` mit `putIfAbsent`)
## A.4 Abhängigkeiten zwischen Methoden
- Beispiel mit `IntegerIterator`: `hasNext()` und `next()` sind einzeln synchronisiert, aber nicht zusammen.
- Problem: Threads können zwischen `hasNext()` und `next()` unterbrochen werden → Inkonsistenzen.
- **Clientbasiertes Locking**: `synchronized`-Block um beide Methoden.
    - Gefahr: DRY-Verstoß, leicht fehleranfällig.
- **Serverbasiertes Locking**: Methoden kombiniert (`getNextOrNull()`), interne Synchronisation.
- Vorteile:
    - weniger Wiederholungen
    - geringere Fehleranfälligkeit
    - encapsulation der Sperrlogik
## A.5 Den Durchsatz verbessern
- Szenario: mehrere Webseiten herunterladen und parsen.
- Single-Threaded: 1 Seite = 1s I/O + 0.5s Parsing → langsam.
- Multi-Threaded: I/O und Parsing parallel → CPU wird besser genutzt.
- Ideal: 3 Threads → 3-facher Durchsatz.
- Wichtig: kleine, gezielte Synchronisationsblöcke.
## A.6 Deadlock (s. 395)
- Tritt auf, wenn:
    1. Gegenseitiger Ausschluss
    2. Sperren & Warten
    3. Keine Präemption
    4. Zirkuläres Warten
- Vermeidungsstrategien:
    - gegenseitiger Ausschluss aufheben (z. B. durch atomare Klassen)
    - Sperren vermeiden und bei Blockade Ressourcen freigeben
    - Ressourcenreihenfolge einhalten (globale Ordnung)
    - präemptives Entziehen von Ressourcen
- Problemfälle sind oft schwer reproduzierbar → besonders tückisch.
## A.7 Multithreaded-Code testen
- Beispiel-Test zeigt, dass `++nextId` nicht thread-sicher ist.
- Zwei Threads → inkonsistente Ergebnisse.
- Problem: Fehler tritt selten auf → viele Iterationen nötig (Millionen).
- Fazit: Threading-Probleme sind schwer testbar.
## A.8 Threadbasierten Code mit Tools testen
- **IBM ConTest**.
- Es erhöht die Wahrscheinlichkeit für das Auftreten von Threading-Fehlern.
- Vorgehensweise:
    - Produktionstestcode schreiben
    - mit ConTest instrumentieren
    - auf verschiedenen Plattformen unter Last testen
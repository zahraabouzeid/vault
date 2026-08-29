## Was ist ein Thread?
Ein Thread ist ein Ausführungsstrang innerhalb eines Prozesses. Threads ermöglichen die gleichzeitige Ausführung mehrerer Aufgaben (Multithreading). Im Gegensatz zu Prozessen teilen sich Threads denselben Speicherbereich.

## Vorteile von Multithreading
- Bessere Ressourcennutzung
- Höhere Leistung
- Reaktionsfähigere Anwendungen

## Thread-Erstellung in Java

#### 1. Thread-Klasse erweitern
```java
public class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println("This code is running in a thread");
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread t1 = new MyThread();  
        t1.start();
    }
}
```

#### 2. Runnable-Interface implementieren
```java
public class MyRunnable implements Runnable {
    @Override
    public void run() {
        System.out.println("This code is running in a thread");
    }
}

public class Main {
    public static void main(String[] args) {
        Thread t1 = new Thread(new MyRunnable());
        t1.start();
    }
}
```

## Lebenszyklus eines Threads
1. **NEW** erstellt
2. **RUNNABLE** bereit, wartet auf CPU
3. **RUNNING** wird ausgeführt
4. **WAITING/TIMED_WAITING** wartet (entweder unbegrenzt oder zeitlich begrenzt)
5. **TERMINATED** beendet

## Wichtige Methoden:
- `start()`: Thread starten
- `run()`: enthaltener Code
- `join()`: auf anderen Thread warten
- `sleep(ms)`: pausieren
- `interrupt()`: unterbrechen
## Arten von Threads
- **Userspace-Threads**: verwaltet durch Programme/Bibliotheken
- **Kernel-Threads**: vom Betriebssystem verwaltet
## Spezialfälle:
- **Main Thread**: startet zuerst, UI läuft hier
- **Worker Threads (Thread-Pools)**: Aufgaben aus Queue
- **Real-Time Threads**: garantierte Ausführungszeit
- **Daemon Threads**: Hintergrundprozesse, keine Blockierung des Programmendes

## Steuerung und Priorität
- `setPriority(int)` – Werte zwischen 1 (niedrig) und 10 (hoch)
- Scheduler kann Prioritäten berücksichtigen – jedoch keine Garantie

## Probleme bei Multithreading
- **Race Conditions**: gleichzeitiger Zugriff auf Ressourcen verursacht unvorhersehbares Verhalten
- **Deadlocks**: gegenseitiges Blockieren durch Ressourcenabhängigkeit
- **Livelocks**: Threads "weichen sich aus", aber es passiert nichts
## Vermeidungstechniken
- **Sperrmechanismen**: Lock, Mutex, Semaphore
- **Synchronisierte Blöcke**: `synchronized` in Java
- **Atomare Operationen**: z.B. `AtomicInteger` → ununterbrechbare Operationen
## Best Practices
- Verwende Synchronisation, um Daten zu schützen
- Nutze Thread-Pools für effiziente Verwaltung
- Bevorzuge `Runnable` für bessere Struktur und Flexibilität
# Systeme
## Konstruktion und Anwendung eines Systems trennen
- Software-Systeme sollten den Startup-Prozess (Konstruktion der Objekte und Abhängigkeiten) von der Laufzeit-Logik trennen.
- Der Startup-Prozess ist ein wichtiger Verantwortlichkeitsbereich, der separat behandelt werden sollte.
- Eine konsistente Strategie zur Auflösung der Haupt-Dependencies sollte angewendet werden.
- Systeme brauchen domänenspezifische Sprachen.
- Immer die einfachste funktionierende Lösung wählen

## Trennung
- Die Konstruktion kann durch Verschieben aller Konstruktionsaspekte in Module, die von `main` aufgerufen werden, von der Anwendung getrennt werden.
- Das restliche System wird unter der Annahme konzipiert, dass alle Objekte korrekt konstruiert und verknüpft sind.
- Die `main`-Funktion erstellt die benötigten Objekte und übergibt sie an die Anwendung.

## Factories
- In manchen Fällen ist die Anwendung selbst für die Objekt-Erstellung verantwortlich.
- Das Abstract Factory-Pattern ermöglicht es der Anwendung, die Kontrolle über den Erstellungszeitpunkt zu behalten, während die Details der Konstruktion vom Anwendungscode getrennt werden.

## Dependency Injection
- **Dependency Injection (DI)**: Technik zur Trennung von Konstruktion und Anwendung, indem ein Objekt seine Abhängigkeiten nicht selbst instanziiert, sondern an einen externen Mechanismus delegiert (Inversion of Control).
- **JNDI-Lookups**: Teilweise DI, bei dem ein Objekt einen Verzeichnis-Server nach einem Service abfragt, aber das aufrufende Objekt löst aktiv die Abhängigkeit auf.
- **Echte DI**: Ein DI-Container übernimmt die Verantwortung für die Instanziierung und Verknüpfung der Abhängigkeiten, indem er Setter-Methoden oder Konstruktor-Argumente verwendet, um Dependencies einzufügen.
- **Spring Framework**: Bekannter DI-Container für Java, der Abhängigkeiten durch eine XML-Konfigurationsdatei definiert und verwaltet.
- **Lazy Initialization**: Einige DI-Container unterstützen Lazy Initialization, bei der Objekte erst instanziiert werden, wenn sie benötigt werden, sowie Optimierungen durch Factories und Proxies.

## Cross-Cutting Concerns
Betreffen mehrere Objekte und erfordern eine einheitliche Strategie (z.B. Persistenz, Sicherheit, Transaktionen).

## EJB2-Architektur
Trennung durch Deployment-Deskriptoren für Transaktionen, Sicherheit.

## Aspect-Oriented Programming (AOP)
- Ermöglicht nicht-invasive Trennung.
- Spezifiziert konsistentes Verhalten über das System hinweg.
- Veränderung des Hauptcodes wird vermieden.

## Trennung von Concerns
Softwarearchitektur kann flexibel geändert werden, wenn Concerns gut getrennt sind.

## Entscheidungsfindung
- Dezentralisierte Entscheidungen
- Verantwortung delegieren
- Entscheidungen aufschieben
- Keine voreiligen Entscheidungen
- Mehr Infos = bessere Entscheidungen
Design Principles sind bewährte Richtlinien für sauberen, flexiblen und wartbaren Code. Sie helfen dir, Software so zu strukturieren, dass sie:
- **leicht anpassbar** bleibt (auch bei neuen Anforderungen)
- **robust** gegen Fehler ist
- **verständlich** für dich und dein Team

Ohne Prinzipien wird Code schnell unübersichtlich (Spaghetti-Code). Änderungen sind riskant und aufwendig. Mit Prinzipien bleibt die Codebasis organisiert, selbst wenn das Projekt wächst.
## SOLID
#### Single Responsibility Principle (SRP)
Jede Klasse bzw. Komponente sollte nur einen einzigen Verantwortungsbereich haben und nur einen Grund für Änderungen bieten.

#### Open/Closed Principle (OCP)
Software-Module sollen offen für Erweiterungen, aber geschlossen für Modifikationen sein. Neue Funktionalität wird durch Erweiterung (Vererbung, Dekoration o. Ä.) hinzugefügt, nicht durch Änderung bestehender Klassen.
#### Liskov Substitution Principle (LSP)
Objekte von abgeleiteten Klassen müssen sich so verhalten, dass sie überall dort eingesetzt werden können, wo Objekte der Basisklasse erwartet werden, ohne das korrekte Verhalten zu verletzen.
#### Interface Segregation Principle (ISP)
Schnittstellen sollten so fein granuliert sein, dass Clients nur die Methoden kennen und implementieren müssen, die sie tatsächlich benötigen. Große, allgemeine Interfaces werden aufgeteilt in spezifische Teil‐Interfaces.
#### Dependency Inversion Principle (DIP)  
Hochwertige (“hohe”) Module sollten nicht von niederen Modulen abhängen; beide sollten von Abstraktionen (Interfaces oder abstrakten Klassen) abhängen. Abstraktionen sollten nicht von Details abhängen, sondern Details von Abstraktionen.
## Ergänzende Prinzipien

#### Don’t Repeat Yourself (DRY)
Gleiche Logik oder Daten sollten nur einmal im System vorkommen, um Redundanz und Inkonsistenzen zu vermeiden.
#### Keep It Simple, Stupid (KISS)
Lösungen sollten so einfach wie möglich gehalten werden, komplexität nur dort einführen, wo sie wirklich nötig ist.
#### You Aren’t Gonna Need It (YAGNI)
Funktionen und Erweiterungen sollen erst dann implementiert werden, wenn sie tatsächlich gebraucht werden.

# Objekte und Datenstrukturen
## Datenabstraktion
- die Essenz der von Datenstrukturen generierten Daten zu manipulieren, ohne deren Implementierung kennen zu müssen.
- die spezifische Funktionsweise unserer Objekte durch die Verwendung von Variablen und Objekt oder Funktionswrappern zu verbergen, sodass nur unsere Daten durchscheinen. 

## Daten/Objekt-Anti-Symmetrie
- Objekte sollten Funktionen bereitstellen, die auf ihren Daten operieren.
- Datenstrukturen sollten ihre Daten offenlegen, ohne neue Funktionen dazu hinzufügen zu müssen.
- Es gibt eine Anti-Symmetrie zwischen den Rollen von Datenstrukturen und Objekten im Programm. Was für das eine gut ist, ist für das andere nicht gut.
- In einem komplexen System, gibt es jeweils Situationen wo wie Datenstrukturen benötigen und andere Situationen wo wir Objekte verwenden müssen.

## Das Law of Demeter
Eine Methode/Funktion sollte nur Methoden aufrufen, die:
- In ihrer eigenen Klasse sind.
- Von ihr selbst erstellt werden.
- Als Parameter an die Funktion selbst übergeben werden.
- In einer Instanzvariablen der Klasse enthalten sind. 

## Datentransfer-Objekte
- Datenstrukturen sollen public Variablen und keine Funktionen haben. 
- Sie wird als Datentransfer-Objekt bezeichnet. Sie sind nützliche Strukturen, besonders für die Kommunikation mit Datenbanken oder beim Parsen von Nachrichten von Sockets usw. 
- Active Records sind eine spezielle Form von DTOs. 
- Sie sind Datenstrukturen mit öffentlichen Variablen.
- Sie verfügen aber üblicherweise auch über Navigationsmethoden wie `save` oder `find`.
- Objekte sollen private Variablen und public Funktionen haben.


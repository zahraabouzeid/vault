# Klassen

## Stepdown Regel
- Code sollte sich wie eine Top-down-Erzählung lesen. 
- Auf jede Methode sollten Methoden auf der nächsten Abstraktionsebene folgen, damit wir das Programm lesen können, indem wir beim Durchlesen der Methodenliste jeweils eine Abstraktionsebene nach der anderen absteigen.

## Einkapselung
- Variablen und Funktionen sollten privat sein, aber Tests haben Priorität.
- Wenn Tests darauf zugreifen müssen, können sie als protected oder mit Package-Geltungsbereich deklariert werden.

## Klassen sollten klein sein
- Klassen sollten klein sein.
- Die Größe von Klassen wird durch ihre Verantwortlichkeiten (Responsibilities) gemessen, nicht durch die Anzahl der Codezeilen.
- Der Name einer Klasse sollte ihre Verantwortlichkeiten widerspiegeln.
- Ein unprägnanter Name deutet auf eine zu große Klasse hin.
- Eine Klasse sollte in 25 Wörtern beschrieben werden können.
- Ein "und" in der Beschreibung ist ein Hinweis auf zu viele Verantwortlichkeiten.

## Single Responsibility Prinzip
- Das Single-Responsibility-Prinzip (SRP) besagt, dass eine Klasse oder ein Modul nur einen Grund zur Änderung haben sollte.
- Es definiert die Verantwortlichkeit und dient als Richtlinie für die Klassengröße.
- Klassen sollten nur eine Verantwortlichkeit haben.

## Wie viele Klassen soll ein System enthalten?
- Ein System mit vielen kleinen Klassen ist nicht komplexer als eines mit wenigen großen Klassen.
- Bei großen Klassen muss man sich durch unnötige Komplexität wühlen.
- Systeme sollten aus vielen kleinen Klassen bestehen, jede mit einer einzigen Verantwortlichkeit und einem Grund zur Änderung.

## Kohäsion
- Klassen sollten nur eine kleine Anzahl an Instanzvariablen haben.
- Jede Methode sollte eine oder mehrere dieser Variablen manipulieren.
- Eine hohe Kohäsion bedeutet, dass Methoden und Variablen logisch zusammenhängen.
- Eine Klasse ist maximal kohäsiv, wenn jede Methode jede Variable verwendet.
- Wenn Funktionen Variablen teilen, sollten sie in eine eigene Klasse ausgelagert werden.

## Änderungen
Ein sauberes System minimiert das Risiko von Fehlfunktionen, indem es Klassen so strukturiert, dass Änderungen den Rest des Systems nicht beeinträchtigen.

## Open Closed Prinzip
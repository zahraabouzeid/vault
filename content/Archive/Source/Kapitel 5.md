# Formatierung
## Vertikale Formatierung
- Vorgeschlagen ist, dass Quelldateien um die 200 Zeilen lang sein sollen, wobei die Obergrenze bei 500 Zeilen liegt.
- Kleine Dateien sind normalerweise leichter zu verstehen als große.
#### Die Zeitungs-Metapher
- Die oberen Teile der Quelldatei sollten die allgemeineren Konzepte und Algorithmen enthalten. 
- Die Detailtiefe sollte nach unten hinzunehmen, bis wir am Ende der Quelldatei die am niedrigsten angesiedelten Funktionen und Details finden.

#### Vertikale Offenheit zwischen Konzepten
Leerzeilen erleichtern die Lesbarkeit. Wenn wir sie auslassen, merken wir, dass die Lesbarkeit des Codes deutlich verschlechtert wird.
#### Vertikale Dichte
Codezeilen, die eng zusammengehören, sollen vertikal dicht beieinanderstehen.
#### Vertikaler Abstand
- Konzepte, die eng verwandt sind, sollten vertikal eng beisammenstehen.
- Eng verwandte Konzepte sollen nicht auf verschiedene Dateien verteilt werden. (mit Ausnahmen)
- `protected` Variablen sollten vermieden werden.
- Variablendeklarationen sollten so eng bei ihrem Verwendungsort wie möglich deklariert werden. 
- Lokale Variablen am Anfang einer Funktion stehen.
- Instanzvariablen sollten am Anfang der Klasse deklariert werden.
- Wenn eine Funktion eine andere aufruft, sollten sie vertikal eng beisammenstehen, und die aufrufende Funktion sollte über der aufgerufenen Funktion stehen, falls möglich.
#### Vertikale Anordnung
Eine Funktion, die aufgerufen wird, sollte sich unter einer Funktion befinden,
von der sie aufgerufen wird.

## Horizontale Formatierung
#### Zeilenbreite
- wir sollten möglichst kurze Zeilen bevorzugen. 
- Zeilenbreite sollte rund um die  80 sein. 120 ist okay.
#### Horizontale Offenheit und Dichte
- die Zuweisungsoperatoren sollten mit Whitespace umgegeben werden, um sie zu betonen.
- Mit Whitespace kann man auch den Vorrang von Operatoren hervorheben.

#### Einrückung
- die meisten Klassendeklarationen, werden nicht eingerückt. 
- Methoden innerhalb einer Klasse werden eine Stufe nach rechts innerhalb ihrer Klasse eingerückt. 
- Implementierungen dieser Methoden werden eine Stufe weiter rechts innerhalb der Methoden-Definition eingerückt.
- Block-Implementierungen werden eine Stufe weiter nach rechts innerhalb des einschließenden Blocks eingerückt usw.

## Team-Regeln
- Wenn ein Programmierer im Team arbeitet, hat das Team Vorrang.
- Ein Team sollte den gleichen Stil verfolgen.
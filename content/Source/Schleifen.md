## Arten von Schleifen
- Bedingungsgesteuerte Schleifen: `while` und `do-while` Schleifen
- Zählgesteuerte Schleife: `for` Schleife
## while Schleife

```java
while(Bedingung) {
   // Anweisungen
}
```
- ist kopfgesteuert und abweisend.
- führt einen Codeblock wiederholt aus, solange eine gegebene Bedingung wahr ist.
- ist eine Eingabesteuerungsschleife, bei der die Bedingung vor der Ausführung des Schleifenrumpfs überprüft wird.

## for Schleife
```java
for(int i=0; i<10; i+=) {
   // Anweisungen
}
```
- ist nützlich, wenn bekannt ist, wie oft eine Aufgabe wiederholt werden soll, bzw. wenn die Wiederholung abhängig ist von einem Wert der einen Anfang und ein Ende hat und immer in der gleichen Art verändert wird.
- wie die while-Schleife ist die for-Schleife ebenfalls eine Eingabesteuerungsschleife, bei der die gegebene Bedingung zuerst ausgeführt wird.

## do-while Schleife
```java
do {
   // Anweisungen
} while(Bedingung);
```
- ist fußgesteuert und nicht abweisend.
- ist der while-Schleife ähnlich, mit dem Unterschied, dass eine do-while-Schleife mindestens einmal ausgeführt wird.
- ist eine Ausgabesteuerungsschleife, bei der die Bedingung erst nach der Ausführung des Schleifenrumpfs überprüft wird.

## for-each Schleife
```java
for(declaration : expression) {
   // Anweisungen
}
```
- ist eine spezielle Wiederholungssteuerungsstruktur, die es ermöglicht, eine Schleife effizient zu schreiben, die eine bestimmte Anzahl von Malen ausgeführt werden muss.
- ist besonders nützlich, wenn nicht bekannt ist, wie oft eine Aufgabe wiederholt werden soll.

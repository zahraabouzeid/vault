## If Anweisung (Einseitige Verzweigung)
In Java wird die `if` Anweisung verwendet, um einen Codeblock basierend auf einer gegebenen Bedingung auszuführen. Eine `if` Anweisung wird ausgeführt, wenn der boolesche Ausdruck der `if` Anweisung wahr ist. Wenn der Ausdruck falsch ist, wird der Codeblock einfach übersprungen.
```java
if (Bedingung) { 
	// Codeblock, der ausgeführt wird, wenn die Bedingung wahr ist 
}
```

## If-else Anweisung (Zweiseitige Verzweigung)
In Java wird die `if-else` Anweisung verwendet, um zwei Codeblöcke basierend auf einer gegebenen Bedingung auszuführen. Eine `if` Anweisung wird ausgeführt, wenn der boolesche Ausdruck der `if` Anweisung wahr ist. Eine `if`-Anweisung kann durch eine optionale `else` Anweisung ergänzt werden, die ausgeführt wird, wenn der boolesche Ausdruck falsch ist.

```java
if (Bedingung) { 
	// Codeblock, der ausgeführt wird, wenn die Bedingung wahr ist 
} else { 
	// Codeblock, der ausgeführt wird, wenn die Bedingung falsch ist 
}
```
## Else-if Anweisungen
In Java wird die `if-else if`-Anweisung verwendet, um mehrere Bedingungen nacheinander zu prüfen und basierend auf der ersten wahren Bedingung den entsprechenden Codeblock auszuführen. Wenn die Bedingung der ersten `if`-Anweisung wahr ist, wird der zugehörige Codeblock ausgeführt. Andernfalls werden die Bedingungen der folgenden `else if` Anweisungen geprüft. Wenn keine der Bedingungen wahr ist, kann optional eine `else` Anweisung am Ende hinzugefügt werden, die ausgeführt wird, wenn alle vorherigen Bedingungen falsch sind.

```java
if (Bedingung1) {
    // Codeblock, der ausgeführt wird, wenn Bedingung1 wahr ist
} else if (Bedingung2) {
    // Codeblock, der ausgeführt wird, wenn Bedingung2 wahr ist
} else if (Bedingung3) {
    // Codeblock, der ausgeführt wird, wenn Bedingung3 wahr ist
} else {
    // Codeblock, der ausgeführt wird, wenn keine der Bedingungen wahr ist
}
```

## Switch-case
In Java wird die `switch` Anweisung verwendet, um eine Variable mit mehreren möglichen Werten zu vergleichen und basierend auf dem Wert den entsprechenden Codeblock auszuführen. Jeder mögliche Wert wird durch einen `case` Zweig repräsentiert. Wenn der Wert der Variable mit einem `case` übereinstimmt, wird der zugehörige Codeblock ausgeführt. Die `switch` Anweisung kann auch einen optionalen `default` Zweig enthalten, der ausgeführt wird, wenn kein `case` Wert mit der Variable übereinstimmt.
```java
switch (Variable) {
    case Wert1:
        // Codeblock, der ausgeführt wird, wenn Variable gleich Wert1 ist
        break;
    case Wert2:
        // Codeblock, der ausgeführt wird, wenn Variable gleich Wert2 ist
        break;
    case Wert3:
        // Codeblock, der ausgeführt wird, wenn Variable gleich Wert3 ist
        break;
    default:
        // Codeblock, der ausgeführt wird, wenn keine Übereinstimmung gefunden wird
}
```
- Mit `switch-case` kann man keine Nachkommazahlen, Wertebereichen und Formeln vergleichen. Strings sind erst ab Java 7 in einem `switch-case` Struktur vergleichbar.
- Andererseits ist eine switch Variable von Datentyp Int, byte, short, long, enums oder char zulässig.
## Vergleichsoperatoren
| **Operator** | **Erklärung**  | **Beispiel**   |
| ------------ | -------------- | -------------- |
| `==`         | ist gleich     | `zahl == 15`   |
| `!=`         | ist ungleich   | `zahl != 0`    |
| `!`          | Nicht          | `!(zahl == 1)` |
| `>`          | größer         | `zahl > 10`    |
| `<`          | kleiner        | `zahl < 5`     |
| `>=`         | größer gleich  | `zahl >= 20`   |
| `<=`         | kleiner gleich | `zahl <= 8`    |
## Logische Operatoren

| **Bedingung A** | **Bedingung B** | **A && B** | **A \|\| B** |
|-----------------|-----------------|------------|--------------|
| false           | false           | false      | false        |
| false           | true            | false      | true         |
| true            | false           | false      | true         |
| true            | true            | true       | true         |
## Strings vergleichen
In Java kann man Strings nicht direkt mit dem Gleichheitsoperator `==` vergleichen, da dieser nur überprüft, ob beide Referenzen auf dasselbe Objekt verweisen, nicht ob die Inhalte der Strings gleich sind.

### equals()

```java
String wort = "Prima";

if ("Prima".equals(wort)) {
    System.out.println("Das Wort ist: " + wort);
} else {
    System.out.println("Das Wort stimmt nicht überein.");
}
```
### compareTo()
```java
String referenceName = "Charlie";
String userInput = "Alice"; 

int comparisonResult = userInput.compareTo(referenceName);

if (comparisonResult < 0) {
    System.out.println(userInput + " kommt vor " + referenceName);
} else if (comparisonResult > 0) {
    System.out.println(userInput + " kommt nach " + referenceName);
} else {
    System.out.println(userInput + " ist gleich " + referenceName);
}
```
**Ausgabe**
```text
Alice kommt vor Charlie
```

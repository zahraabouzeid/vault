## Definition
- Eine Variable bietet uns benannten Speicher, den unsere Programme manipulieren können. 
- Variablen sind Platzhalter für Werte oder Zeichen, die während der Laufzeit gespeichert werden sollen.
- Eine Variable hat einen bestimmten Typ, der die Größe und das Layout des Speichers der Variablen bestimmt, den Wertebereich, der in diesem Speicher gespeichert werden kann, und die Menge der Operationen, die auf die Variable angewendet werden können.

## Deklaration von Variablen
Um eine Variable zu benutzen, muss man sie zuerst deklarieren. Bei der Deklaration einer Variable wird:
- Speicherplatz für eine Variable reserviert. 
- ein Name vereinbart, mit dem der Speicherplatz angesprochen werden kann.
- der Datentyp festgelegt, der die Art der Werte bestimmt, die in der Variable gespeichert werden dürfen. 
-  Aus dem Datentyp bestimmt der Rechner, wieviel Byte er für die Variable im Speicher reservieren muss.

## Deklaration, Initialisierung und Zuweisung
```java
public class Rechnen
{
	public static void main(String[] args) {
		int menge;
		double einzelpreis = 15.8, mwst = 0.19, gesamtpreis;
		menge = 20;
		gesampreis = einzelpreis * menge * (1 + mwst);
		System.out.println("Gesamtpreis: " + gesamtpreis + ".");
	}//public static void main(String[] args)
}//public class Rechnen
```

Bei der Deklaration einer Variablen kann man ihr direkt einen Wert zuweisen, was als Initialisierung bezeichnet wird, wie bei der Variablen `einzelpreis`. Alternativ kann man nur den Datentyp festlegen und ihr später einen Wert zuweisen, was dann als Zuweisung bezeichnet wird, wie bei der Variablen `menge`.

```java
final double mwst = 0.19;
```
Deklariert man eine Variable mit `final`, wird sie zu einer Konstante, und ihr Wert kann später nicht mehr geändert werden. Das bedeutet, dass eine erneute Zuweisung nicht möglich ist, und die Variable muss zwingend bei ihrer Deklaration initialisiert werden.
>[!info]
>Ein Speicherplatz ist eine bestimmte Adresse im Arbeitsspeicher.

## Regel und Namenskonvention
Regeln sind zwingend einzuhalten und werden von der Programmiersprache selbst oder den Entwicklungswerkzeugen durchgesetzt. Folgende Regeln sind zu beachten:
- dürfen Buchstaben, Zahlen und Unterstrich enthalten
- Groß und Kleinschreibung beachten (Java ist Case Sensitive)
- Keine Zahlen am Anfang
- Keine Sonderzeichen
- Keine Leerzeichen
- Keine Operatoren (+ - * / %)
- Keine reservierten Worte (class, out, print)

**Namenskonvention**: sind empfohlene, aber nicht zwingend vorgeschriebene Richtlinien, die dazu dienen, den Code lesbarer und konsistenter zu gestalten. Beispielsweise ist es in Java üblich, Variablennamen im CamelCase-Stil zu schreiben (z. B. `einzelPreis`). Empfohlen ist folgendes:
- Zweckbeschreibende Namen zu benutzen
- Ungarische Notation (Datentyp als Präfix, z. B `intMenge`)
- Klassen mit einer Großbuchstabe anfangen

## Datentypen
| Datentyp  | Speichergröße (Bit) | Beispiel              | Kleinster Wert  | Größter Wert               |
| --------- | ------------------- | --------------------- | --------------- | -------------------------- |
| `char`    | 16                  | `char zeichen = 'Z';` | Unicode 0       | Unicode 2<sup>16</sup> - 1 |
| `byte`    | 8                   | `byte b = 65;`        | -128            | 127                        |
| `short`   | 16                  | `short s = 65;`       | -2<sup>15</sup> | 2<sup>15</sup> - 1         |
| `int`     | 32                  | `int i = 65;`         | -2<sup>31</sup> | 2<sup>31</sup> - 1         |
| `long`    | 64                  | `long l = 65L;`       | -2<sup>63</sup> | 2<sup>63</sup> - 1         |
| `float`   | 32                  | `float f = 65f;`      |                 |                            |
| `double`  | 64                  | `double d = 65.55;`   |                 |                            |
| `boolean` | 1                   | `boolean b = true;`   |                 |                            |
## Operatoren
| Operator | Beschreibung                                                                     |
| -------- | -------------------------------------------------------------------------------- |
| `+`      | Addiert die Werte auf beiden Seiten des Operators.                               |
| `-`      | Subtrahiert den rechten Operanden vom linken Operanden.                          |
| `*`      | Multipliziert die Werte auf beiden Seiten des Operators.                         |
| `/`      | Teilt den linken Operanden durch den rechten Operanden.                          |
| `%`      | Teilt den linken Operanden durch den rechten Operanden und gibt den Rest zurück. |
| `++`     | Erhöht den Wert des Operanden um 1. (Inkrementierung)                            |
| `--`     | Verringert den Wert des Operanden um 1. (Dekrementierung)                        |
- `summe += 5` erhöht den Wert von `summe` um 5, entspricht auch `summe = summe + 5`
- `summe *= 5` multipliziert den aktuellen Wert von `summe` mit 5, entspricht auch `summe = summe * 5`
- `summe -= 5` verringert den Wert von `summe` um 5, entspricht auch `summe = summe - 5`
- `summe /= 5` dividiert den aktuellen Wert von `summe` durch 5, entspricht auch `summe = summe / 5`

## Typumwandlung (Type Casting)

Typumwandlung ist eine Technik, die entweder vom Compiler oder vom Programmierer verwendet wird, um einen Datentyp in einen anderen zu konvertieren. Zum Beispiel: Umwandlung von `int` in `double`.

### implizite Typumwandlung

tritt auf, wenn ein kleinerer Typ in einen größeren Typ konvertiert wird. Dies erfolgt automatisch durch den Compiler.

Hier ist die Hierarchie der erweiterten Typumwandlung in Java:

```text
byte < short < char < int < long < float < double
```
- **`byte`, `short`, `char`**: Diese Typen werden auf den nächstgrößeren Typ `int` erweitert.
- **`int`**: Wird auf den nächstgrößeren Typ `long`, `float`, oder `double` erweitert.
- **`long`**: Wird auf den nächstgrößeren Typ `float` oder `double` erweitert.
- **`float`**: Wird auf den nächstgrößeren Typ `double` erweitert.


Der Compiler übernimmt die Typkonvertierung und die Umwandlung erfolgt nur von einem kleinen Datentyp in einen großen Datentyp.

**Beispiel:**

```java
public class Rechnen {
	int zaehler = 1;
	int nenner = 5;
	double ergebnis;
	ergebnis = zaehler / nenner;
	System.out.print("Ergebnis: " + ergebnis);
}
```

**Ausgabe:**

```text
Ergebnis: 0.0
```

Eine Ganzzahl dividiert durch eine Ganzzahl ergibt einen Ganzzahl, daher wie oben ausgegeben wird das Ergebnis falsch berechnet. Im Gegenteil wenn mindestens einer der Operanden einen double ist `double zaehler`, erfolgt eine implizite Typumwandlung und wird das Ergebnis richtig angezeigt.
```java
public class Beispiel {
	double zaehler = 1;
	int nenner = 5;
	double ergebnis;
	ergebnis = zaehler / nenner;
	System.out.print("Ergebnis: " + ergebnis);
}
```

**Ausgabe:**

```text
Ergebnis: 0.2
```

### Explizite Typumwandlung

wird manuell vom Programmierer durchgeführt. Bei der verengenden Typumwandlung wird ein größerer Typ in einen kleineren Typ konvertiert.
Die Syntax für die verengende Typumwandlung lautet:

```java
double doubleNum = (double) num;
```

Der obige Code konvertiert die Variable in den Typ `double`.
#### Beispiel: 
```java
public class Beispiel {
	public static void main(String[] args) {
	    int zaehler = 1, nenner = 5;
		double ergebnis;
		ergebnis = (double) zaehler / nenner;
		System.out.print("Ergebnis: " + ergebnis);
   }
}
```

**Ausgabe:**

```text
Ergebnis: 0.2
```
Exceptions ermöglichen die Trennung von regulärem Code und Fehlerbehandlung, wodurch Programme robuster und wartbarer werden.

## Merkmale
* der reguläre Ablauf wird nicht durch Fehlerunterbrechungen gestört
* derselbe Fehler kann an unterschiedlichen Stellen auftreten, aber zentral behandelt werden
* Exceptions sind Objekte, die mithilfe von `throw` ausgelöst und mit `catch` abgefangen werden
## try-catch-Blöcke
* **try:** Enthält riskanten Code, der eine Exception auslösen könnte.
* **catch:** Fängt spezifische oder allgemeine Exceptions ab und behandelt sie.
* **finally:** Optionaler Block, der immer ausgeführt wird (auch bei `return` oder `exit`).

```java
try {
	riskanteMethode();
} catch (IOException e) {
	e.printStackTrace(System.out);
	System.out.println(e.getMessage());
} finally {
	System.out.println("Aufräumarbeiten abgeschlossen.");
}
```

> [!warning]
> Immer von spezifischen zu allgemeinen `catch` Blöcken arbeiten.  So wird sichergestellt, dass spezifische Fehler passend behandelt werden können.
## Multicatch (Java 7 und höher)
Ermöglicht das Abfangen mehrerer Exceptions in einem `catch` Block.
```java
try {
	double result = calcHypothenuse(-5, 0);
} catch (IllegalArgumentException | ArithmeticException e) {
	System.out.println("Fehler: " + e.getMessage());
}
```

## Exceptions auslösen
* Mit `throw` wird eine Exception manuell ausgelöst.
* Konstruktoren oder Methoden können die Anlage eines Objekts verhindern oder Fehler signalisieren.
* `throws` deklariert geprüfte Exceptions, die eine Methode auslösen könnte (wenn eine Methode eine Exception auslöst, aber sie nicht abfängt)
```java
public class Spielfigur {
	public Spielfigur(int alter) throws IllegalArgumentException {
		if (alter <= 0) {
			throw new IllegalArgumentException("Alter unzulässig!");
		}
	}
}
```


## Stack-Rewinding

* bei einer ausgelösten Exception wird der Call Stack zurückverfolgt
* alle im `try` Block deklarierten Variablen werden zerstört (deswegen in catch nicht verfügbar)
## Nützliche Runtime-Exceptions
- **NumberFormatException**: Ungültiges Zahlenformat beim Parsen
- **IndexOutOfBoundsException**: Ungültiger Index in Liste/Array/String
- **NegativeArraySizeException**: Array mit negativer Größe erstellt
- **InstantiationException**: Instanzierung einer abstrakten Klasse/Interface
- **UnsupportedOperationException**: Nicht unterstützte Operation
- **IllegalAccessException**: Zugriff auf private/fremde Methoden oder Felder
- **ArithmeticException**: Mathematischer Fehler (z. B. Division durch null)
- **StringIndexOutOfBoundsException**: Ungültiger String-Index
- **IllegalStateException**: Ungültiger Zustand für eine Operation
- **ClassCastException**: Ungültiger Typen-Cast
- **IllegalArgumentException**: Ungültiges Argument an Methode übergeben

>[!info]
>Fehler kann durch `e.printStackTrace()` diagnosiert werden
   
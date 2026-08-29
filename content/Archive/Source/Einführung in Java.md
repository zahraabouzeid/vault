## Vokabeln
**Programm**: Vollständige Anweisungsfolge für eine EDV-Anlage zur Lösung einer konkreten Aufgabe

**Quellcode**: Ursprüngliches, in einer Programmiersprache geschriebenes Programm. Erst nach Compilierung ist ein solches Programm ausführbar.

**Compilieren**: Übersetzung des Quellcodes in Maschinensprache oder Bytecode (Java). Es wird eine ausführbare Datei erzeugt.

**Compiler**: Programm, das Quellcode übersetzt und eine ausführbare Datei erzeugt.

**Interpreter**: Programm, welches Quellcode während der Ausführung übersetzt.

**Syntax**: Rechtschreibung und Grammatik einer Programmiersprache

**Algorithmus**: wiederholbare Handlungsvorschrift zur Lösung einer bestimmten Art von Problemen.

## Erstes Java Programm
```java
public class HelloWorld {
	public static void main(String[] args){
		System.out.println("Hallo Welt!");
	}
}
```

**Ausgabe**
```bash
Hallo Welt
```

### 1. Public Main Class
```java
public class HelloWorld {
```
Diese Zeile erstellt eine neue Klasse HelloWorld, und da sie öffentlich `public` ist, muss diese Klasse in einer Datei mit demselben Namen definiert werden, also `HelloWorld.java`. 
### 2. Public Static Void Main

```java
public static void main(String[] args) {
```

Diese Zeile stellt die `main` Methode dar, die von der JVM aufgerufen wird, wenn dieses Programm in den Speicher geladen wird. Diese Methode wird verwendet, um das Programm auszuführen.
- `public`: definiert den Geltungsbereich der `main` Methode. Da sie öffentlich ist, kann diese Methode von einem externen Programm wie der JVM aufgerufen werden.
- `static`: definiert den Zustand der `main` Methode. Da sie statisch ist, kann diese Methode von einem externen Programm wie der JVM aufgerufen werden, ohne dass zuerst ein Objekt der Klasse erstellt wird.
- `void`: definiert den Rückgabewert der `main` Methode. Da sie `void` ist, gibt diese Methode keinen Wert zurück.
- `main`: Name der Methode.
- `String[] args`: Argumente, die beim Ausführen des Programms über die Befehlszeile (Command Line Arguments) übergeben werden können.

>[!info]
> Die JVM (Java Virtual Machine) ist eine Laufzeitumgebung, die es ermöglicht, Java-Programme auszuführen.
### 3. System.out.println()
```java
System.out.println("Hallo Welt");
```
- `System`: eine Klasse in Java, die grundlegende Systemoperationen bereitstellt.
- `out`: ein Objekt der System Klasse, das den Standardausgabestrom repräsentiert. 
- `println`: eine Methode von `out`, die eine Zeile von Text auf der Konsole ausgibt und dann einen Zeilenumbruch hinzufügt. 
- `"Hallo Welt!"`: ein String, der den Text enthält, der auf der Konsole ausgegeben wird.
- `;`: zeichnet die Ende der Anweisung.
>[!info]
>- Java ist eine objektorientierte Programmiersprache. Eine Funktion in einer Klasse wird Methode genannt.
>- Einrückungen erleichtern die Lesbarkeit.

## Lesbarkeit
```java
/* Das ist ein 
mehrzeiliges Kommentar */

//Einzeiliges Kommentar
```

Diese Zeilen werden vom Java-Compiler nicht berücksichtigt und sind Kommentare. Ein Kommentar hilft dabei, das Programm besser zu strukturieren und zu verstehen und macht den Code lesbar und verständlich.

### Javadoc Kommentare
javadoc Kommentare dokumentieren das Programm.
```java
/** AddTwoNumbers addiert zwei Ganzzahlen und gibt die Ergebnisse aus.
    @author Z. Bou-Zeid */
// ------------------------------------------------------------------

public class AddTwoNumbers{
    public static void main(String[] args) {
        int result;
        int num1 = 10;
        int num2 = 3;
        System.out.println(num1 + num2);
    } //public static void main (String[] args)
} //public class AddTwoNumbers
```

## Vom Quellcode zur Ausführung

Die Übersetzung eines Java-Programms erfolgt in mehreren Schritten. Zunächst übersetzt der Compiler den Quellcode (.java-Datei) in eine Bytecode-Datei (.class). Der Compiler namens `javac` ist Teil des Software Development Kits (SDK) von Oracle. Anschließend wird der Bytecode von einem Interpreter, der Java Virtual Machine (JVM), zur Laufzeit in Maschinensprache übersetzt, sodass der Code auf verschiedenen Computern ausgeführt werden kann. Die JVM gehört zur Java Runtime Environment (JRE), die unabhängig auf Computern installiert oder in Webbrowsern integriert sein kann.

## Escape-Sequenzen:
- `\n`: Neue Zeile (Linefeed)
- `\t`: Tabulator (Tab)
- `\b`: Rückschritt (Backspace)
- `\r`: Wagenrücklauf (Carriage Return)
- `\"`: Doppeltes Anführungszeichen
- `\'`: Einfaches Anführungszeichen
- `\\`: Backslash
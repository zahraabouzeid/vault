
## Operators
#### Arithmetische Operatoren

- `+` Addition
- `-` Subtraktion
- `*` Multiplikation
- `/` Division
- `%` Modulo (Rest)

#### Inkrement/Dekrement

- `++` Inkrement
- `--` Dekrement

#### Vergleichsoperatoren

- `==` Gleich
- `!=` Ungleich
- `>` Größer
- `<` Kleiner
- `>=` Größer oder gleich
- `<=` Kleiner oder gleich

#### Logische Operatoren

- `&&` AND (und)
- `||` OR (oder)
- `!` NOT (nicht)

#### Zuweisungsoperatoren

- `=` Zuweisung
- `+=` Addition und Zuweisung
- `-=` Subtraktion und Zuweisung
- `*=` Multiplikation und Zuweisung
- `/=` Division und Zuweisung
- `%=` Modulo und Zuweisung

#### Bitwise Operatoren

- `&` Bitwise AND
- `|` Bitwise OR
- `^` Bitwise XOR
- `~` Bitwise NOT
- `<<` Left Shift
- `>>` Right Shift
- `>>>` Unsigned Right Shift

#### Ternärer Operator

 `? :` Ternärer (Conditional)

#### Instanceof Operator

`instanceof` Typ-Prüfung

## Vergleichsoperatoren
- `==` Gleich
- `!=` Ungleich
- `>` Größer als
- `<` Kleiner als
- `>=` Größer oder gleich
- `<=` Kleiner oder gleich

## Vergleichsmethoden

### Für Strings

- `.equals()` Inhalt vergleichen
- `.equalsIgnoreCase()` Ignoriert Groß-/Kleinschreibung
- `.compareTo()` Lexikografischer Vergleich (gibt int zurück)
- `.compareToIgnoreCase()` Vergleich ohne Groß-/Kleinschreibung
- `.contentEquals()` Vergleicht mit CharSequence
- `.regionMatches()` Vergleicht Teilbereiche

### Für Objects

- `.equals()` Objekt-Vergleich (überschreibbar)
- `.hashCode()` Hash-Wert (für HashMap, HashSet)
- `==` Referenz-Vergleich (zeigen auf gleiches Objekt)

### Für Arrays

- `Arrays.equals()` Array-Inhalte vergleichen
- `Arrays.deepEquals()` Mehrdimensionale Arrays 

## If-Statements

#### Einfaches If

```java
if (bedingung) {
    // Code
}
```

#### If-Else

```java
if (bedingung) {
    // Code
} else {
    // Alternativer Code
}
```

#### If-Else-If

```java
if (bedingung1) {
    // Code
} else if (bedingung2) {
    // Code
} else {
    // Standard Code
}
```

#### Verschachtelt

```java
if (bedingung1) {
    if (bedingung2) {
        // Code
    }
}
```

#### Ternärer Operator

```java
variable = (bedingung) ? wertWennTrue : wertWennFalse;
```

## Switch-Statement

#### Einfaches Switch

```java
switch (variable) {
    case wert1:
        // Code
        break;
    case wert2:
        // Code
        break;
    default:
        // Standard Code
}
```

#### Fall-through

```java
switch (variable) {
    case wert1:
    case wert2:
    case wert3:
        // Code für alle drei
        break;
}
```

#### Mit String

```java
switch (string) {
    case "text1":
        // Code
        break;
    case "text2":
        // Code
        break;
}
```

#### Mit Enum

```java
switch (enumVariable) {
    case WERT1:
        // Code
        break;
    case WERT2:
        // Code
        break;
}
```

#### Switch Expression

```java
variable = switch (wert) {
    case wert1 -> ergebnis1;
    case wert2 -> ergebnis2;
    default -> standardErgebnis;
};
```

## Primitive Datentypen

### Ganzzahlen

- `byte` 8-bit (-128 bis 127)
- `short` 16-bit (-32,768 bis 32,767)
- `int` 32-bit (-2³¹ bis 2³¹-1)
- `long` 64-bit (-2⁶³ bis 2⁶³-1)

### Fließkommazahlen

- `float` 32-bit (6-7 Dezimalstellen)
- `double` 64-bit (15 Dezimalstellen)

### Andere

- `char` 16-bit (einzelnes Zeichen)
- `boolean` true oder false

```java
int zahl = 10;
double dezimal = 3.14;
char buchstabe = 'A';
boolean istWahr = true;
```

## Referenztypen

### Häufige Typen

- `String` Zeichenkette
- `Array` Sammlung gleicher Typen
- `Class` Eigene Klassen
- `Interface` Schnittstellen
- `Enum` Aufzählungstypen

```java
String text = "Hallo";
int[] array = {1, 2, 3};
Object obj = new Object();
```

## Wrapper-Klassen (für Primitive)

- `Byte` für byte
- `Short` für short
- `Integer` für int
- `Long` für long
- `Float` für float
- `Double` für double
- `Character` für char
- `Boolean` für boolean

```java
Integer zahl = 10;
Double dezimal = 3.14;
```

## String-Methoden

#### length()

```java
int laenge = string.length();
```

#### charAt()

```java
char zeichen = string.charAt(index);
```

#### substring()

```java
String teil = string.substring(start, end);
```

#### indexOf()

```java
int position = string.indexOf("text");
```

#### contains()

```java
boolean enthaelt = string.contains("text");
```

#### replace()

```java
String neu = string.replace("alt", "neu");
```

#### toLowerCase()

```java
String klein = string.toLowerCase();
```

#### toUpperCase()

```java
String gross = string.toUpperCase();
```

#### trim()

```java
String getrimmt = string.trim();
// Entfernt Leerzeichen am Anfang/Ende
```

#### split()

```java
String[] teile = string.split("trennzeichen");
```

#### startsWith()

```java
boolean startet = string.startsWith("prefix");
```

#### endsWith()

```java
boolean endet = string.endsWith("suffix");
```

#### isEmpty()

```java
boolean leer = string.isEmpty();
```

#### equalsIgnoreCase()

```java
boolean gleich = string1.equalsIgnoreCase(string2);
// Vergleich ohne Groß-/Kleinschreibung
```

#### compareTo()

```java
int ergebnis = string1.compareTo(string2);
// <0: string1 < string2, 0: gleich, >0: string1 > string2
```

#### compareToIgnoreCase()

```java
int ergebnis = string1.compareToIgnoreCase(string2);
```

## Casting (Typumwandlung)

#### Primitive Casting (Widening - automatisch)

```java
int i = 10;
double d = i;  // Automatisch
```

#### Primitive Casting (Narrowing - manuell)

```java
double d = 10.5;
int i = (int) d;  // Explizit
```

#### Object Casting (Upcasting - automatisch)

```java
Hund hund = new Hund();
Tier tier = hund;  // Automatisch
```

#### Object Casting (Downcasting - manuell)

```java
Tier tier = new Hund();
Hund hund = (Hund) tier;  // Explizit
```

#### instanceof prüfen

```java
if (objekt instanceof TypName) {
    TypName variable = (TypName) objekt;
}
```

## Wrapper-Klassen Methoden

#### parseInt / parseDouble

```java
int zahl = Integer.parseInt("123");
double dezimal = Double.parseDouble("3.14");
```

#### valueOf()

```java
Integer i = Integer.valueOf("123");
Double d = Double.valueOf("3.14");
```

#### toString() (static)

```java
String text = Integer.toString(123);
String text = Double.toString(3.14);
```

## Math-Methoden

#### Math.abs()

```java
int absolut = Math.abs(zahl);
```

#### Math.max() / Math.min()

```java
int maximum = Math.max(a, b);
int minimum = Math.min(a, b);
```

#### Math.pow()

```java
double ergebnis = Math.pow(basis, exponent);
```

#### Math.sqrt()

```java
double wurzel = Math.sqrt(zahl);
```

#### Math.round()

```java
long gerundet = Math.round(dezimalzahl);
```

#### Math.random()

```java
double zufall = Math.random();  // 0.0 - 1.0
```

## Formatierung

#### Printf Format-Specifiers

```java
%d          // Integer
%f          // Float/Double
%s          // String
%c          // Character
%b          // Boolean
%n          // Newline
%%          // Prozentzeichen
```

#### Printf - Integer

```java
System.out.printf("%d", 42);                    // 42
System.out.printf("%5d", 42);                   // "   42" (Breite 5)
System.out.printf("%-5d", 42);                  // "42   " (linksbündig)
System.out.printf("%05d", 42);                  // "00042" (mit Nullen)
System.out.printf("%,d", 1000000);              // "1,000,000"
```

#### Printf - Double

```java
System.out.printf("%f", 3.14159);               // 3.141590
System.out.printf("%.2f", 3.14159);             // 3.14
System.out.printf("%8.2f", 3.14);               // "    3.14"
System.out.printf("%-8.2f", 3.14);              // "3.14    "
```

#### Printf - String

```java
System.out.printf("%s", "Hallo");               // Hallo
System.out.printf("%10s", "Hallo");             // "     Hallo"
System.out.printf("%-10s", "Hallo");            // "Hallo     "
```

#### Printf - Mehrere Argumente

```java
System.out.printf("%s ist %d%n", "Max", 25);    // Max ist 25
```

#### String.format()

```java
String text = String.format("%.2f", 19.99);     // "19.99"
String info = String.format("%s: %d", name, zahl);
```

#### DecimalFormat

**Import:** `import java.text.DecimalFormat;`

```java
DecimalFormat df = new DecimalFormat("pattern");
String ergebnis = df.format(zahl);
```

**Patterns:**

```java
"#.##"              // 123.46 (keine führende 0)
"0.00"              // 5.00 (mit führenden 0en)
"#,###"             // 1,000,000
"#,##0.00"          // 1,234,567.89
"0.###E0"           // 1.234E4 (wissenschaftlich)
```

**Symbole:**

- `0` = Ziffer (mit Nullen)
- `#` = Ziffer (ohne Nullen)
- `.` = Dezimalpunkt
- `,` = Tausender-Trennzeichen

## Schleifen
#### For-Loop

```java
for (int i = 0; i < n; i++) {
    // Code
}
```

#### For rückwärts

```java
for (int i = n; i > 0; i--) {
    // Code
}
```

#### For mit Schrittweite

```java
for (int i = 0; i < n; i += 2) {
    // Code
}
```

#### Enhanced For-Loop (For-Each)

```java
for (Typ element : collection) {
    // Code
}
```

#### While-Loop

```java
while (bedingung) {
    // Code
}
```

#### Do-While-Loop

```java
do {
    // Code
} while (bedingung);
```

#### Break

```java
for (int i = 0; i < n; i++) {
    if (bedingung) {
        break; // Verlässt Schleife
    }
}
```

#### Continue

```java
for (int i = 0; i < n; i++) {
    if (bedingung) {
        continue; // Überspringt Rest der Iteration
    }
}
```

#### Verschachtelte Loops

```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        // Code
    }
}
```

#### Infinite Loop

```java
while (true) {
    // Code
    if (bedingung) break;
}
```

## Collections

#### ArrayList

Dynamisches Array, schneller Zugriff, erlaubt Duplikate, geordnet

**Methoden:**

```java
add(element)           
add(index, element)    
get(index)            
set(index, element)    
remove(index)          
size()                 
isEmpty()              
contains(element)      
clear()                
indexOf(element)       
```

**Iteration:**

```java
ArrayList<String> liste = new ArrayList<>();

// For-Loop
for (int i = 0; i < liste.size(); i++) {
    System.out.println(liste.get(i));
}

// For-Each
for (String element : liste) {
    System.out.println(element);
}
```

#### LinkedList

 Doppelt verkettet, schnelles Einfügen/Löschen, langsamer Zugriff, erlaubt Duplikate

**Methoden:**

```java
add(element)           
addFirst(element)      
addLast(element)      
getFirst()             
getLast()              
removeFirst()          
removeLast()           
```

### HashSet

**Keine Duplikate**, keine Reihenfolge, schnell

**Methoden:**

```java
add(element)           
remove(element)        
contains(element)      
size()                 
isEmpty()             
clear()
```

**Iteration:**

```java
HashSet<String> set = new HashSet<>();

for (String element : set) {
    System.out.println(element);
}
```

### TreeSet

**Keine Duplikate**, **automatisch sortiert**, langsamer als HashSet

**Methoden:**

```java
add(element)           
first()               
last()                 
ceiling(element)       
floor(element)         
higher(element)        
lower(element)         
```

### Queue (mit LinkedList)

**Merkmale:** FIFO (First In First Out)

**Methoden:**

```java
add(element)           
offer(element)         
poll()                 
peek()                 
isEmpty()              
```

**Beispiel:**

```java
Queue<String> queue = new LinkedList<>();
queue.add("Erster");
queue.add("Zweiter");
String element = queue.poll();  // "Erster"
```

### Stack

**Merkmale:** LIFO (Last In First Out)

**Methoden:**

```java
push(element)         
pop()                  
peek()                 
isEmpty()              
search(element)        
```

**Beispiel:**

```java
Stack<Integer> stack = new Stack<>();
stack.push(10);
stack.push(20);
int top = stack.pop();  // 20
```

## Maps

### HashMap

Key-Value Paare, **keine Duplikat-Keys**, keine Reihenfolge, schnell

**Methoden:**

```java
put(key, value)        
get(key)               
remove(key)            
containsKey(key)       
containsValue(value)   
keySet()              
values()               
entrySet()             
size()                
isEmpty()              
clear()               
```

**Iteration:**

```java
HashMap<String, Integer> map = new HashMap<>();

// Keys durchlaufen
for (String key : map.keySet()) {
    System.out.println(key);
}

// Values durchlaufen
for (Integer value : map.values()) {
    System.out.println(value);
}

// Key-Value Paare
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}
```


### TreeMap

Key-Value Paare, **nach Keys sortiert**, langsamer als HashMap

**Methoden:**

```java
put(key, value)       
get(key)               
firstKey()             
lastKey()              
ceilingKey(key)       
floorKey(key)          
higherKey(key)      
lowerKey(key)         
```

## Scanner

**Import:** `import java.util.Scanner;`

### Scanner erstellen

```java
Scanner scanner = new Scanner(System.in);
```

### Methoden

```java
nextLine()              
next()                  
nextInt()              
nextDouble()            
nextFloat()             
nextBoolean()           
nextByte()              
nextShort()            
nextLong()              

hasNext()               
hasNextInt()            
hasNextLine()           

close()                
```

## Random

**Import:** `import java.util.Random;`

#### Random erstellen

```java
Random random = new Random();
```

#### Methoden

```java
nextInt()               
nextInt(obergrenze) // exclusive obergrenze       
nextDouble()            
nextFloat()             
nextLong()              
nextBoolean()           
nextBytes(byte[])       
nextGaussian()           
```

#### Random in einem Bereich

**Ganzzahlen**
```java
int zahl = random.nextInt(oben - unten + 1) + unten;
```

**Dezimalzahlen**
e
```java
double zahl = random.nextDouble() * (oben - unten) + unten;
```

## Exceptions
#### Checked Exceptions (müssen behandelt werden)

- `IOException` - Ein-/Ausgabefehler
- `FileNotFoundException` - Datei nicht gefunden
- `SQLException` - Datenbankfehler
- `ClassNotFoundException` - Klasse nicht gefunden
- `InterruptedException` - Thread unterbrochen
- `ParseException` - Parsing-Fehler

#### Unchecked Exceptions (RuntimeException)

- `NullPointerException` - Zugriff auf null
- `ArrayIndexOutOfBoundsException` - Array-Index außerhalb
- `ArithmeticException` - Mathematischer Fehler (z.B. Division durch 0)
- `NumberFormatException` - Falsche Zahlenkonvertierung
- `IllegalArgumentException` - Ungültiges Argument
- `ClassCastException` - Falscher Cast
- `IllegalStateException` - Ungültiger Zustand
- `IndexOutOfBoundsException` - Index außerhalb

#### Errors 

- `OutOfMemoryError` - Kein Speicher mehr
- `StackOverflowError` - Stack voll (meist durch Rekursion)
- `AssertionError` - Assertion fehlgeschlagen

## Try-Catch

#### Einfaches Try-Catch

```java
try {
    // Code der Exception werfen könnte
    int ergebnis = 10 / 0;
} catch (ArithmeticException e) {
    // Fehlerbehandlung
    System.out.println("Fehler: " + e.getMessage());
}
```

#### Mehrere Catch-Blöcke

```java
try {
    int[] array = new int[5];
    array[10] = 50;
} catch (ArrayIndexOutOfBoundsException e) {
    System.out.println("Index zu groß!");
} catch (NullPointerException e) {
    System.out.println("Objekt ist null!");
} catch (Exception e) {
    System.out.println("Allgemeiner Fehler");
}
```

#### Try-Catch-Finally

```java
try {
    // Code
} catch (Exception e) {
    // Fehlerbehandlung
} finally {
    // Wird IMMER ausgeführt (auch bei return!)
    System.out.println("Aufräumen");
}
```

#### Multi-Catch (ab Java 7)

```java
try {
    // Code
} catch (IOException | SQLException e) {
    System.out.println("IO oder SQL Fehler");
}
```


## Throws 

#### Einfaches Throws

```java
public void pruefeAlter(int alter) throws IllegalArgumentException {
    if (alter < 0) {
        throw new IllegalArgumentException("Alter kann nicht negativ sein!");
    }
    if (alter > 150) {
        throw new IllegalArgumentException("Alter unrealistisch!");
    }
}
```

#### Mehrere Exceptions

```java
public void verarbeiten() throws IOException, SQLException {
    // Beide Exceptions werden weitergegeben
}
```


>[!tip]
>Wenn eine Exception im `try` Block auftritt, werden lokale Variablen des Blocks verworfen und der Stack wird "zurückgespult" (Stack Rewind)

## Enums

```java
enum Tag {
    MONTAG, DIENSTAG, MITTWOCH, DONNERSTAG, FREITAG
}
```

**Methoden:**

```java
Tag.values()                // Alle Werte als Array
Tag.valueOf("MONTAG")       // String zu Enum
tag.name()                  // Name als String
tag.ordinal()               // Index (0, 1, 2, ...)
```

## Factory 

```java
enum FahrzeugTyp {
    AUTO, MOTORRAD, LKW
}

class FahrzeugFactory {
    public static Fahrzeug erstelleFahrzeug(FahrzeugTyp typ, List<Object> params) {
        switch (typ) {
            case AUTO:
                return new Auto(
                    (String) params.get(0),  
                    (int) params.get(1),     
                    (int) params.get(2)      
                );
            case MOTORRAD:
                return new Motorrad(
                    (String) params.get(0),
                    (int) params.get(1)     
                );
            case LKW:
                return new LKW(
                    (String) params.get(0),  
                    (int) params.get(1),     
                    (double) params.get(2)   
                );
            default:
                return null;
        }
    }
}

List<Object> autoParams = Arrays.asList("BMW", 200, 4);
Fahrzeug auto = FahrzeugFactory.erstelleFahrzeug(FahrzeugTyp.AUTO, autoParams);
```

## Polymorphie

Objekt vom Typ Subklasse kann als Typ der Superklasse behandelt werden

#### Decorators

- `@Override` überschreibt Methoden durch Polymorphie
- `@Overload` Gleicher Name aber andere Parameter

## Super

- `super()` Konstruktor der Superklasse aufrufen (erste Zeile)
- `super.methode()` Methode der Superklasse aufrufen
- `super.attribut` Attribut der Superklasse zugreifen

## Abstract

**Abstrakte Klasse:**

- Kann nicht instanziiert werden
- Kann abstrakte Methoden haben (ohne Body)
- Kann normale Methoden haben
- Kann Konstruktor haben
- Abstrakte Methoden **müssen** in Subklasse überschrieben werden
- Keyword: `abstract class`

**Abstrakte Methode:**

- Kein Methodenkörper
- Muss in nicht-abstrakter Subklasse implementiert werden
- Keyword: `public abstract void methode();`


## Interface

```java
public interface Executable {
    void execute();  
}

class App implements Executable {
    @Override
    public void execute() {
        System.out.println("Running");
    }
}
```


## Threads

#### Thread mit Runnable Interface

```java
class MeinTask implements Runnable {
    public void run() {
        System.out.println("Thread läuft");
    }
}

Runnable task = new MeinTask();
Thread thread = new Thread(task);
thread.start();
```

#### Thread durch Vererbung

```java
class MeinThread extends Thread {
    public void run() {
        System.out.println("Thread läuft");
    }
}

MeinThread thread = new MeinThread();
thread.start();
```

#### Anonyme Klasse

```java
Thread thread = new Thread(new Runnable() {
    public void run() {
        System.out.println("Thread läuft");
    }
});
thread.start();
```

#### Thread-Methoden

```java
thread.start()              // Thread starten
thread.run()                // Direkt ausführen (kein neuer Thread!)
Thread.sleep(milliseconds)  // Warten
thread.join()               // Auf Thread warten
thread.isAlive()            // Läuft noch?
thread.interrupt()          // Thread unterbrechen
thread.setName(name)        // Name setzen
thread.getName()
```


## Lambda
Kurzschreibweise für anonyme Funktionen (ab Java 8)

#### Syntax

**Ohne Parameter:**

```java
() -> System.out.println("Hallo")
() -> { return 42; }
```

**Ein Parameter:**

```java
x -> x * 2
x -> { return x * 2; }
(x) -> x * 2              // Klammern optional
```

**Mehrere Parameter:**

```java
(x, y) -> x + y
(x, y) -> { return x + y; }
```

**Mit Typ-Angabe:**

```java
(int x, int y) -> x + y
(String s) -> s.length()
```

#### Lambda mit Collections

**forEach:**

```java
List<String> liste = Arrays.asList("A", "B", "C");
liste.forEach(element -> System.out.println(element));
```

**sort:**

```java
List<Integer> zahlen = Arrays.asList(3, 1, 4, 1, 5);
zahlen.sort((a, b) -> a - b);  // Aufsteigend
zahlen.sort((a, b) -> b - a);  // Absteigend
```

**filter:**

```java
List<Integer> zahlen = Arrays.asList(1, 2, 3, 4, 5);
zahlen.stream()
      .filter(x -> x > 2)
      .forEach(x -> System.out.println(x));
```

**map:**

```java
List<String> namen = Arrays.asList("anna", "bob", "carl");
namen.stream()
     .map(s -> s.toUpperCase())
     .forEach(System.out::println);
```

#### Functional Interfaces

Lambda funktioniert nur mit **Functional Interfaces** (Interface mit **einer** abstrakten Methode)


## Wichtige Imports

#### Scanner & Input

```java
import java.util.Scanner;
```

#### Collections

```java
import java.util.ArrayList;
import java.util.LinkedList;
import java.util.HashSet;
import java.util.TreeSet;
import java.util.HashMap;
import java.util.TreeMap;
import java.util.Queue;
import java.util.Stack;
import java.util.Map;              // Für Map.Entry
import java.util.List;
import java.util.Set;
```

#### Arrays

```java
import java.util.Arrays;
```

#### Random

```java
import java.util.Random;
```

#### File I/O

```java
import java.io.File;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.io.FileNotFoundException;
```

#### Formatierung

```java
import java.text.DecimalFormat;
import java.text.NumberFormat;
```

#### Threads

```java
import java.lang.Thread;
import java.lang.Runnable;
```

#### Collections Utilities

```java
import java.util.Collections;      // Für sort(), reverse(), etc.
import java.util.Comparator;
import java.util.Iterator;
```

#### Math 

```java
// Math ist in java.lang und wird automatisch importiert
Math.random();
Math.pow();
```

#### Date & Time

```java
import java.util.Date;
import java.time.LocalDate;
import java.time.LocalTime;
import java.time.LocalDateTime;
```

#### Alle aus einem Package

```java
import java.util.*;                // Alle util-Klassen
import java.io.*;                  // Alle io-Klassen
```
## Syntax einer Java-Methode

Die Methodensignatur besteht aus dem Methodennamen und der Parameterliste.

```java
modifizierer rückgabewert nameDerMethode (Parameterliste) {
   // Methodenkörper
}
```

- **modifizierer:** Bestimmt den Zugriffstyp der Methode (z. B. `public`, `private`) und ist optional.
- **rückgabewert:** Die Methode kann einen Wert zurückgeben. Wird kein Wert zurückgegeben, verwendet man `void`.
- **nameDerMethode:**  Der Methodenname. 
- **Parameterliste:** Eine Liste von Parametern (Typ, Reihenfolge und Anzahl der Parameter). Diese ist optional; eine Methode kann keine oder mehrere Parameter haben.
- **Methodenkörper:** Der Methodenkörper definiert, was die Methode mit den Anweisungen macht.

## Aufruf einer Java-Methode  
- Um eine Methode zu verwenden, muss sie aufgerufen werden. 
- Gibt diie Methode keinen Wert zurück (kein Rückgabewert) ist sie eine Prozedure.  
- Prozeduren sind Methoden die `void` zurückgeben, werden als Aufruf einer Anweisung betrachtet. 
- Eine Methode, die einen Wert zurückgibt, kann wie folgt verwendet werden:

```java
int ergebnis = sum(6, 9);
```

## Übergabe von Parametern Java-Methoden (Call by Value)

- Bei der Arbeit mit dem Aufrufprozess werden Argumente übergeben werden. 
- Parameter können entweder durch Wert oder durch Referenz übergeben werden.
- Parameterübergabe durch Wert bedeutet, dass eine Methode mit einem Parameter aufgerufen wird. Jedoch ändert die Methode den tatsächlichen Wert der Variable nicht.

## Gültigkeitsbereich (Scope)   
Der **Gültigkeitsbereich** bezeichnet den Bereich im Code, in dem eine Variable deklariert und verwendet werden kann. Variablen sind in Java nur zwischen den geschweiften Klammern (`{}`) verfügbar, in denen sie deklariert wurden.

**Methoden**: 
Variablen, die innerhalb einer Methode deklariert werden, sind nur in dieser Methode sichtbar. Sobald die Methode endet, sind diese Variablen nicht mehr zugreifbar.   
```java   
public void methode() {       
	int x = 10; // x ist nur innerhalb dieser Methode sichtbar   
}
```

**if-Block**: 
Variablen, die in einem `if`-Block deklariert werden, sind nur innerhalb dieses Blocks sichtbar.
```java
if (true) {
    int y = 5; // y ist nur innerhalb dieses if-Blocks sichtbar
}
// y ist hier nicht zugreifbar
```

**else-Block**: 
Wie beim `if`-Block gilt auch für den `else`-Block, dass Variablen nur innerhalb des Blocks sichtbar sind.

```java
else {     
	int z = 7; // z ist nur innerhalb des else-Blocks sichtbar  
} 
// z ist hier nicht zugreifbar`
```

**for-Schleifen**: 
Variablen, die in einer `for`-Schleife deklariert werden, sind nur innerhalb der Schleife gültig. Sie können nicht außerhalb der Schleife verwendet werden.

```java
for (int i = 0; i < 10; i++) {     
	// i ist nur innerhalb der for-Schleife sichtbar 
} 
// i ist hier nicht zugreifbar`
```
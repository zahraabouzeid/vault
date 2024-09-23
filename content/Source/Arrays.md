## Was sind Arrays?
Ein Array in Java ist eine Datenstruktur, die eine festgelegte Anzahl von Elementen desselben Typs speichert und es ermöglicht, diese Elemente wie eine Sammlung von Variablen über Indizes anzusprechen.

## Deklaration
```java
dataType[] arrName; 
dataTye arrName[];
```
Der Unterschied wird erkannt, wenn mehrere Variablen auf einer zeile deklariert werden:
```java
int [ ] arr1, arr2, arr3;
int arr1[ ], zahl, arr2[ ];
```
## Speicherplatz anlegen
```java
arrName = new double[4];
```

## Zugriff auf einen Wert
Ein Array ist nullindiziert, d.h. fängt ab 0 an.
```java
System.out.println(arrName[2]);
```

## Array mit Werte Initialisieren
```java
int arr[] = {2, 1, 5, 7, 8}
```
## Alle Elemente eines Arrays anzeigen
**for Schleife**
```java
for (int i = 1; i < arrName.length; i++ ) {
	System.out.println(arrName[i]);
}
```

**for Schleife**
```java
for (double element: arrName) { 
	System.out.println(element); 
}
```

>[!warning]
>Bei Ungültige Zugriffe, wird eine **IndexOutOfBoundsException** ausgelöst und bricht das Programm ab
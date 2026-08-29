## Direkte rekursive Funktion
Eine Funktion ist direkt rekursiv, wenn sie sich selbst, unmittelbar in ihrem eigenen Algorithmus, aufruft.
## Indirekte rekursive Funktion
Eine Funktion ist indirekt rekursiv, wenn sie sich selbst, über eine andere Funktion/en, aufruft.
## Speicher und Lokale Variablen
- Wird eine Funktion aufgerufen, definiert sie in den meisten Fällen lokale Variablen.
- Diese "Lokalen Variablen" stehen nur am Ort ihrer Entstehung oder Definition zur Verfügung. Andere Funktionen "kennen" diese Objekte nicht.
- Bei der Rekursion werden viele gleichnamige Variablen im Speicher gestapelt und unterschieden.

## Speicherbelegung und Ablauf
- Ohne **Abbruchbedingung** wird eine Endlos-Rekursion erzeugt. Im Gegensatz zur Endlos-Schleife wird der Speicher vollgeschrieben und das Programm stürzt ab.
- ist die Abbruchbedingung erfüllt, werden die Rückgabewerte, wie bei einer Transportkette, an alle aufgerufenen Funktionen zurückgeleitet, bis der Einstiegs-Funktionsaufruf erreicht ist.
- alle Funktionen sterben nach dem Prinzip LIFO.  

## Quersumme
**Ohne Rekursion**
```java
public static int quersumme(int num) {  
    int result = 0;  
  
    while (num != 0) {  
        result += num % 10;  
        num /= 10;  
    }  
    return result;
}
```

**Mit Rekursion**
```java
public static int quersumme(int num) {
	int result = 0;

    if (num < 10) {
	    result = num;
    } else {
	    result = (num % 10) + quersumme(num / 10);
    }
    
    return result;
}
```
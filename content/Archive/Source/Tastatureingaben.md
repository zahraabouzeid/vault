```java
import java.util.Scanner;

public class EinfachsteEingabe
{
	public static void main(String[] args)
	{
		String strEingabe;
		Scanner eingabeTool = new Scanner(System.in);
		System.out.print( "Name eingeben: ");
		strEingabe = eingabeTool.next();
		System.out.println(strEingabe.charAt(0));
		eingabeTool.close();
	}
}
```

- Mit `Scanner eingabeTool = new Scanner(System.in)` wird eine Variable vom Typ der Klasse Scanner deklariert.
- `.next()` ist eine Methode von der mit dem `new` Befehl erstellten Scanner Objekt, die einen Text einliest.
- `.nextDouble()` ist eine Methode die eine Gleitkommazahl einliest.
-  `.nextInt()` ist eine Methode die eine Ganzzahl einliest.
- `.next()` ist eine Methode von der mit dem `new` Befehl erstellten Scanner Objekt, die einen Text einliest.
- Im Kern des Scanners liegt `System.in`, was die Tastatur repräsentiert.
- `charAt(0)` gibt das erste Zeichen des Strings.


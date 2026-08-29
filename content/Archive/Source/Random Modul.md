## Verwendung der Klasse `Random`

```java
import java.utils.Random
```

In Java kann die Klasse `Random` verwendet werden, um Zufallszahlen zu erzeugen. Diese Klasse bietet verschiedene Methoden, um unterschiedliche Arten von Zufallswerten zu generieren.
## Methoden der Klasse `Random`
- `nextInt()`: Gibt eine zufällige Ganzzahl (positiv oder negativ) zurück.
- `nextInt(obergrenze)`: Gibt eine Ganzzahl zwischen `0` und `obergrenze` (exklusiv) zurück.
- `nextFloat()`: Gibt eine Dezimalzahl zwischen `0` und `1` zurück.
- `nextDouble()`: Gibt eine Dezimalzahl zwischen `0` und `1` zurück.
- `nextBoolean()`: Gibt einen zufälligen Wahrheitswert (`true` oder `false`) zurück.
## Zufallszahlen in einem Bereich

**Ganzzahlen**
```java
int zufallsGanzzahl = zahlenMaschine.nextInt(oben - unten + 1) + unten;
```

**Dezimalzahlen**

```java
double zufallsDezimalzahl = zahlenMaschine.nextDouble() * (oben - unten) + unten;
```
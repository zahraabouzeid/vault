
## Warum Generics?
- **Ziel**: Typsicherheit bei der Arbeit mit Collections.
- **Ohne Generics**: Alle Objekte als `Object`, Gefahr falscher Typen.
- **Mit Generics**: z. B. `ArrayList<Ball>` – nur passende Objekte erlaubt, sicherer Code.
## Java Collection Framework
- **Zentrale Interfaces**: `Collection`, `List`, `Set`, `SortedSet`, `Queue`, `Deque`.
- **Beispiele**: `ArrayList`, `HashSet`, `TreeSet`, `LinkedList`, `Stack`.

**Methoden von dem Interface Iterable (für alle collections):**
- `boolean add(E)`
- `boolean remove(Object)`
- `boolean contains(Object)`
- `int size()`
- `isEmpty()`
- `iterator()`
- `stream()`
## Der Iterator
- Iteration durch Collections, unabhängig vom Typ.
- Methoden: `hasNext()`, `next()`.
- Alternativ: **for-each Schleife**.

```java
Collection<String> stringList;
stringList = new ArrayList<>();
stringList.add("Hannah");


Iterator<String> it = stringList.iterator();
while (it.hasNext())
{
    String name = it.next();
    System.out.println("Name: " + name);
}
```

## Listen
Geordnete Elemente, Duplikate erlaubt, mit Indexzugriff.

**Methoden (Auswahl)**:
- `get(int)`
- `set(int, E)`
- `indexOf(Object)`
- `remove(int)`
- `remove(Object)`
- `subList(from, exclusiveto)`
#### Beispiel: `ArrayList`

```java
List<Figur> figuren = new ArrayList<>();

figuren.add(new Kreis(3));
figuren.set(0, new Rechteck(7,9));
figuren.remove(0);
```

## Sets
- **Keine Duplikate, ungeordnet oder sortiert (SortedSet).**
- `TreeSet`: automatisch sortiert (z. B. Lottozahlen).
#### Beispiel: `TreeSet`

```java
TreeSet<Integer> zahlen = new TreeSet<>();
while (zahlen.size() < 6) ...
```

## Stack und Queue
- **Stack**: FILO (Last In, First Out)
- **Queue**: FIFO (First In, First Out)
- **priority_queue**: höhere Priorität zuerst
- Heute bevorzugt: `Deque` für beides

## Maps
- **Map ≠ Collection**, kein Iterable
- Ordnet **Werte eindeutigen Schlüsseln** zu.
- In `SortedMap` sind die Objekte in aufsteigender Reihenfolge der Schlüssel sortiert.

**Methoden**:
- `get(Object)`
- `put(K,V)`
- `remove(Object)`
- `containsKey()`
- `containsValue()`
- `keySet()`
- `values()`
#### Beispiel `HashMap`:
```java
HashMap<String, String> englDeut = new HashMap<>();
englDeut.put("hello", "Hallo");
```
#### Beispiel `TreeMap`:
```java
Map<String, Set<String>> woerterbuch = new TreeMap<>();
woerterbuch.put("A", new TreeSet<>(...));
```
## Wann benutzt man was?

|Kriterium|Empfehlung|
|---|---|
|Reihenfolge wichtig|`List` (z. B. `ArrayList`, `LinkedList`)|
|Eindeutigkeit wichtig|`Set` (z. B. `HashSet`, `TreeSet`)|
|Schlüssel/Wert|`Map` (z. B. `HashMap`, `TreeMap`)|
|Sortierung|`TreeSet`, `TreeMap`|
|Schneller Zugriff|`HashSet`, `HashMap` (Hashing)|

## Hashing
- Methode zur schnellen Indexierung und Zugriff.
- In `HashMap`: Schlüssel wird gehasht → schneller Zugriff auf Werte.

## Algorithmen aus `java.util.Collections`
- **Allgemeine Algorithmen**: `min`, `max`, `frequency`    
- **Für Listen (mit Indexzugriff)**: `sort`, `shuffle`, `swap`, `copy`, `reverse`

#### Beispiel `Collections.sort()`:
```java
public static <T extends Comparable> void sort(List<T> list);
```
Klasse muss `Comparable<T>` implementieren (`compareTo`-Methode).
**Beispiel:**
```java
class Mitarbeiter implements Comparable<Mitarbeiter> {
    private int id;
    private String name;

    @Override
    public int compareTo(Mitarbeiter m) {
        
    }

}
```

## Kontrollfragen
**1. Warum sind Generics gut?**  
→ Sie sorgen für **Typsicherheit**, vermeiden Casts & Laufzeitfehler.

**2. Wann verwendet man `List`?**  
→ Wenn **Reihenfolge wichtig ist** oder **Duplikate erlaubt** sind.

**3. Wann verwendet man `Set`?**  
→ Wenn **keine Duplikate** erlaubt sein sollen.

**4. Wann verwendet man `Map`?**  
→ Wenn man **Schlüssel-Wert-Paare** speichern will.

**5. Welcher Container für **schnellen Zugriff auf Positionen**?**  
→ `ArrayList`.

**6. Welcher Container für **häufiges Einfügen/Löschen in der Mitte**?**  
→ `LinkedList`.

**7. Welcher Container für **Sortierung + Eindeutigkeit**?**  
→ `TreeSet`.

**8. Welcher Container für **Eindeutigkeit + schnellen Zugriff**?**  
→ `HashSet`.
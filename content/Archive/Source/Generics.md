## Warum funktioniert Polymorphie nicht bei Generics?
- Java ist streng typisiert: Ein `List<Mitarbeiter>` ist nicht kompatibel mit `List<BueroArbeiter>`, obwohl `BueroArbeiter` eine Unterklasse ist.
- Typsicherheit: Java verhindert fehlerhafte Objekteinspeisung in Collections (z.B. `SchichtArbeiter` in `List<BueroArbeiter>`).

## Generics vs. Arrays
- Ohne Generics: alles wird als `Object` behandelt → unsicher.
- Mit Generics: z.B. `ArrayList<BueroArbeiter>` ist typsicher:
    - Nur `BueroArbeiter`-Objekte erlaubt.
    - Kein unerwarteter `ClassCastException`.
## Wildcards

```java
public static void ausgabe(List<? extends Mitarbeiter> mitList)
```

- `? extends Mitarbeiter` erlaubt: `List<BueroArbeiter>`, `List<SchichtArbeiter>` usw.
- Einschränkung: nur lesend verwendbar, keine Objekte einfügen.
## Typvariablen

```java
public static <T extends Mitarbeiter> void ausgabe(List<T> mitList)
```
- Typvariable `T` bietet
    - Bessere Typsichtbarkeit innerhalb der Methode.
    - Vorteilhaft bei komplexeren Operationen.
## Schreiben mit `super`

```java
public static void hinein(List<? super Mitarbeiter> list, Mitarbeiter m)
```

- `? super Mitarbeiter`: akzeptiert Listen von `Mitarbeiter`, `Object`, usw.
- Erlaubt Einfügen, aber nicht unbedingt typklar beim Lesen.

## LESS-Prinzip

`LE`sen → `extends` (Upper Bound) 
`SS`chreiben → `super` (Lower Bound)

| Aktion    | Syntax                  | Zweck                         |
| --------- | ----------------------- | ----------------------------- |
| Lesen     | `? extends Mitarbeiter` | Zugriff auf Methoden des Typs |
| Schreiben | `? super Mitarbeiter`   | Einfügen, Konsistenz wahren   |
**Bei Collections:**
1.benötigt die Methode compareTo() à Upper bound Comparable.
2.Verändert die Reihefolge (Schreibzugriff) à Lower Bound T

## Wildcard vs. Typvariable
**Wildcard:**
- Einfach, wenn man nur lesen will. 
- Keine Rückgabe mit Typinformation möglich.
```java
public static void ausgabe( List < ? extends Mitarbeiter> mitList){
    for( Mitarbeiter m: mitList ) {
        System.out.println( m.toString() );
    }
}
```

**Typvariable:**
- Rückgabewerte, komplexere Methoden.
- Bietet Typinformation innerhalb der Methode.
```java
public static <T extends Mitarbeiter> void ausgabe( List <T> mitList){
    for(T m: mitList ) {
        System.out.println( m.toString() );
    }
}
```

**Verwendung als Rückgabetyp:**
```java
static <T> T random(T m, T n) {
    return Math.random() > 0.5 ? m : n;
}
```

Mit Wildcards: nicht möglich, da Rückgabetyp undefiniert.

## Generics in Klassenhierarchien

Beispiel mit `ClassA<T extends Part>`, `SubClassA<T extends Part>` etc.

```java
public class SubSubClassA extends SubClassA<SubPart> {
    public SubPart operateA(SubPart part);
}
```

-Vererbung mit generischen Typen erlaubt Wiederverwendbarkeit + Typsicherheit.
    

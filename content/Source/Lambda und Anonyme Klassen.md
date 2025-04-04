
## inner classes
- Eine **innere Klasse** (inner class) wird **innerhalb einer anderen Klasse** definiert.
- Sie hat **Zugriff auf alle Member der äußeren Klasse**, auch auf **private**.
- **Keine eigenen `static`-Elemente erlaubt.**
- Sie **braucht eine Instanz** der äußeren Klasse.
- Kann auch `private` sein.
- Dient zur **logischen Gruppierung**, wenn die Klasse **nur in Zusammenhang mit der äußeren Klasse** gebraucht wird.

**Arten innerer Klassen:**
- **static nested class** (KEINE echte innere Klasse!)
- **inner class** (non-static)
- **method-local inner class**
- **anonymous inner class**

## GUI & Listener

```java
button1.addActionListener(new ButtonListener1());
```

- Die Listener-Klasse wird **innerhalb der äußeren Klasse** definiert.
- Wenn man sie **nur einmal** braucht: **Overkill**.
- Alternativen: **Anonyme Klasse** oder **Lambda Expression**.
## Anonyme Klassen
- Wird **direkt beim Erzeugen eines Objekts** erstellt.  
- Kein Name, kein eigenes File, keine separate Deklaration.

```java
button1.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent e) {
        // Reaktion
    }
});
```

### Merkmale:
- **Eigener Scope**
- Zugriff auf:
    - Eigenschaften & Methoden der **umgebenden Klasse**
        - Eindeutig: `name`
        - Nicht eindeutig: `OuterClass.this.element`
    - **Lokale Variablen** der Methode **nur wenn `final` oder "effectively final"**
- Können **eigene Methoden & Eigenschaften** haben (anders als Lambdas!)
- Stichwort: **Shadowing** = Variablen gleichen Namens überdecken sich

## Scope
- **Gültigkeitsbereich** von Variablen oder Methoden.  
- In einer inneren Klasse kannst du auf `attributeOuter` zugreifen, aber musst ggf. `OuterClass.this.attributeOuter` schreiben, um Verwechslungen zu vermeiden.
## Lambdas

**Ersetzt anonyme Klassen**, wenn man ein **funktionales Interface** implementiert = **nur eine einzige abstrakte Methode**

```java
(event) -> { /* Aktion */ }
```

### Aufbau einer Lambda Expression:

- **Parameterliste**: Typ kann weggelassen werden, Name reicht
- **Pfeil `->`**
- **Methodenkörper**
    - Bei EINEM Ausdruck: **keine Klammern nötig**
    - Mehrere Anweisungen: **mit `{}` + `return` wenn nötig**

##### Beispiel:
```java
event -> ((JTextField) event.getSource()).setText("touched by lambda");
```

### Lambda vs. Anonyme Klasse:

| Merkmal                       | Anonyme Klasse | Lambda                      |
| ----------------------------- | -------------- | --------------------------- |
| Eigene Methoden               | möglich        | nicht erlaubt               |
| Eigene Eigenschaften          | möglich        | nicht erlaubt               |
| Neuer Scope                   | ja             | nein                        |
| Funktionale Interfaces nötig? | nein           | ja (z. B. `ActionListener`) |

## Wann benutzt man was?
- **Innere Klassen** → Wenn man eine Implementierung **mehrmals** braucht
- **Anonyme Klassen** → Wenn man eine Implementierung **einmal braucht**, aber mehrere Methoden
- **Lambda Expressions** → Wenn man eine Implementierung **einmal braucht** für ein **funktionales Interface**

## Vokabeln

|Begriff|Erklärung|
|---|---|
|**inner class**|Klasse innerhalb einer anderen Klasse|
|**anonymous class**|Klasse ohne Namen, einmalig verwendet|
|**lambda expression**|Kurzschreibweise für funktionale Interfaces|
|**functional interface**|Interface mit nur einer abstrakten Methode|
|**effectively final**|Variable wird nach Initialisierung nicht mehr verändert|
|**scope**|Sichtbarkeit/Gültigkeit von Variablen|
|**shadowing**|Verdeckung durch gleichnamige Variable|

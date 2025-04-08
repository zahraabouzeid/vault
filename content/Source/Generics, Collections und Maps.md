Hier ist die dritte große Zusammenfassung – jetzt zum Herzen der Klausur: **Generics, Collections und Maps**. 🎯

---

## 🧬 **Generics & Collections in Java**

---

### 🔍 **Warum Generics?**

- Java ist **stark typisiert**: jede Variable hat einen klaren Typ.
    
- Generics machen **Sammlungen typsicher**.
    
- Ohne Generics: Man arbeitet mit `Object` → **Casting notwendig** → **Fehleranfällig!**
    
- Mit Generics: **Nur Objekte vom definierten Typ** erlaubt → **kein Cast, keine Verwechslung**
    

---

### ❌ **Ohne Generics – veraltet & gefährlich**

```java
ArrayList meineListe = new ArrayList();
meineListe.add(new Ball());
meineListe.add(new Kuh()); // wird kompiliert!
```

### ✅ **Mit Generics – sicher & elegant**

```java
ArrayList<Ball> meineListe = new ArrayList<>();
meineListe.add(new Ball()); // okay
meineListe.add(new Kuh());  // Compilerfehler! 🎉
```

---

## 📦 **Java Collections Framework – Überblick**

```
               Collection (Interface)
                /       |       \
          List        Set       Queue
          ↓            ↓           ↓
      ArrayList     HashSet     LinkedList
                     TreeSet     PriorityQueue
```

|Interface|Eigenschaften|Klassen|
|---|---|---|
|`List`|geordnet, indexbasiert, duplikate ok|`ArrayList`, `LinkedList`|
|`Set`|keine Duplikate, ungeordnet oder sortiert|`HashSet`, `TreeSet`|
|`Map`|Schlüssel-Wert-Paare|`HashMap`, `TreeMap`|

---

## 🔁 **Iteratoren – die einheitliche Schleifenlösung**

```java
Collection<String> namen = new ArrayList<>();
namen.add("Hannah");
namen.add("Sven");

Iterator<String> it = namen.iterator();
while (it.hasNext()) {
    String name = it.next();
    System.out.println("Name: " + name);
}
```

➡️ oder einfacher mit **For-Each**:

```java
for (String name : namen) {
    System.out.println("Name: " + name);
}
```

---

## 🧠 **Was ist `E`, `T`, `K`, `V`?**

|Symbol|Bedeutung|
|---|---|
|`E`|Elementtyp|
|`T`|Type|
|`K`|Key|
|`V`|Value|

```java
ArrayList<E>       // Liste von Elementen
HashMap<K, V>      // Schlüssel-Wert-Paare
```

---

## 🧪 **Typische Klausuraufgaben**

- Unterschied `ArrayList`, `HashSet`, `TreeSet` erklären
    
- Methoden wie `add()`, `remove()`, `contains()` anwenden
    
- Iterator oder For-Each einsetzen
    
- eigene generische Klasse schreiben (`class Box<T> { ... }`)
    
- UML-Diagramm mit `<T>` verstehen/ergänzen
    

---

Als Nächstes: **T DS0 Dynamische Arrays** – los geht’s mit den Datenstrukturen! 🔥📚
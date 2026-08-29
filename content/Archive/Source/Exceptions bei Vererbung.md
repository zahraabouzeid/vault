## Klassifizierung
- **Throwable:** Oberklasse aller Fehler und Ausnahmen.
- **Error:** Schwere Fehler, die die JVM betreffen.
- **Exception:** Behandlungsfähige Fehler.
- **Checked Exceptions:** Müssen behandelt oder deklariert werden.
- **Unchecked Exceptions (RuntimeException):** Vom Compiler nicht überprüft.

## Eigene Exceptions
Eigene Ausnahmen können durch Vererbung von `Exception` oder `RuntimeException` erstellt werden.

```java
class CustomCheckedException extends Exception {
    public CustomCheckedException(String message) {
        super(message);
    }
}

class CustomUncheckedException extends RuntimeException {
    public CustomUncheckedException(String message) {
        super(message);
    }
}
```


## Regeln bei Redefinition von Exceptions
#### Spezialisieren
Eine Methode in einer abgeleiteten Klasse darf spezifischere Exceptions werfen, solange diese von den Exceptions der Basisklasse erben.
```java
class Basis {
    // Basismethode wirft allgemeine Exception
    public void riskanteMethode() throws Exception {
        throw new Exception("Allgemeiner Fehler in Basis");
    }
}

class Abgeleitet extends Basis {
    @Override
    public void riskanteMethode() throws CustomCheckedException {
        // Spezialisierte Exception werfen
        throw new CustomCheckedException("Spezifischer Fehler in Abgeleitet");
    }
}
```
Die Methode `riskanteMethode` in der abgeleiteten Klasse wirft `CustomCheckedException`, die von `Exception` erbt.

#### Ergänzen
Neue Exceptionstypen dürfen nicht hinzugefügt werden, da dies die Signatur der Methode verändert und gegen das Prinzip der Kompatibilität verstößt.

**Verboten:**
```java
class Basis {
    public void riskanteMethode() throws Exception {
        throw new Exception("Allgemeiner Fehler in Basis");
    }
}

class Abgeleitet extends Basis {
    @Override
    public void riskanteMethode() throws Exception, IllegalArgumentException { // Ergänzung verboten
        throw new IllegalArgumentException("Ungültiges Argument in Abgeleitet");
    }
}
```
Das Hinzufügen einer neuen Exception (`IllegalArgumentException`) ist nicht erlaubt, da dies die Kompatibilität mit der Basisklasse bricht.

#### Weglassen
Eine Methode in der abgeleiteten Klasse kann entscheiden, keine Exception mehr zu werfen, auch wenn die Methode in der Basisklasse eine Exception deklariert.

```java
class Basis {
    public void riskanteMethode() throws Exception {
        throw new Exception("Allgemeiner Fehler in Basis");
    }
}

class Abgeleitet extends Basis {
    @Override
    public void riskanteMethode() {
        // Keine Exception mehr
        System.out.println("Kein Fehler in der abgeleiteten Methode");
    }
}
```

Die Methode `riskanteMethode` in der abgeleiteten Klasse wirft keine Exception mehr, was erlaubt ist.
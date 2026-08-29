# Fehlerhandling
## Ausnahmen auslösen
- Ausnahmen auslösen statt Fehlerstatus macht den Code sauberer.
- Mit einer `try-catch-finally` den Code zuerst umschließen (damit anfangen).
- Ausnahmen sollen genügend Kontext liefern, um die Quelle und den Ort eines Fehlers zu bestimmen.
- Ausnahmen müssen richtig in Klassen nach ihrem Typ klassifiziert werden .
- Robusten sauberen Code entsteht, wenn wir das Fehler-Handling als separaten Concern betrachten, unabhängig von unserer Hauptlogik.
## Checked Exceptions
- werden mit `throw` deklariert.
- werden während des Compile-time überprüft.
- ein Beispiel von einem unchecked Exception ist ArithmeticException, das ausgelöst wird, wenn ein Zahl durch  0 geteilt wird.
- Checked Exceptions verstoßen gegen das [Open-Closed-Prinzip](https://de.wikipedia.org/wiki/Open-Closed-Prinzip), denn ein eine Änderung auf einer niedrigen Ebene der Software Signaturänderungen auf vielen höheren Ebenen erforderlich macht.
- Checked Exceptions können manchmal nützlich sein (kritische Library). Ansonsten überwiegen die Kosten der Abhängigkeit die Vorteile.

## Sonderfälle behandeln
- Klassen oder Objekte werden konfiguriert so, dass es einen Sonderfall für Sie handhabt,
- Der Client Code muss nicht it dem Ausnahmeverhalten befassen.
- Die Verhaltensweise wird in einem Sonderfall-Objekt eingekapselt.

## Keine Null zurück/übergeben
- Die Gefahr von `NullPointerExceptions` minimieren mithilfe von Special Case Objects (was zurückgeben wenn der Objekt null ist).
- Mit einer Ausnahmen sicherstellen dass der übergebene Parameter ungleich `null` ist, oder es mit einem `assert` dokumentieren.
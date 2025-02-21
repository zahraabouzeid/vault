### Refactoring von JUnit
- Pfadfinder-Regel angewendet, bei dem wir Code besser hinterlassen, als wir ihn vorgefunden haben.
- Umbenennungen bzw.  Redundante `fs` entfernt.
- `compact` in `formatCompactedComparison()` umbenannt, da die Methode auch Strings formatiert.
- Kapselung von `shouldNotCompact()` (S. 308) eingeführt.
- Lokale Variablen mit gleichen Namen wie Member-Variablen umbenannt (z. B. `expected` und `actual`).
- Negativ formulierte Bedingungen umgedreht, `canBeCompacted()` statt `shouldNotCompact()`.
- Body der if-Anweisung (S. 309) in eine separate Methode ausgelagert, die für die Komprimierung verantwortlich ist.
- `prefixIndex` an `findCommonPrefix()` übergeben, danach weiter umgebaut (S. 311).
- Die `+1`s in `computeCommonSuffix` bereinigt.
- `if`-Anweisung überprüfte `suffixLength`, die 0 sein konnte, aber nie 0 war wegen der `+1` Berechnung.
- Überflüssige `if`-Anweisungen entfernt.
### Fazit
- Manche Entscheidungen wurden rückgängig gemacht.
- Ein Refactoring führt oft zu weiteren Refactorings.
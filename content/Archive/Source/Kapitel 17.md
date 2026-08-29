# Smells und Heuristiken

## Kommentare
- Ungeeignete Informationen gehören in Versionierungstools, nicht in Code.
- Keine Überholte Kommentare schreiben, die schnell altern können.
- Redundante Kommentare vermeiden (z.B. etwas das sich hinreichend selbst beschreibt).
- Wenn unbedingt nötig, nur gute Kommentare schreiben.
- Auskommentierter Code direkt löschen.
## Umgebung
- Ein Build = ein Befehl, keine kryptische Scripts.
- Tests in einem Schritt startbar.
## Funktionen
- max. 3 Argumente, besser weniger.
- Output-Argumente vermeiden.
- Flag-Argumente  sind Hinweis auf mehrere Aufgaben in einer Funktion.
- Funktionen löschen, die nie aufgerufen werden.
- DRY-Prinzip
- Eine Aufgabe pro Funktion.
## Allgemein
**G1: Mehrere Sprachen in einer Quelldatei**  
Anzahl zusätzlicher Sprachen in unseren Quelldateien minimieren.

**G2: Offensichtliches Verhalten ist nicht implementiert**  
Least-Surprise-Prinzip: der Code soll sich so verhalten, wie man erwartet.

**G3: Falsches Verhalten an den Grenzen**  
Sonderfälle sorgfältig berücksichtigen.

**G4: Übergangene Sicherungen**  
Sicherheitsmechanismen wie Versionskontrolle oder Validierung dürfen nicht vergessen werden.

**G5: Duplizierung**  
Doppelt geschriebenen Code durch sinnvolle Abstraktion ersetzen.

**G6: Auf der falschen Abstraktionsebene codieren**  
Funktionen und Konzepte gehören auf die richtige Abstraktionsebene programmieren.

**G7: Basisklasse hängt von abgeleiteten Klassen ab**  
Eine Basisklasse darf nichts über ihre abgeleiteten Klassen wissen.

**G8: Zu viele Informationen**  
Klassen und Interfaces so klein wie möglich halten.

**G9: Toter Code**  
Unnötiger Code löschen.

**G10: Vertikale Trennung**  
Variablen und Funktionen nahe ihrer ersten Verwendung definieren.

**G11: Inkonsistenzen**  
Ähnliche Aufgaben sollen im Code auf ähnliche Weise lösen und nennen.

**G12: Müll**  
Ungenutzte Konstruktoren, Variablen, Kommentare und toten Code entfernen.

**G13: Künstliche Kopplung**  
Was logisch nicht zusammengehört trennen.

**G14: Funktionsneid**  
Eine Klasse soll nicht auf interne Daten einer anderen zugreifen wollen.

**G15: Selektor-Argumente**  
Booleschen oder enums Argumente lieber in mehrere Funktionen benuzten.

**G16: Verdeckte Absicht**  
Ungarische Notation und magische Zahlen vermeiden.

**G17: Falsche Zuständigkeit**  
Platzieren Sie Code dort, wo man ihn logisch erwarten würde.

**G18: Fälschlich als statisch deklarierte Methoden**  
Nicht jede Methode sollte statisch sein - Polymorphie kann manchmal besser sein.

**G19: Aussagekräftige Variablen verwenden**  

**G20: Funktionsname sollte die Aktion ausdrücken**  

**G21: Den Algorithmus verstehen**  
Algorithmus verstehen und lesen auch wenn er bereits läuft.

**G22: Logische Abhängigkeiten in physische umwandeln**  

**G23: Polymorphismus statt If/Else oder Switch/Case verwenden**  

**G24: Konventionen beachten**  
An Teamkonventionen sich halten.

**G25: Magische Zahlen durch benannte Konstanten ersetzen**  

**G26: Präzise sein**  

**G27: Struktur ist wichtiger als Konvention**  
Gute Struktur ist entscheidender als Einhaltung jeder kleinen Namensregel.

**G28: Bedingungen einkapseln**  

**G29: Negative Bedingungen vermeiden**  

**G30: Eine Aufgabe pro Funktion**

**G31: Verborgene zeitliche Kopplungen**  
Aufrufreihenfolge von Funktionen explizit und sichtbar machen.

**G32: Keine Willkür**  
Alles sollte begründet sein.

**G33: Grenzbedingungen einkapseln**  
Wiederholte Grenzwerte wie `+1` sollten in benannte Variablen ausgelagert werden.

**G34: In Funktionen nur eine Abstraktionsebene tiefer gehen**  

**G35: Konfigurierbare Daten hoch ansiedeln**  
Konstanten und Konfigurationswerte sollten auf höherer Ebene definiert werden, damit sie leicht auffindbar und änderbar sind.

**G36: Transitive Navigation vermeiden**  
Module sollten nur mit ihren direkten Abhängigkeiten interagieren und keine verschachtelten Objektstrukturen wie `a.getB().getC()` durchlaufen.
### Java

**J1: Lange Importlisten durch Platzhalter vermeiden**  
Verwende `import package.*`, um lange Listen spezieller Importe zu vermeiden und die Lesbarkeit zu erhöhen.

**J2: Keine Konstanten vererben**  
Vermeide es, Konstanten über Interfaces zu vererben – nutze statische Importe, um die Herkunft klar zu machen.

**J3: Konstanten im Gegensatz zu Enums**  
Nutze `enum` statt `public static final` Konstanten, da sie typensicherer, ausdrucksstärker und flexibler sind.
## Namen

**N1: Deskriptive Namen wählen**  
Namen sollen ausdrücken, was der Code tut.

**N2: Namen sollten der Abstraktionsebene entsprechen**  
Namen müssen zur konzeptionellen Ebene der Klasse oder Funktion passen, nicht zur Implementierung.

**N3: Möglichst die Standardnomenklatur verwenden**  
Verwende etablierte Namenskonventionen (z. B. `toString()`), statt eigene Begriffe zu erfinden.

**N4: Eindeutige Namen**  
Namen sollen klar ausdrücken, was eine Funktion oder Variable tut, um Verwechslungen zu vermeiden.

**N5: Namen für große Geltungsbereiche**  
Je größer der Geltungsbereich, desto länger und beschreibender sollte der Name sein.

**N6: Codierungen vermeiden**  
Namensmuster wie `m_` oder `s_` die den Typ oder die Sichtbarkeit kodieren vermeiden.

**N7: Namen sollten Nebeneffekte beschreiben**  
Wenn eine Funktion mehr tut als sie vorgibt (z. B. erzeugt statt nur zurückgibt), soll der Name das deutlich machen.
## Tests

**T1: Unzureichende Tests**  
Alles Wichtige testen.

**T2: Ein Coverage-Tool verwenden** 

**T3: Triviale Tests nicht überspringen**  
Einfache Tests sind wertvoll und helfen, Dokumentation und Stabilität zu verbessern.

**T4: Ein ignorierter Test zeigt eine Mehrdeutigkeit auf**  

**T5: Grenzbedingungen testen**  

**T6: Bei Bugs die Nachbarschaft gründlich testen**  
Wenn ein Fehler auftritt,  auch die angrenzenden Bereiche prüfen.

**T7: Das Muster des Scheiterns zur Diagnose nutzen**  

**T8: Hinweise durch Coverage-Patterns**  
Bestehende Tests analysieren, um Lücken zu erkennen.

**T9: Tests sollen schnell sein**  

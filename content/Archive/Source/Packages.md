
## Definition

- Pakete in Java dienen der Strukturierung von Klassen in logischen Gruppen.
- Sie helfen, Chaos zu vermeiden, indem verwandte Klassen in Unterordnern organisiert werden.

## Erstellung
Ein Paket wird erstellt, indem Klassen in ein Verzeichnis verschoben oder mit `package` am Anfang einer Datei deklariert werden.
## Nutzung
Um Klassen aus einem Paket zu verwenden, wird `import` genutzt:
- Spezifisch: `import figuren.Kreis;`
- Alle Klassen: `import figuren.*;`

## Sichtbarkeit

- private: Nur innerhalb der eigenen Klasse zugänglich.
- public: Überall zugänglich, wo die Klasse bekannt ist.
- keine Angabe: Sichtbar nur innerhalb des gleichen Pakets.
# Schrittweise Verfeinerung

### Allgemeine Prinzipien
- **Schrittweise Verfeinerung**: Code kontinuierlich verbessern, anstatt ihn auf einmal perfekt zu machen.  
- **Inkrementelle Entwicklung**: Code sollte schrittweise verbessert werden, anstatt alles auf einmal zu ändern.  
- **Schmutzigen Code als Zwischenschritt akzeptieren**: Es ist in Ordnung, zunächst unsauberen Code zu schreiben, solange er später bereinigt wird.  
- **Den Code kontinuierlich sauber und einfach halten**: Lesbarkeit und Wartbarkeit haben Priorität.  
- **Frühzeitig Probleme erkennen und lösen**: Wenn der Code schwer wartbar wird, sollte man innehalten und ihn verbessern.  

### Testen
- **Testgetriebene Entwicklung (TDD) anwenden**: Erst Tests schreiben, dann den Code entwickeln.  
- **Unit und Akzeptanztests einbauen**: Automatisierte Tests sichern die Qualität und erleichtern zukünftige Änderungen.  
- **Fehlgeschlagene Tests sofort korrigieren**: Tests müssen nach jeder Änderung erfolgreich laufen.  
- **Nach jeder Änderung lauffähig bleiben**: Das Programm sollte stets funktional bleiben, auch während der Entwicklung.  

### Struktur
- **Trennung der Zuständigkeiten (Separation of Concerns)**: Jede Klasse oder Methode sollte eine klar definierte Aufgabe haben.  
- **Modularisierung nutzen**: Wiederverwendbare oder komplexe Codeblöcke sollten in separate Methoden oder Klassen ausgelagert werden.  
- **Fehlermeldungen und Logik sauber trennen**: Fehlerbehandlung sollte die Hauptlogik nicht unübersichtlich machen.  

### Erweiterbarkeit und Wartbarkeit
- **Erweiterbarkeit prüfen**: Der Code sollte so geschrieben sein, dass neue Anforderungen leicht implementiert werden können.  
- **Designmuster erkennen und anwenden**: Wenn sich ähnliche Strukturen wiederholen, kann eine geeignete Abstraktion helfen.  
- **Wartbarkeit vor Geschwindigkeit**: Gut strukturierter Code ist wichtiger als schneller, aber unlesbarer Code.  
- **Redundanzen vermeiden**: Wiederholter Code sollte abstrahiert oder in eigene Module ausgelagert werden.  

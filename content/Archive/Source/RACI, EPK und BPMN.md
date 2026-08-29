> Den Prozess der Bearbeitung von Serviceanfragen beschreiben (S. 34 f.) 
> - grafische Prozessmodellierungen mittels EPK und BPMN erstellen 
> - Rollen und Zuständigkeiten in einer R-A-C-I-Matrix darstellen (S. 35 f.) 
> - Service-Level-Support mit den entsprechenden Service-Level-Agreements einordnen (S. 38f.)

## RACI
Bekannte Zuordnungstechnik in Matrixform zur Darstellung, Besprechung und Analyse von Verantwortlichkeiten:
#### Responsible
- Durchführungsverantwortung
- Person die tatsächlich den Prozess durchführt
#### Accountable
- Person die notwendigen Ressourcen genehmigt
- Kosten bzw. Gesamtverantwortung
#### Consulted
- Beraterrolle
- Person, deren Fachkompetenzen und Expertise notwendig zur Durchführung eines Prozesses oder die Tätigkeit sind.
#### Informed
- Informationsrecht
- Person die über den Status und die Ergebnisse informiert werden soll.

### Rollen
#### Positionen
Formale Stellen in einem Unternehmen:
- Leiterin
- Techniker
- Sachbearbeiter
#### Funktionen
Arbeiten oder zu leistende Beiträge in einer bestimmten Stelle.
#### Rollen
- Verhaltenserwartung oder Aktionen an Inhaber von Positionen und Funktionen und Gruppen.
- Werden individuell definiert
- Können den Mitarbeitern zugeordnet werden.

### Zuständigkeiten im IT-Service nach RACI
- Klare Rechenschaftspflicht in der RACI-Matrix sicherstellen.
- Jede Zeile sollte **nur ein "A" (Accountable)** aufweisen.
- Jede Zeile sollte **mindestens ein "R" (Responsible)** enthalten.
- Vermeidung von gleichzeitiger Zuordnung von "A" und "R" an dieselbe Person/Rolle für dieselbe Aktivität.
- **Service Owner:** Gesamtverantwortung für spezifischen Service im Service-Portfolio.
- **Case Owner:** Verantwortung für spezifischen Servicefall.

![500](Archive/Attachments/Pasted%20image%2020241209230834.png)
## Service-Level-Support

### Service-Level-Support und Eskalationsstufen

#### First-Level-Support:
- Bearbeitung einfacher Anfragen und Störungen.
- Nutzung von Wissensdatenbanken, um bekannte Probleme schnell zu lösen.
- Weiterleitung (Eskalation) an den Second-Level-Support, wenn keine Lösung gefunden wird.

#### Second-Level-Support:
- Bearbeitung komplexerer Anfragen und Diagnosen.
- Durchführung von Workarounds (provisorische Lösungen) und detaillierte Analyse.
- Eskalation an Third-Level-Support bei Spezialproblemen.

#### Third-Level-Support:
- Spezialisten (z. B. Hersteller oder externe Dienstleister).
- Lösung besonders komplexer Probleme und Durchführung von Systemanpassungen.

#### Workarounds:
Provisorische Lösungen, um schnell eine Behelfslösung bereitzustellen, bevor eine dauerhafte Lösung implementiert wird.

### Service-Level-Agreements (SLAs)

#### Definition
- Verträge zwischen Dienstleister und Kunden, die Qualität und Zeitrahmen der Servicebereitstellung regeln.
- Enthalten Parameter wie:
  - **Reaktionszeiten** (z. B. 1 Stunde für hohe Priorität).
  - **Lösungszeiten** abhängig von der Priorität.

#### Kategorisierung und Priorisierung
- **Kategorisierung**:
  - Zuordnung von Anfragen zu Dienstleistungskategorien (z. B. Software-Updates, Hardware-Reparaturen).
- **Priorität**:
  - Bewertung nach Dringlichkeit und Auswirkungen auf den Geschäftsbetrieb:
    - **Hohe Priorität**: Reaktion < 1 Stunde, Lösung < 4 Stunden.
    - **Mittlere Priorität**: Lösung innerhalb eines Werktages.
    - **Niedrige Priorität**: Lösung innerhalb von 2–3 Tagen.

#### Eskalation
- Erfolgt, wenn die Lösung in der vereinbarten Zeit nicht möglich ist.
- Weiterleitung an die nächsthöhere Support-Ebene.
### Ticket-Systeme

#### Zweck
- Zentralisierte Verwaltung von Serviceanfragen.
- Dokumentation von Anfragen, Diagnose und Lösungen.
- Überblick über den Bearbeitungsstatus und Eskalationen.
#### Funktionen
- Erstellen, Kategorisieren und Priorisieren von Tickets.
- Zuweisung an zuständige Bearbeiter (Case Owner).
- Transparente Kommunikation zwischen Support-Team und Kunden.
### KPIs (Key Performance Indicators) im SLA
#### Messung der Servicequalität
- **Reaktionszeit** (Zeit bis zur ersten Bearbeitung).
- **Lösungszeit** (Zeit bis zur Behebung des Problems).
- **Kundenzufriedenheit** (Feedback).
#### Ziel
- Stetige Verbesserung der Serviceprozesse und Einhaltung der SLA-Vorgaben.


---------------------
## EPK

### Start und Ende
- Eine EPK beginnt mit einem **Ereignis** oder **Prozesswegweiser**, nicht mit einer Funktion.
- Sie endet mit einem **Endereignis** oder **Prozesswegweiser**, nicht mit einer Funktion.
### Verbindungen
- Ereignisse folgen oder gehen Funktionen voraus, können nicht direkt aufeinander folgen.
- Funktionen können nicht direkt miteinander oder mit einem Prozesswegweiser verbunden sein.
- Alle Elemente der EPK (Ereignisse, Funktionen, Operatoren etc.) müssen miteinander verbunden sein. **Lose Objekte sind ungültig.**
### Logische Verknüpfungen
- **UND-Verknüpfung:** Alle eingehenden Ereignisse/Funktionen müssen erfüllt sein, damit die Funktion oder das Ereignis ausgeführt wird.
- **ODER-Verknüpfung:** Mindestens ein Ereignis/Funktion muss erfüllt sein; mehrere gleichzeitig sind möglich.
- **XOR-Verknüpfung (exklusives ODER):** Genau ein Ereignis oder eine Funktion darf eintreten; die anderen schließen sich aus.
### Vorteile
- Flexibel für die Abbildung von Standardprozessen.
- Anwendungsübergreifend und unterstützt durch viele Tools.
- Einfach zu erlernen und auch für Nicht-IT-Fachleute verständlich.
- Eignet sich gut für Simulationen, Analysen und Sollkonzepte.

### Nachteile
- Kann bei umfangreichen Modellen unübersichtlich werden.
- Wenig verbreitet außerhalb Deutschlands aufgrund fehlender Standardisierung.

## BPMN
- Visualisiert welche Schritte nötig sind für ein Ziel zu erreichen und was die Relationen zwischen den Schritte sind Sequenzfluss
- BPMN (Business Process Model and Notation) ist ein Industriestandard der Object Management Group (OMG) für die grafische Darstellung und Modellierung von Geschäftsprozessen. 
#### Ziele
- BPMN vereinheitlicht die verschiedenen Darstellungsformen der Prozessmodellierung. 
- Ein einheitlicher Standard fördert die Portabilität und Interoperabilität zwischen Systemen. 
- BPMN erleichtert die Darstellung, Ausführung und Kommunikation von Geschäftsprozessen.
- Es bietet umfassende Möglichkeiten, um Geschäftsprozesse detailliert zu beschreiben.
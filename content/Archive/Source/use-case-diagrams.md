## Definition
Ein Use Case beschreibt eine Anforderung an ein System und dokumentiert die Interaktionen zwischen Akteuren und dem System um Funktionen des Systems aus Sicht der Benutzer klar darzustellen.

![[Archive/Attachments/Pasted image 20250101210449.png|500]]
## Elemente
#### Akteur (Actor)

- Repräsentiert eine Rolle, die mit dem System interagiert (z. B. Benutzer, Geräte, andere Systeme)
- Darstellung: Strichmännchen

#### Use Case (Anwendungsfall)

- Beschreibt eine Funktionalität des Systems
- Alle use cases zusammen dokumentieren alle Möglichkeiten der Benutzung des Systems
- Darstellung: Ellipse

#### Beziehungen 
- **Include** (<>): zeigt, dass ein Use Case eine andere Funktionalität immer einbezieht.
- **Extend** (<>): zeigt eine optionale Funktionalität, die nur unter bestimmten Bedingungen ausgeführt wird.

#### Bedingung (Condition)

- Beschreibt, unter welchen Voraussetzungen ein **Extend**-Use Case ausgeführt wird
- Darstellung: Geschweifte Klammern `{}`

#### Systemgrenze
- Markiert, welche Funktionen innerhalb des Systems liegen.
- Darstellung: Rechteck, das die Use Cases umgibt.
#### Extension Points
Definieren, wo ein Use Case erweitert werden kann.

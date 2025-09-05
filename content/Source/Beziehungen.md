## Assoziation
Eine Assoziation ist eine Beziehung zwischen zwei Klassen, die keine Vererbung ist. Sie kann Aggregation, Komposition, aber auch eine lockere Bindung sein.

![[Attachments/Pasted image 20250102220531.png|500]]
- Pfeilspitze zeigt die Zugriffsrichtung an
- Jeder Zylinder hat genau einen Kreis
- Jeder Kreis gehört zu genau einem Zylinder

## Komposition
Eine Klasse enthält eine **Eigenschaft vom Typ der anderen Klasse**. Die Raute gibt an, welche Klasse die Eigenschaft enthält, d.h. das **Ganze** ist. Die andere Klasse ist dann ein **unzertrennlicher Teil** des Ganzen. Bei der Komposition leben und sterben die Teile mit dem Ganzen:

![[Attachments/Pasted image 20250102221228.png|500]]
- Ein Zylinder hat einen Kreis als Boden
- Bei dem Zylinder ist die Kardinalität  immer 1 und kann daher weggelassen werden
#### Factory Klasse
Darüber, dass es auch wirklich eine Komposition ist, wacht eine Factory-Klasse. Factories bauen komplexe Objekte zusammen:
```java
Zylinder dose = new Zylinder( new Kreis(3), 13.5);
```

## Aggregation
Die Raute gibt an, welche Klasse das "Ganze" ist. Objekte der anderen Klasse existieren unabhängig von dem Aggregationsobjekt. 

![[Attachments/Pasted image 20250102222056.png|500]]
- Wird das Projekt abgeschlossen, existieren die Mitarbeiter weiter
- Die Kardinalität an der Raute kann alles sein, bei Aggregation darf sie nicht weggelassen werden
- **shared aggregation:** Mitarbeiter können gleichzeitig mehreren Projekten zugeordnet werden.
## Kardinalitäten
- **1:**  genau eins
- **\*:**  beliebig viele
- **3..6:**  drei bis sechs
- **0..1:** null bis eins

## Komposition vs. Aggregation

#### Gemeinsamkeiten
- Beide repräsentieren eine **Ganzes-Teile-Beziehung**.
- In beiden Fällen wird die **Raute** in UML-Diagrammen auf der Seite des Ganzen (der Klasse, die das Ganze darstellt) verwendet.
#### Unterschiede

| **Komposition**                                            | **Aggregation**                                         |
| ---------------------------------------------------------- | ------------------------------------------------------- |
| **Unzertrennbar**: Teile leben und sterben mit dem Ganzen. | **Unabhängig**: Teile existieren unabhängig vom Ganzen. |
| Die Kardinalität des Ganzen ist stets **1**.               | Die Kardinalität des Ganzen kann **beliebig** sein.     |


**T**est **D**riven **D**evelopment 
## Die drei Gesetze der TDD
- Produktionscode erst schreiben, wenn Sie einen scheiternden Unit-Test geschrieben haben.
- Der Unit-Test darf nicht mehr Code enthalten, als für das Scheitern und ein korrektes Kompilieren des Tests erforderlich ist.
- Nur so viel Produktionscode schreiben, wie für das Beste hen des gegenwärtig scheiternden Tests ausreicht.

## Tests sauber halten
- Schmutzige Tests zu haben gleichbedeutend, wenn nicht sogar schlimmer ist, als keine Tests zu haben.
- Die Tests müssen geändert werden, wenn der Produktionscode weiterentwickelt wird.
- Wird der Produktionscode modifiziert, fangen alte Tests an zu scheitern, und das Chaos in dem Testcode macht es schwer, die Tests so zu ändern, dass sie wieder bestanden werden. 
- Mit sauberen Unit-Tests können Projekte erfolgreich abgewickelt werden.
- Testcode ist genauso wichtig wie Produktionscode.
- Die Unit-Tests, sorgen dafür, dass unser Code flexibel, wartbar und wiederverwendbar bleibt.

## Saubere Tests
Lesbarkeit zeichnet einen sauberen Code aus: Klarheit, Einfachheit und Ausdrucksdichte.
#### Domänenspezifische Testsprache
Eine Testsprache bilden, mit denen Programmierer sich selbst helfen, ihre Tests zu schreiben, und auch denen helfen, die diese Tests später lesen müssen.
#### Ein Doppelstandard
Ein Test muss immer noch einfach, präzise und ausdrucksstark sein, aber er muss nicht so effizient wie der Produktionscode sein.
#### Ein assert pro Test
Ein Test in separate Tests zerlegen, die ihre eigene spezielle Zusicherung enthalten.
#### Ein Konzept pro Test
In jeder Testfunktion soll nur ein einziges Konzept getestet werden.

#### F.I.R.S.T
- **Fast:** Tests sollen schnell laufen.
- **Independent:** Tests sollen nicht voneinander abhängen.
- **Repeatable:** Tests sollten in jeder Umgebung wiederholbar sein.
- **Self-Validating:** Die Tests sollten einen booleschen Output haben. Entweder sie werden bestanden oder sie scheitern.
- **Timely:** Die Tests müssen rechtzeitig geschrieben werden. Unit-Tests sollten kurz vor dem Produktionscode geschrieben werden, der dafür sorgt, dass sie bestanden werden.
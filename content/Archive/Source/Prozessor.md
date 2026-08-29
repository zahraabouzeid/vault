Steuerung elektrischer Prozesse, zentral für Computer und eingebettete Systeme (z. B. Waschmaschinen, Flugzeuge).

## Bestandteile der CPU

**Steuerwerk:**
- Lädt Befehle, dekodiert sie (über Befehlssatz, z. B. x86) und interpretiert sie.
- Enthält Register.

**Rechenwerk (ALU):**
Führt arithmetische (Addition, Subtraktion) und logische Operationen aus.

**Speichercontroller:**
Steuert Daten zwischen CPU und RAM.

**Cache-Speicher (Zwischenspeicher):** Beschleunigt Datenzugriffe, da RAM langsamer als CPU.
- L1-Cache: Direkt im Kern, sehr schnell (64–128 KB).
- L2-Cache: Größer (256 KB–2 MB), etwas langsamer.
- L3-Cache: Größter Cache (bis 256 MB), teilt sich mehrere Kerne.    
## Moderne CPUs
- Mehrere Kerne (physisch & virtuell durch Hyper-Threading).
- Parallele Verarbeitung für höhere Effizienz.
- Integrierte Komponenten wie Speichercontroller & Grafikeinheit.

## Multi und Hyperthreading
Hyper-Threading (HT) ist eine Technologie von Intel, die es einem physischen Kern ermöglicht, zwei logische Threads gleichzeitig zu verarbeiten, was die Effizienz steigert. Dadurch kann der Prozessor Ressourcen besser ausnutzen, besonders bei Multitasking. Multithreading allgemein bezieht sich darauf, mehrere Threads gleichzeitig zu bearbeiten, um Prozesse effizienter auszuführen. Im Vergleich zu physischen Kernen, die echte parallele Verarbeitung ermöglichen, ist Hyper-Threading eine Art "Simulierung" zusätzlicher Kerne, jedoch ohne echte Mehrleistung bei extrem rechenintensiven Aufgaben.
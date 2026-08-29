## Arten

- Onboard-Lösungen: Direkt auf dem Mainboard; eher für einfache Anwendungen geeignet.
- APUs (Accelerated Processing Units): Kombination aus CPU und GPU auf einem Chip; ebenfalls limitiert in der Leistung.
- Dedizierte Grafikkarten: Separate Einheiten bieten maximale Leistung.

## Hauptbestandteile einer Grafikkarte

**Platine (PCB):**
- Trägt alle Komponenten.
- Verbindet den Grafikprozessor (GPU) mit dem Speicher.
- Enthält bis zu 14 Schichten für komplexe Datenleitungen.

**Spannungsversorgung:**
- PCIe-Steckplatz liefert 75 Watt.
- Externe Anschlüsse: 6-polig (75 W) und 8-polig (150 W). Hochleistungs-GPUs nutzen beide, um bis zu 300 W zu liefern.

**Videospeicher (VRAM):**
- Zwischenspeicher für Grafikdaten.
- Typ: GDDR5 (schneller als DDR3), Taktfrequenzen bis 3500 MHz.
- Speichergrößen variieren.

**Grafikprozessor (GPU):**
- Kernstück der Karte.
- Hat Tausende von Kernen.
- Parallele Verarbeitung (Shader): Berechnung von Texturen, Geometrien und Effekten.

## Arbeitsweise

**Shader-Typen:**
- Vertex Shader: Wandeln Eckdaten in Polygone um.
- Tessellation Shader: Verfeinern Polygone.
- Geometry Shader: Modifizieren Geometrien.
- Pixel Shader: Berechnen Effekte wie Beleuchtung.

**Rasterisierung:** Wandelt Geometrien in Pixel.
## SATA und SAS
- Verbinden Speichermedien (Festplatten, SSDs) mit dem System.
- Der Unterschied ist **Leistung**: SAS = schneller, stabiler, aber teurer. SATA = einfacher, günstiger, reicht für den Alltag.
## Direct Attach Storage (DAS)
- der Speicher (Festplatten) **direkt** an einen Server angeschlossen ist, z. B. über SCSI oder SATA.
- ist direkt verbunden und gehört einem bestimmten Server und keinem anderen.
- ist unflexibel dh. andere Server können diesen Speicher nicht einfach nutzen, weil er "fest verdrahtet" ist.
- das Vorteil ist, dass es schnell ist, weil es keine Umwege (z. B. durchs Netzwerk) gibt, und es hat wenig Verwaltungsaufwand (Overhead).

## Network Attached Storage (NAS)
- Server oder Geräte verbinden sich über das Netzwerk mit dem NAS, um Dateien zu speichern oder zu lesen (Zugriff übers Netzwerk).
- Das NAS hat ein eigenes Dateisystem (z. B. ext4 oder NTFS), das die Dateien organisiert.
- Optimiert für gemeinsame Nutzung besonders, wenn mehrere Leute oder Systeme gleichzeitig auf dieselben Dateien zugreifen müssen (z. B. Freigaben über SMB oder NFS).

## Storage Area Network (SAN)
- Blockbasierte Übertragung von Datenblöcke, nicht Dateien. Es ist, als hätte dein Computer eine extra Festplatte im Netzwerk.
- Das Dateisystem ist auf dem **Client**, der den Speicher nutzt.
- Datenblöcke werden wie bei z.B. SATA oder SAS übertragen, aber nicht über direkte Kabelverbindungen sondern über ein Netzwerk Filesystem auf dem SAN-Client.


## SAN vs NAS
![500](Archive/Attachments/Pasted%20image%2020241201231915.png)
- **Dedizierter Speicher**, der direkt an Servern hängt.
- **Pooled Storage**, den mehrere User/Server gleichzeitig nutzen können.
## SAN mit Fibre Channel
**Topologie für:**
- Mission-kritische Berechnungen
- Hohe Leistungsanforderungen
- Potenziell hoher ROI (Return on Investment)

**Topologie nicht für:**

- Begrenztes Budget
- Begrenzte Mitarbeiterzahl
- Einfache Implementierung und laufende Wartung

## SAN mit iSCSI
iSCSI (Internet Small Computer Systems Interface) ist ein **Protokoll**, das es ermöglicht, **Speichergeräte** über ein **IP-Netzwerk** mit einem Computer oder Server zu verbinden. Es überträgt **Blockdaten** (ähnlich wie bei SAS oder SATA), sodass der Server das entfernte Speichergerät wie eine lokale Festplatte nutzen kann.

**Topologie für:**
- Kostenwirksamer Speicher
- Maximierung der begrenzten Mitarbeiterzahl
- SMBs (kleine und mittlere Unternehmen), Arbeitsgruppen und Remote-Office-Umgebungen
- Nutzung eines weit verbreiteten IP-Netzwerks

**Topologie nicht für:**

- Späte Technologieadopter
- Hohe Anforderungen im Enterprise-Bereich
- Kunden, die gegen die Erweiterung des Ethernet-Umfelds für Speicher sind.

## iSCSI Initiator und Target
![400](Archive/Attachments/Pasted%20image%2020241201235341.png)
- Verbindungen können sicheren Login verwenden (CHAP) 
- Standard iSCSI port ist 3260
## iSCI
![500](Archive/Attachments/Pasted%20image%2020241201235544.png)
- iSCSI kapselt quasi DAS über Ethernet 
- Erlaubt den Transport von I/O block data über IP networks 
- SCSI Befehle werden als Nutzdaten in TCP-Segmente gekapselt
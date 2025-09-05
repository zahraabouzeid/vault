
## 7.1 Ethernet-Frames
#### Ethernet Kapselung
- Kabelgebundene LAN-Technologie (Alternative: WLAN)
- Medien: Twisted-Pair, Glasfaser, Koaxial
- Schichten: Layer 1 (Bitübertragung), Layer 2 (Sicherung/MAC)
- Standards: IEEE 802.2 & 802.3
- Datenraten: 
	- 10 Mbit/s
	- 100 Mbit/s
	- 1.000 Mbit/s
	- 10.000 Mbit/s (10 Gbit/s)
	- 40.000 Mbit/s (40 Gbit/s)
	- 100.000 Mbit/s (100 Gbit/s)
- Definiert physikalische und logische Netzwerkfunktionen
- Arbeitet auf der Sicherungs- und der Bitübertragungsschicht.  

![[Attachments/Pasted image 20250622194843.png|400]]

#### Data-Link-Sublayer
IEEE 802-Standards (z. B. Ethernet) nutzen zwei Sublayer des Data-Link-Layers:
- **LLC (Logical Link Control)** – IEEE 802.2
	- Vermittelt zwischen Netzwerksoftware (Layer 3) und Hardware
	- Kennzeichnet das verwendete Layer-3-Protokoll (z. B. IPv4/IPv6)
	- Erlaubt mehreren Protokollen die Nutzung derselben Schnittstelle

- **MAC (Media Access Control)** – z. B. IEEE 802.3 / 802.11 / 802.15
	- In Hardware integriert
	- Zuständig für Datenkapselung und Medienzugriff
	- Verwaltet Data-Link-Adressierung (z. B. MAC-Adresse)
	- Bindeglied zum Physical Layer

![[Attachments/Pasted image 20250622195449.png|500]]

#### MAC-Sublayer
Der MAC-Sublayer ist für die Datenkapselung und den Zugriff auf das Medium verantwortlich.  

**Datenkapselung**  
Die IEEE 802.3 Datenkapselung umfasst Folgendes:  
- **Ethernet-Frame**: Struktur für den Ethernet Frame im LAN
- **Adressierung**: Quell- und Ziel-MAC-Adresse im Frame enthalten
- **Fehlererkennung**: FCS-Feld (Frame Check Sequence) prüft auf Übertragungsfehler

**Medienzugriff**  
- MAC-Sublayer (IEEE 802.3) regelt Kommunikation über Kupfer & Glasfaser
- **Altes Ethernet** (Bus/Hubs, Halbduplex):
    - Gemeinsames Medium → **CSMA/CD** (Kollisionserkennung) nötig
- **Modernes Ethernet** (Switches, Vollduplex):
    - Keine Kollisionen → **kein CSMA/CD** erforderlich
#### Felder des Ethernet Frames
![[Attachments/Pasted image 20250622195644.png|500]]
- **Minimale Frame-Größe**: 64 Byte
- **Maximale Standardgröße**: 1518 Byte (ohne Präambel)
- **Kollisionsfragmente / Runt-Frames**: < 64 Byte → automatisch verworfen
- **Jumbo-/Baby-Giant-Frames**: 
	- 1500 Byte Daten → gelten als übergroß
    - Werden meist von Fast/Gigabit-Ethernet-Switches und NICs unterstützt
- **Ungültige Frames**:
    - < 64 oder > 1518 Byte → vom Empfänger verworfen
    - Ursache oft: Kollisionen oder Störungen
- **Präambel:**
	- Die **Präambel** ist ein spezielles Feld am **Anfang eines Ethernet-Frames**
	- Länge: **7 Byte Präambel** + **1 Byte SFD (Start Frame Delimiter)**
	- Funktion:
	    - Synchronisation zwischen Sender und Empfänger
	    - Signalisiert: "Jetzt kommt ein gültiger Frame“
	- Die Präambel zählt **nicht zur berechneten Frame-Größe** (also nicht in den 64–1518 Byte enthalten)

| **Feld**                            | **Beschreibung** |
|------------------------------------|------------------|
| **Präambel- und Start-Frame-Delimiter-Felder** | 7 Bytes Präambel + 1 Byte Start Frame Delimiter (SFD). Dienen der Synchronisation zwischen Sender und Empfänger. Signalisieren den Beginn eines gültigen Frames. Nicht Teil der Frame-Größenberechnung. |
| **Ziel-MAC-Adresse**               | 6-Byte-Feld zur Identifikation des Empfängers. Wird mit der MAC-Adresse des Geräts verglichen. Bei Übereinstimmung wird der Frame akzeptiert. Kann Unicast-, Multicast- oder Broadcast-Adresse sein. |
| **Quell-MAC-Adresse**              | 6-Byte-Feld, das angibt, von welcher Netzwerkkarte oder Schnittstelle der Frame stammt. |
| **Typ/Länge**                      | 2-Byte-Feld zur Identifikation des Protokolls der nächsthöheren Schicht (z. B. 0x0800 = IPv4, 0x86DD = IPv6, 0x0806 = ARP). Wird auch EtherType genannt. |
| **Daten**                          | 46–1500 Byte. Enthält die gekapselten Daten der höheren Schichten (z. B. IPv4-Paket). Bei zu kleinen Paketen werden Padding-Bits hinzugefügt, um auf mindestens 64 Byte Gesamtgröße zu kommen. |
| **FCS (Frame Check Sequence)**     | 4-Byte-Feld zur Fehlererkennung (CRC-Prüfung). Der Empfänger prüft mit eigener CRC-Berechnung, ob der Frame fehlerfrei ist. Bei Abweichung wird der Frame verworfen. |

## 7.2 Ethernet MAC-Adressen
#### MAC-Adresse und Hexadezimalformat  
- Eine Ethernet-MAC-Adresse besteht aus einem **48-Bit-Binärwert**.
- Darstellung erfolgt in **12 Hexadezimalwerten**.
- **8 Bit = 1 Byte** → entspricht **2 Hex-Ziffern** (z. B. `00000000` bis `11111111` = `00` bis `FF`).
- **Führende Nullen werden angezeigt**, um die vollständige 8-Bit-Darstellung zu erhalten (z. B. `00001010` = `0A`).
- Hexadezimalzahlen werden häufig mit **`0x`** gekennzeichnet (z. B. `0x73`).
- Weitere Darstellungen: **tiefgestellte 16** (z. B. `73₁₆`) oder **Suffix H** (z. B. `73H`).

#### Ethernet-MAC-Adresse
![[Attachments/Pasted image 20250622202556.png|500]]

- Alle Geräte in einem Ethernet-LAN nutzen dasselbe Medium → eindeutige **MAC-Adresse** nötig
- **MAC-Adresse**:
    - 48 Bit = **6 Byte**
    - Darstellung: 12 **hexadezimale Ziffern** (z. B. `00:1A:2B:3C:4D:5E`)
- Jede MAC-Adresse ist **weltweit eindeutig**
- Aufbau:
    - Erste 3 Byte = **OUI** (Organizationally Unique Identifier, vom Hersteller)
    - Letzte 3 Byte = **Geräte-/Hersteller-spezifisch**
- Hersteller müssen sich beim **IEEE registrieren**, um OUI zu bekommen
#### Frame-Verarbeitung  
- Jeder Ethernet-Frame enthält:
    - **Quell-MAC-Adresse** (Sender)
    - **Ziel-MAC-Adresse** (Empfänger)
- **Empfangsprüfung durch Netzwerkkarte (NIC):**
    - Vergleicht Ziel-MAC im Frame mit eigener MAC-Adresse (im RAM gespeichert)
    - **Bei Übereinstimmung** → Frame wird zur Entkapselung an höhere OSI-Schichten weitergeleitet
    - **Keine Übereinstimmung** → Frame wird verworfen
- **Jedes Gerät im Netzwerk** (z. B. PC, Server, Router, Drucker, Smartphone) hat eine eigene MAC-Adresse über die jeweilige **NIC** (Network Interface Card)

> [!info] Ethernet-Netzwerkkarten akzeptieren auch Frames, wenn die Ziel-MAC-Adresse eine Broadcast oder eine Multicast-Gruppe ist, falls der Host zu dieser Multicastgruppe gehört.  
#### Unicast-MAC-Adresse

In Ethernet werden verschiedene MAC-Adressen der Schicht 2 für die Unicast-, Broadcast- und Multicast-Kommunikation verwendet.

![[Attachments/Pasted image 20250622202939.png|500]]

- Eindeutige Adresse für **1:1-Kommunikation** (Sender → genau ein Empfänger)
- **Adressauflösung (IP → MAC)**:
    - **IPv4**: über **ARP** (Address Resolution Protocol)
    - **IPv6**: über **ND** (Neighbor Discovery)

>[!info] Die Quell-MAC-Adresse muss immer ein Upload sein.

#### Broadcast-MAC-Adresse
![[Attachments/Pasted image 20250622203109.png|500]]
- **Broadcast-Frame** wird an **alle Geräte** im lokalen Ethernet-LAN gesendet
- **Ziel-MAC-Adresse**: `FF-FF-FF-FF-FF-FF` (48 Einsen in binär)
- Switch **flutet** den Frame an alle Ports (außer Eingangsport)
- **Router leitet Broadcasts nicht weiter** (bleiben in der Broadcast-Domäne)
- **IPv4-Broadcast**: Zieladresse = alle Bits im Host-Teil auf 1 → alle Hosts im LAN müssen reagieren
#### Multicast-MAC-Adresse
![[Attachments/Pasted image 20250622203316.png|500]]

- **Multicast-Frames**: werden von **einer definierten Gruppe von Geräten** empfangen (Multicast-Gruppe)
- **Ziel-MAC-Adressen**:
    - **IPv4-Multicast**: beginnt mit `01-00-5E`
    - **IPv6-Multicast**: beginnt mit `33-33`
    - Weitere reservierte Multicast-Adressen: z. B. für **STP**, **LLDP**
- **Switch-Verhalten**:
    - Standard: Frame wird an alle Ports (außer Eingangsport) geflutet
    - Ausnahme: **Multicast-Snooping** aktiv → gezielte Weiterleitung nur an interessierte Ports
- **Router-Verhalten**:
    - Leitet Multicast nur weiter, wenn speziell **dafür konfiguriert**
- **Quell-/Ziel-Adressen**:
    - Quelle immer **Unicast-Adresse**
    - Ziel = **Multicast-Adresse** (stellt Host-Gruppe dar)
- **IP-Multicast-Adressen** → benötigen passende **MAC-Multicast-Adressen** zur Zustellung im LAN

## 7.3 Die MAC-Adresstabelle

#### Grundlagen des MAC-Adresstabellen-Switches
![[Attachments/Pasted image 20250622203506.png|500]]

- **Layer-2-Switch** trifft Entscheidungen **nur anhand der MAC-Adressen** (nicht IP oder Protokoll)
- Funktioniert unabhängig vom Inhalt des Frames (z. B. IPv4, ARP, IPv6, ND)
- Nutzt eine **MAC-Adresstabelle** zur gezielten Weiterleitung
- Unterschied zu Hubs:
    - **Switch**: leitet Frames gezielt weiter
    - **Hub**: sendet an alle Ports außer dem Eingang
- **MAC-Tabelle beim Start**: zunächst **leer**, wird dynamisch beim Empfang von Frames aufgebaut

> [!info] Die MAC-Adresstabelle wird manchmal auch CAM-Tabelle (Content Addressable Memory) genannt.

#### Switch Learning and Forwarding  
**Überprüfen Sie die Quell-MAC-Adresse** 
![[Attachments/Pasted image 20250622203819.png|500]]
- Jeder eingehende Frame wird vom Switch analysiert
- **Lernprozess**:
    - Prüfe **Quell-MAC-Adresse** + **eingehender Port**
    - **Neue MAC-Adresse** → Eintrag mit Portnummer wird **zur Tabelle hinzugefügt**
    - **Bekannte MAC-Adresse** → **Timer wird zurückgesetzt** (Aktualisierung)
- **Gültigkeitsdauer**:
    - Einträge bleiben **standardmäßig 5 Minuten** gespeichert (wenn kein neuer Frame kommt)

>[!info] Wenn die Quell-MAC-Adresse in der Tabelle vorhanden ist, sich aber auf einem anderen Port befindet, behandelt der Switch dies als neuen Eintrag. Der Eintrag wird durch dieselbe MAC-Adresse, aber mit der aktuelleren Port-Nummer ersetzt.

**Suchen Sie die Ziel-MAC-Adresse (Weiterleiten)**  
![[Attachments/Pasted image 20250622203840.png|500]]
- **Ziel-MAC ist Unicast** → Switch prüft MAC-Tabelle:
    - **Eintrag vorhanden** → Frame wird gezielt an **zugeordneten Port** weitergeleitet
    - **Eintrag fehlt** → Frame wird an **alle Ports außer dem Eingangsport** gesendet
        - Vorgang nennt sich: **unbekannter Unicast**

>[!info] Wenn die Ziel-MAC-Adresse eine Broadcast- oder eine Multicast-Adresse ist, wird der Frame ebenfalls an alle Ports mit Ausnahme des eingehenden Ports weitergeleitet.

#### Filtern von Frames  
- Switch empfängt Frames von mehreren Geräten
- **Quell-MAC-Adressen** werden verwendet, um die **MAC-Tabelle dynamisch zu füllen**
- **Ziel-MAC-Adresse bekannt** → Switch **filtert** den Frame und **leitet ihn gezielt** an den zugehörigen Port weiter
- Ergebnis: Effiziente, zielgerichtete Kommunikation im LAN
#### MAC-Adresstabelle auf verbundenen Switches  **
![[Attachments/Pasted image 20250622204611.png|500]]
**Ausgangssituation:**
Zwei Computer, **PC-A** und **PC-B**, sind über zwei Switches (**S1** und **S2**) verbunden. Sie kommunizieren über **Ethernet-Frames**, also kleine Datenpakete mit Quell- und Ziel-MAC-Adressen. Jeder Switch kann MAC-Adressen lernen, um gezielt weiterzuleiten.

**Phase 1: PC-A sendet einen Frame an PC-B**
1. **PC-A erstellt einen Frame**
    - **Quell-MAC**: `00-0A`
    - **Ziel-MAC**: `00-0B`
2. **Switch S1 empfängt den Frame**
    - Erkennt, dass die **Quell-MAC `00-0A`** neu ist
    - Speichert sie mit dem Port, an dem der Frame ankam
    - Die **Ziel-MAC `00-0B`** ist unbekannt → **S1 sendet den Frame an alle Ports (außer zurück)**
3. **PC-B empfängt den Frame**
    - Stellt fest: Ziel-MAC stimmt mit seiner Adresse überein → **Frame wird akzeptiert**
4. **Frame wird auch an Switch S2 weitergeleitet**
    - S2 speichert **Quell-MAC `00-0A`** und den Port
    - Die Zieladresse (`00-0B`) kennt S2 nicht → **leitet Frame an alle Ports außer dem Eingang**
5. **PC-B prüft erneut, erkennt aber diesmal eine falsche Zieladresse** → **verwirft Frame**  
    **(Hinweis: Dies ist vermutlich ein zweiter Frame, der aus einer anderen Richtung kam)**
    - Auch andere Geräte (z. B. Router) verwerfen den Frame, da Zieladresse nicht passt

**Phase 2: PC-B antwortet an PC-A**
1. **PC-B sendet einen Frame zurück**
    - **Quell-MAC**: `00-0B`
    - **Ziel-MAC**: `00-0A`
2. **Switch S1 empfängt den Frame**
    - Lernt **MAC `00-0B`** und den zugehörigen Port
    - Erkennt: **Ziel-MAC `00-0A`** ist bereits in der Tabelle
    - → **Leitet den Frame direkt an Port 1** (also an PC-A)
3. **PC-A prüft die Zieladresse**
    - Stimmt mit seiner Adresse überein → **Frame wird akzeptiert**

**Fazit**
- Switches **lernen automatisch**, welche MAC-Adresse an welchem Port erreichbar ist
- Anfangs wird an **alle Ports geflutet**, wenn Zieladresse unbekannt ist
- Sobald MAC-Adressen bekannt sind, erfolgt **gezielte Weiterleitung**
- Das spart Bandbreite und verhindert unnötigen Datenverkehr im Netzwerk

#### Senden des Frames an das Standard-Gateway
![[Attachments/Pasted image 20250622205030.png|500]]
**Ziel:**
**PC-A** möchte ein **Paket an das Internet** senden. Die Ziel-IP-Adresse liegt **außerhalb des lokalen Netzwerks**, daher wird das Paket an den **Router** geschickt. Der Router antwortet ebenfalls mit einem Frame zurück an PC-A.

**Teil 1: PC-A sendet an das Internet**
1. **Frame-Erstellung bei PC-A**
    - **Quell-MAC**: MAC von PC-A
    - **Ziel-MAC**: MAC des Routers (`00-0D`)
    - **Grund**: Ziel-IP ist außerhalb → Gateway (Router) wird Ziel des Ethernet-Frames

2. **Switch S1 verarbeitet den Frame**
    - Quell-MAC ist **bereits bekannt** → **Timer wird aktualisiert**
    - Ziel-MAC **nicht bekannt** → **S1 flutet** den Frame an alle Ports

3. **PC-B erhält den Frame**
    - Ziel-MAC passt **nicht** → **Frame wird verworfen**

4. **Switch S2 erhält den Frame**
    - Quell-MAC ist **bekannt** → Timer wird aktualisiert
    - Ziel-MAC **unbekannt** → **S2 flutet** erneut alle Ports

5. **PC-C empfängt Frame**
    - Ziel-MAC passt nicht → verwirft Frame

6. **Router empfängt Frame**
    - Ziel-MAC **stimmt überein** → **Router akzeptiert** den Frame
    - Verarbeitung auf Layer 3 (IP) erfolgt nun im Router

 **Teil 2: Antwort vom Router an PC-A**
1. **Router erstellt Antwort-Frame**
    - **Quell-IP**: aus dem entfernten (Internet-)Netz
    - **Quell-MAC**: MAC-Adresse des Routers (`00-0D`)
    - **Ziel-MAC**: MAC von PC-A
2. **Switch S2 empfängt Frame**
    - Quell-MAC `00-0D` **neu** → wird mit Port gespeichert
    - Ziel-MAC (PC-A) **bekannt** → Frame wird **gezielt weitergeleitet**
3. **Switch S1 empfängt Frame**
    - Quell-MAC `00-0D` wird **eingetragen**
    - Ziel-MAC (PC-A) ist **bekannt** → Weiterleitung direkt an Port von PC-A
4. **PC-A empfängt Frame**
    - Ziel-MAC stimmt überein → **Frame wird akzeptiert**

### Fazit:
- Switches lernen **Quell-MAC-Adressen dynamisch**
- Ziel-MAC unbekannt → **Broadcast (Flooding)**
- Ziel-MAC bekannt → **gezielte Weiterleitung**
- Kommunikation mit fremden Netzwerken läuft **über das Default Gateway (Router)**
- MAC-Tabelle ermöglicht effiziente Weiterleitung in zukünftigen Kommunikationen

## 7.4 Switch-Geschwindigkeiten und Weiterleitungsmethoden

#### Frame-Forwarding Methoden auf Cisco Switches  
Switches verwenden eine der folgenden Weiterleitungsmethoden, um Daten zwischen Netzwerk-Ports zu übertragen:  
- **Store-and-Forward Switching**
    - **Empfängt gesamten Frame vollständig**
    - Führt **CRC-Prüfung** (Fehlererkennung) durch
    - Nur **fehlerfreie Frames** werden weitergeleitet
    - **Vorteil**: schützt Bandbreite durch Verwerfen beschädigter Frames
    - Wird z. B. bei **QoS (Quality of Service)** verwendet (z. B. bei VoIP)
- **Cut-Through Switching**
    - **Beginnt Weiterleitung, sobald Ziel-MAC gelesen wurde**
    - Frame muss **nicht vollständig empfangen** sein
    - **Schneller**, aber keine Fehlerprüfung wie bei Store-and-Forward.  
#### Cut-Through Switching  
- Switch beginnt Weiterleitung **während des Empfangs**
- Liest nur so viel wie nötig (mind. Ziel-MAC-Adresse)
- **Keine CRC-/Fehlerprüfung** → schnell, aber fehleranfällig

**Arten von Cut-Through Switching**
- **Fast-Forward Switching**
    - **Geringste Latenz**
    - Weiterleitung **sofort nach Ziel-MAC-Erkennung**
    - **Fehlerhafte Frames werden weitergeleitet**
    - **Zielgerät** verwirft sie ggf. → hohe Geschwindigkeit, weniger Zuverlässigkeit
    - → **Standardmethode bei Cut-Through**

- **Fragment-Free Switching**
    - **Kompromiss** zwischen Geschwindigkeit und Zuverlässigkeit
    - Switch wartet auf die **ersten 64 Byte**
    - Grund: Die meisten Kollisionen/Fehler passieren dort
    - → **Vermeidung beschädigter Frames**, ohne komplette Verzögerung wie bei Store-and-Forward

#### Speicherpufferung auf Switches  
Ein Ethernet-Switch kann Frames zwischenspeichern, bevor er sie weitergeleitet insbesondere wenn der Zielport überlastet ist.  

| Methode                 | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Port-basierter Speicher | • Frames werden in Warteschlangen gespeichert, die mit bestimmten eingehenden und ausgehenden Ports verknüpft sind. <br>• Ein Frame wird nur dann an den ausgehenden Port übertragen, wenn alle vorhergehenden Frames in der Warteschlange erfolgreich übertragen wurden. <br>• Es kann vorkommen, dass ein einzelner Frame die Übertragung aller nachfolgenden Frames blockiert, weil der zugehörige Ziel-Port belegt ist. <br>• Diese Verzögerung tritt sogar auch dann auf, wenn die anderen Frames an freie Ziel-Ports gesendet werden könnten. |
| Gemeinsamer Speicher    | • Belegt alle Frames in einem Speicherpuffer, der von allen Switch-Ports gemeinsam genutzt wird, und die Menge an Pufferspeicher, die von einem Port benötigt wird, wird dynamisch zugewiesen. <br>• Dies ermöglicht es, einen Frame an einem Port zu empfangen und ihn dann an einen anderen Port weiterzuleiten, ohne ihn in eine Warteschlange zu stellen.                                                                                                                                                                                       |

- Shared Memory Pufferung führt zu größeren Frames, so dass weniger frames verworfen werden. Dies ist wichtig beim asymmetrischen Switching, das unterschiedliche Datenraten an verschiedenen Ports zulässt. Daher kann für bestimmte Ports (z.B. Serverport) mehr Bandbreite erforderlich werden.

#### Duplex- und Geschwindigkeitseinstellungen  
- **Switch-Port-Einstellungen**:
    - **Bandbreite** (auch: Geschwindigkeit)
    - **Duplex-Modus** (Datenrichtung)
- **Duplex-Modi**:
    - **Vollduplex**: gleichzeitiges Senden & Empfangen möglich
    - **Halbduplex**: nur eine Richtung gleichzeitig (Senden **oder** Empfangen)
- **Wichtig**: Switch und Gerät müssen **übereinstimmende Einstellungen** haben
    - Mismatches führen zu Paketverlusten & geringer Leistung
- **Autonegotiation**:
    - Geräte handeln **automatisch** Bandbreite & Duplex-Modus aus
    - Weit verbreitet, aber kann bei Fehlkonfiguration Probleme verursachen

>[!info] Gigabit-Ethernet-Ports können nur im Vollduplex-Modus arbeiten.  

**Duplexfehler **
- Häufige Ursache für **Leistungsprobleme bei 10/100 Mbit/s** Ethernet
- Entsteht, wenn ein Port auf **Halbduplex**, der andere auf **Vollduplex** steht
- Folgen: **Kollisionen**, Paketverluste, langsame Datenübertragung
- Ursachen:
    - **Autonegotiation** scheitert bei Neustart oder Reset
    - **Manuelle Änderung** nur auf einer Seite (andere bleibt unverändert)
- **Best Practice**:
    - Beide Seiten der Verbindung **gleich konfigurieren**
    - **Empfohlen**: Beide Ports auf **Vollduplex + Autonegotiation aktiviert**
    - Alternativ: **manuell identisch konfigurieren**, aber nur wenn nötig

#### Auto-MDIX  
Verbindungen zwischen Geräten erfordern die Verwendung eines Crossover- oder Straight-Through-Kabels. Die Art des benötigten Kabels hängt vom Typ der Geräte ab, die miteinander verbunden werden sollen.  

>[!info] Eine direkte Verbindung zwischen einem Router und einem Host erfordert eine Cross-Over-Verbindung.  

- **Auto-MDIX**: automatische Erkennung & Anpassung des **Kabeltyps** (Crossover oder Straight-Through)
- Switch konfiguriert Schnittstelle automatisch – egal, welches Ethernet-Kabel angeschlossen ist
- **Standardmäßig aktiviert** bei Cisco IOS ab Version **12.2(18)SE**
- Funktion kann **deaktiviert sein** → richtige Kabelwahl weiterhin empfohlen
- **Aktivierung (CLI)**: `mdix auto`

## 7.5 Fazit

- **Ethernet** arbeitet auf **Layer 1 (Bitübertragung)** und **Layer 2 (Sicherung)**
- Nutzt die **LLC-** und **MAC-Sublayer** der Sicherungsschicht
- **Ethernet-Frame** enthält: Präambel, Ziel-MAC, Quell-MAC, EtherType, Daten, FCS
- **MAC-Adressen** (48 Bit / 6 Byte) identifizieren Geräte eindeutig auf Layer 2
- **Kommunikationsarten**: **Unicast**, **Broadcast**, **Multicast**
- **Switches** leiten Frames **auf Basis von MAC-Adressen (Layer 2)** weiter
    - Lernen MAC-Adressen dynamisch über eingehende Frames
    - Prüfen Ziel-MAC → gezielte Weiterleitung oder Flooding (bei Unbekanntem)
- **Weiterleitungsmethoden**:
    - **Store-and-Forward** (mit Fehlerprüfung)
    - **Cut-Through** (schneller, keine Fehlerprüfung)
        - Varianten: **Fast-Forward**, **Fragment-Free**
- **Speicherpufferung**:
    - **Port-based** (feste Warteschlangen pro Port)
    - **Shared Memory** (gemeinsamer, dynamischer Puffer)
- **Duplexmodi**:
    - **Halbduplex** = nur Senden **oder** Empfangen
    - **Vollduplex** = gleichzeitig Senden **und** Empfangen


---
## Quiz

- **Welcher Teil eines Ethernet-Frames verwendet ein Pad, um das Frame-Feld auf seine Mindestgröße von 64 Bytes zu erhöhen?** Datenfeld

- **Welcher Teil eines Ethernet-Frames erkennt Fehler im Frame?** Frame-Prüfsumme

- **Welcher Teil eines Ethernet-Frames beschreibt das Protokoll der nächsthöheren Schicht?** Start of Frame Delimiter (SFD)

- **Welcher Teil eines Ethernet-Frames beschreibt das Protokoll der nächsthöheren Schicht?** Ethernettyp

- **Welcher Teil eines Ethernet-Frames benachrichtigt das Ziel über die Ankunft eines neuen Frames?** Vorwort

- **Welcher Sublayer der Sicherungsschicht kontrolliert die Netzwerkschnittstelle über Software-Treiber?** LLC 

- **Welcher Sublayer der Sicherungsschicht arbeitet mit der nächsthöheren Schichten zusammen, um Informationen über Daten an Protokolle höherer Ebenen hinzuzufügen?** LLC

- **Was ist die Funktion des MAC-Sublayers? (Wählen Sie drei Antwortmöglichkeiten aus.)**
	- Steuert den Zugriff auf die Medien
	- Prüft empfangene Bits auf Fehler
	- Verwendet CSMA/CD oder CSMA/CA zur Unterstützung der Ethernet-Technologie

## Quiz 2
- **Welche beiden Merkmale beschreiben die Ethernet-Technologie?** Es wird durch die IEEE 802.3 Standards unterstützt; Es nutzt die CSMA/CD-Zugriffsmethode

- **Welche Aussage beschreibt ein Merkmal von MAC-Adressen?** Sie müssen weltweit eindeutig sein
- **Welcher Wert wird den ersten 24 Bits einer Multicast-MAC-Adresse zugewiesen?** 01-00-5E
    
- **Was macht ein Host in einem Ethernet-Netzwerk mit einem Frame mit einer Ziel-MAC-Adresse, die nicht mit seiner eigenen MAC-Adresse übereinstimmt?** Er verwirft den Frame
    
- **Welches Netzwerkgerät trifft Weiterleitungsentscheidungen auf Grundlage der Ziel-MAC-Adresse, die im Frame enthalten ist?** Switch
    
- **Welches Netzwerkgerät sendet Daten an ein bestimmtes Ziel, basierend auf den Informationen in der MAC-Adresstabelle?** Switch
    
- **Welche Funktion oder Operation wird vom LLC-Sublayer ausgeführt?** Er kommuniziert mit oberen Protokollschichten
    
- **Was passiert mit Runt-Frames, die von einem Cisco Ethernet-Switch empfangen werden?** Der Frame wird verworfen
    
- **Welche Adressinformationen werden von einem Switch zur Erstellung seiner MAC-Adresstabelle benötigt?** Quell-Layer-2-Adresse der empfangenen Frames
    
- **Was versteht man unter Auto-MDIX?** Eine Funktion, die Ethernet-Kabeltypen erkennt
    
- **Um welche Adressart handelt es sich bei 01-00-5E-0A-00-02?** Eine Adresse, die eine bestimmte Gruppe von Hosts erreicht
    
- **Welche Aussage gilt für MAC-Adressen?** Die ersten drei Bytes entsprechen der dem Hersteller zugewiesenen OUI
    
- **Was sind die Grenzen (Minimum und Maximum) eines Ethernet-Frames?** 64 Byte; 1518 Byte
    
- **Welche beiden Funktionen oder Operationen werden vom MAC-Sublayer ausgeführt?** Er ist verantwortlich für die Media Access Control; Er fügt einen Header und Trailer zur Bildung einer OSI Layer 2 PDU hinzu
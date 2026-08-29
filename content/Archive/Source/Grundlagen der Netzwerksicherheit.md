## Sicherheitsbedrohungen und Schwachstellen
### Bedrohungsarten

Nach erfolgreichem Eindringen eines Bedrohungsakteurs (Threat Actor) können vier Arten von Bedrohungen auftreten:

- **Informationsdiebstahl:** Vertrauliche Daten werden gestohlen
- **Datenverlust und Datenmanipulation:** Daten werden beschädigt oder verändert. Daten werden verschlüsselt und gedroht den Schlüssel zu löschen, falls kein Lösegeld eingereicht wird.
- **Identitätsdiebstahl:** Persönliche Identitäten werden missbraucht
- **Dienstunterbrechung:** Netzwerkdienste werden blockiert oder gestört

### Schwachstellen (Vulnerabilities)

Der Grad der Anfälligkeit in einem Netzwerk oder Gerät. Dieses schließt Router, Switches, Desktops, Server und sogar Sicherheitsgeräte mit ein. Netzwerkgeräte, die angegriffen werden, sind in der Regel Endgeräte wie Server und Desktopcomputer. Drei primäre Schwachstellen:

**Technologische Schwachstellen**

- Schwächen des TCP/IP-Protokolls
- Schwächen des Betriebssystems
- Schwächen der Netzwerkausrüstung
- Unsichere oder alte Protokolle wie HTTP, FTP, ICMP, SNMP, SMTP

**Konfigurationsschwachstellen**

- Ungesicherte Benutzerkonten
- Leicht zu erratende Kennwörter
- Falsch konfigurierte Internetdienste
- Unsichere Standardeinstellungen
- Falsch konfigurierte Netzwerkgeräte

**Sicherheitslücken in Sicherheitsrichtlinien**

- Fehlen einer schriftlichen Sicherheitsrichtlinie
- Fehlende Authentifizierungskontinuität
- Nicht angewandte logische Zugriffskontrollen
- Nicht richtlinienkonforme Software-/Hardware-Installation
- Fehlender Notfallwiederherstellungsplan

### Physische Sicherheit

Vier Klassen physischer Bedrohungen:

**Hardware-Bedrohungen**

- Physische Schäden an Servern, Routern, Switches
- Beschädigung von Verkabelungen und Workstations

**Bedrohungen durch extreme Umgebungsbedingungen**

- Temperaturextreme (zu heiß oder kalt)
- Feuchtigkeitsextreme (zu nass oder trocken)

**Elektrische Bedrohungen**

- Spannungsspitzen
- Unzureichende Versorgungsspannung (Spannungsabfälle)
- Ungefilterte Spannungsversorgung (Rauschen)
- Totaler Stromausfall

**Bedrohungen durch unsachgemäße Wartung**

- Schlechte Handhabung elektrischer Komponenten (elektrostatische Entladung)
- Mangel an kritischen Ersatzteilen
- Fehlerhafte Verkabelung
- Unzureichende Kennzeichnung

## Netzwerkangriffe

### Arten von Malware

Malware ist bösartige (malicious) Software zum Stehlen, Beschädigen oder Stören von Daten, Hosts oder Netzwerken.

**Viren**

- Verbreiten sich durch Einfügen von Kopien in andere Programme
- Werden Teil des Programms
- Benötigen Verbreitung einer infizierten Host-Datei

**Würmer**

- Replizieren funktionsfähige Kopien von sich selbst
- Sind Standalone-Software
- Benötigen kein Host-Programm oder menschliche Unterstützung zur Verbreitung

**Trojanische Pferde**

- Sehen harmlos und legitim aus
- Vervielfältigen sich nicht durch Infektion anderer Dateien
- Verbreitung erfolgt durch Benutzerinteraktion (E-Mail-Anhang, Downloads)

> [!example] Weitere Malware-Arten
> 
> - **Ransomware** (Verschlüsselt Daten und fordert Lösegeld)
> - **Spyware** (Sammelt unbemerkt Informationen über Benutzer)
> - **Adware** (Zeigt unerwünschte Werbung an)
> - **Rootkit** (Versteckt sich im System und verschleiert andere Malware)
> - **Keylogger** (Zeichnet Tastatureingaben auf)
> - **Botnet-Malware** (Macht Rechner zum ferngesteuerten Zombie)
> - **Cryptominer** (Nutzt Ressourcen für Kryptowährungs-Mining)
> - **Fileless Malware** (Läuft im Arbeitsspeicher ohne Datei auf Festplatte)
> - **Logic Bomb** (Wird bei bestimmtem Ereignis oder Datum aktiviert)
> - **Backdoor** (Ermöglicht unbemerkten Fernzugriff)
### Kategorien von Netzwerkangriffen

**Reconnaissance-Angriffe (Aufklärungsangriffe)**

- Erkennung und Zuordnung von Systemen, Diensten oder Schwachstellen
- Verwendung von Tools wie ==nslookup, whois==
- Ermittlung von IP-Adressbereichen
- Identifizierung aktiver Adressen durch Ping

**Zugriffsangriffe (Access Attacks)**

Kategorien:

- **Passwort-Angriffe:** Brute-Force, Trojaner, Paket-Sniffer
- **Vertrauensausnutzung:** Nutzung nicht autorisierter Berechtigungen
- **Port-Umleitung:** Kompromittiertes System als Basis für weitere Angriffe
- **Man-in-the-Middle:** Bedrohungsakteur zwischen zwei Systemen zum Lesen/Ändern von Daten

**Denial of Service (DoS)-Angriffe**

- Verhindern Nutzung von Diensten durch Verbrauch von Systemressourcen
- Stören Kommunikation und führen zu Geld- und Zeitverlusten
- Leicht durchzuführen, schwer zu beseitigen
- **DDoS (Distributed DoS):** Angriff von mehreren koordinierten Quellen
    - Botnetz aus infizierten Hosts (Zombies)
    - Steuerung über Command and Control (CnC)-Programm

## Abwehr von Netzwerkangriffen

### Der tiefgreifende Verteidigungsansatz

Mehrschichtiger Sicherheitsansatz mit Kombination von Netzwerkgeräten und Diensten:

- **VPN:** Sichere Verbindungen über unsichere Netze
- **ASA Firewall:** Cisco Adaptive Security Appliance
- **IPS:** Intrusion Prevention System
- **ESA/WSA:** Email/Web Security Appliance
- **AAA Server:** Authentication, Authorization, Accounting

### Backups aufbewahren

Eine der wirksamsten Möglichkeiten zur Vermeidung von Datenverlust.

|Erwägung|Beschreibung|
|---|---|
|**Häufigkeit**|Regelmäßige Sicherungen nach Sicherheitsrichtlinie; vollständige Sicherungen monatlich/wöchentlich mit häufigen Teilsicherungen|
|**Storage**|Überprüfung der Backups zur Gewährleistung der Datenintegrität; Validierung der Wiederherstellungsverfahren|
|**Sicherheit**|Transport zu genehmigtem externen Lagerort in definierten Intervallen|
|**Validierung**|Schutz mit starken Kennwörtern; Kennwort für Wiederherstellung erforderlich|

>[!Tip]
>Die 3-2-1-Regel ist eine Backup-Strategie, die besagt, dass Sie **drei** Kopien Ihrer Daten erstellen, diese auf **zwei** verschiedenen Medientypen speichern und **eine** Kopie an einem externen Standort aufbewahren sollten. (PS. Danke Reddit :D)
### Upgrade, Update und Patch

- Antivirussoftware stets auf neuestem Stand halten
- Sicherheits-Updates von Betriebssystem-Anbietern herunterladen
- Alle anfälligen Systeme patchen
- Automatische Updates auf allen Endsystemen sicherstellen

### AAA (Authentication, Authorization, Accounting)

Das Hauptgerüst für Zugriffskontrolle auf Netzwerkgeräten.

**Authentication (Authentifizierung)**
Wer ist berechtigt, auf Netzwerk zuzugreifen?

**Authorization (Autorisierung)**
Was dürfen Personen im Netzwerk machen?

**Accounting (Abrechnung)**
Welche Aktionen führen Personen durch?

> [!info] 
> Das AAA-Konzept ähnelt der Verwendung einer Kreditkarte: Identifizierung des Benutzers, Ausgabelimit, Aufzeichnung der Ausgaben

#### Firewalls

Netzwerk-Firewalls befinden sich zwischen zwei oder mehr Netzwerken:

- Kontrollieren Datenverkehr zwischen Netzwerken
- Verhindern nicht autorisierte Zugriffe
- Ermöglichen kontrollierten Zugriff auf bestimmte Dienste

**DMZ (Demilitarisierte Zone)**

![[Archive/Attachments/Pasted image 20251209160939.png|400]]
- Spezielles Netzwerk für öffentlich zugängliche Server
- Ermöglicht Anwendung bestimmter Richtlinien
- Trennung zwischen internem Netz und öffentlichen Diensten

**Typen von Firewalls**

| Technik                              | Beschreibung                                                                                                                            |
| ------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| **Paketfilterung**                   | Verhindert/erlaubt Zugriff basierend auf IP- oder MAC-Adressen                                                                          |
| **Anwendungsfilterung**              | Verhindert/erlaubt Zugriff basierend auf Port-Nummern                                                                                   |
| **URL-Filterung**                    | Verhindert/ermöglicht Zugang basierend auf URLs oder Schlüsselwörtern                                                                   |
| **Stateful Packet Inspection (SPI)** | Eingehende Pakete müssen gültige Antworten auf interne Anfragen sein; unerwünschte Pakete werden blockiert; Erkennung von DoS-Angriffen |
|                                      |                                                                                                                                         |

### Endpunktsicherheit (Endpoint Security)

- Sichern von Endgeräten (Laptops, Desktops, Server, Smartphones, Tablets)
- Gut dokumentierte Sicherheitsrichtlinien erforderlich
- Schulung der Mitarbeiter zur richtigen Netzwerknutzung
- Einsatz von Antivirus-Software und Host-Intrusion-Prevention
- Umfassende Lösungen mit Netzwerkzugriffskontrolle

## Gerätesicherheit

Beim Installieren eines neuen Betriebssystems sind Sicherheitseinstellungen auf Standardwerte gesetzt.

**Grundlegende Sicherheitsmaßnahmen:**

- Standard-Benutzernamen und -Kennwörter sofort ändern
- Zugriff nur auf autorisierte Personen beschränken
- Nicht benötigte Dienste und Anwendungen deaktivieren/deinstallieren
- Software aktualisieren und Sicherheits-Patches installieren

### Passwörter

**Richtlinien für sichere Kennwörter:**

- Mindestens 8 Zeichen, vorzugsweise 10 oder mehr
- Komplexe Kennwörter: Groß-/Kleinbuchstaben, Zahlen, Symbole, Leerzeichen
- Keine Wörterbuchwörter, Buchstaben-/Zahlenfolgen, Benutzernamen
- Absichtlich falsch geschriebene Wörter (Smith = 5mYth)
- Kennwörter häufig ändern
- Kennwörter nicht aufschreiben oder sichtbar aufbewahren

**Passphrase**

- Satz aus vielen Wörtern mit Leerzeichen
- Leichter zu merken als einfaches Passwort
- Länger und schwerer zu erraten

### SSH aktivieren

**Schritte zur SSH-Konfiguration:**

- Eindeutigen Hostnamen konfigurieren
- IP-Domänennamen konfigurieren
- Schlüssel generieren: Empfohlene Mindestlänge: 1024 Bit
- Lokalen Datenbankeintrag erstellen
- Lokale Datenbank-Authentifizierung
- Eingehende SSH-Sitzungen aktivieren*

### Ungenutzte Dienste deaktivieren

- Deaktivierung aller nicht verwendeten Dienste
- Freigabe von Systemressourcen (CPU, RAM)
- Verhinderung der Ausnutzung durch Bedrohungsakteure

## Firewalls

### Sicherheitsmechanismen und Systeme 
- Verschlüsselungssysteme (DES, RSA, etc.)
- Digitale Signatur 
- Key Management
- Authentication: PKI, Kerberos, etc. 
- IP-Security: IPSec, VPN 
- Web Security: SSL / TLS 
- Email: PGP, S/MIME 
- Intrusion Detection 
- Schutz vor Malware (Viren, Würmer, etc.) 
- **Firewalls**

### Definition

![[Archive/Attachments/Pasted image 20251209162342.png|400]]

Eine Firewall besteht aus einer Gruppe von Netzwerkkomponenten (Hard- und Software) an der Schnittstelle zweier Netze.

Sie gewährleistet die Einhaltung von Sicherheitsrichtlinien zwischen einem zu schützenden und einem unsicheren Netz (z.B. dem Internet).

An dieser "Brandschutzmauer" entscheidet sich:

- Auf welche Dienste innerhalb des privaten Netzes zugegriffen werden kann
- Welche Dienste des nicht sicheren Netzes aus dem privaten Netz heraus nutzbar sind

### Technische Implementierung

#### Schichtenmodell

Firewalls operieren auf verschiedenen Schichten des Netzwerkmodells:

- **Anwendungsschicht:** Telnet, HTTP, SMTP, FTP, DNS → **Application Gateway**
- **Transportschicht:** Transmission Control Protocol, User Datagram Protocol → **Paketfilter**
- **Internetschicht:** Internet Protocol
- **Linkschicht:** Ethernet, X.25

### Paketfilter

Filterung auf Grund von sechs Eigenschaften:

- Pakete gehen **ein** oder **aus**
- **IP-Adressen** von Sender und Empfänger (Internetschicht)
- **Portnummern** von Sender und Empfänger (Transportschicht)
- **Protokoll** (TCP/UDP)
- **ACK-Flag** (bei TCP)
- **Richtung** (eingehend/ausgehend)

**Verfeinerung: Stateful Inspection**

- Regeln berücksichtigen den Zustand einer Verbindung
- Verbindungstabelle speichert aktive Verbindungen

#### Beispiel: Paket-Filterregeln für Interface LAN

| Nr. | Richtung | Quell-IP    | Ziel-IP     | Protokoll | Quell-Port | Ziel-Port | ACK-Flag | Aktion       | Kommentar                          |
| --- | -------- | ----------- | ----------- | --------- | ---------- | --------- | -------- | ------------ | ---------------------------------- |
| 1   | rein     | *           | 10.0.0.20   | TCP       | >1023      | 443       | egal     | Weiterleiten | https auf Webserver                |
| 2   | raus     | 10.0.0.0/24 | *           | TCP       | >1023      | 443       | egal     | Weiterleiten | https ins Internet                 |
| 3   | rein     | *           | 10.0.0.0/24 | TCP       | 443        | >1023     | ja       | Weiterleiten | https Antwort aus Internet         |
| x   | *        | *           | *           | *         | *          | *         | *        | blockieren   | Aller andere Traffic wird verboten |

> [!info] 
> Das ACK-Flag bei Regel 3 stellt sicher, dass nur Antwortpakete zu bestehenden Verbindungen durchgelassen werden, nicht aber neue Verbindungsversuche von außen.
### Application Gateway (Proxy)

![[Archive/Attachments/Pasted image 20251209162814.png|400]]

**Funktionsweise:**

- Firewall als aktiver Kommunikationspartner
- Unterbrechung der direkten Verbindung zwischen Client und Server
- Zwei separate Verbindungen: Client↔Firewall und Firewall↔Server

Es gibt zwei Arten von Proxy:
**Application Level Proxy**

- Spezifisch für jede Anwendung (HTTP, FTP, SMTP, Telnet)
- Protokollspezifische Überprüfung möglich
- Inhaltliche Filterung möglich

**Circuit Level Proxy**

- Generische Verbindungsweiterleitung
- Weniger protokollspezifische Überprüfung

### Vergleich: Paketfilter vs. Application Gateway

||Schwächen|Stärken|
|---|---|---|
|**Paketfilter**|Filterregeln nur grobkörnig einstellbar; bei vielen Regeln geht Übersicht verloren|Relativ einfache Konfiguration (neues Protokoll ⇒ neue Regeln); effiziente Verarbeitung|
|**Application Gateway**|Jeder Prozess muss einzeln konfiguriert werden; Verarbeitung eher ineffizient|Feinkörnige Filterung möglich; inhaltliche Überprüfung möglich; logische Trennung der Verbindung|

### Stateful Inspection

**Prinzip:**

- Vom LAN ins Internet können Verbindungen aufgebaut werden
- Aus dem Internet ins LAN werden Verbindungsversuche blockiert

#### TCP Verbindungsaufbau: 3-Way Handshake

![[Archive/Attachments/Pasted image 20251209163042.png|300]]

- **Schritt 1:** Client sendet SYN (SEQ=100, CTL=SYN)
- **Schritt 2:** Server antwortet mit SYN/ACK (SEQ=300, ACK=101, CTL=SYN,ACK)
- **Schritt 3:** Client bestätigt mit ACK (SEQ=101, ACK=301, CTL=ACK)

#### Stateful Inspection TCP 

![[Archive/Attachments/Pasted image 20251209163212.png|400]]
![[Archive/Attachments/Pasted image 20251209163250.png|500]]

**Connection Table:**

| Type | Internal IP | Internal Port | External IP | External Port | Status |
| ---- | ----------- | ------------- | ----------- | ------------- | ------ |
| TCP  | 60.55.33.12 | 62600         | 123.80.5.34 | 80            | OK     |

**Schritt 1-3:** Client (60.55.33.12:62600) sendet SYN an Server (123.80.5.34:80)

- Firewall trägt Verbindung in Connection Table ein
- Paket wird weitergeleitet

**Schritt 4-6:** Server antwortet mit SYN/ACK

- Firewall prüft Connection Table
- Verbindung ist vorhanden → Paket wird weitergeleitet

> [!info] 
> Bei ausgehenden Verbindungen wird standardmäßig erlaubt; bei eingehenden Paketen wird Connection Table geprüft

#### Stateful Inspection UDP

![[Archive/Attachments/Pasted image 20251209163448.png|300]]

UDP ist verbindungslos, daher:

- Filter merkt sich ausgehende UDP-Anfragen temporär
- Zeitfenster für Antworten (Timer)
- Eingehende UDP-Pakete werden mit gespeicherten Informationen abgeglichen
- Keine Übereinstimmung → Paket wird blockiert

## Firewall-Topologien

### Einfache Firewall

**Private (trusted) Network** ←→ **Firewall** ←→ **Public (untrusted) Network**

- Erlaubter ausgehender Traffic: HTTP, SMTP, DNS
- Kein Zugriff von außen nach innen

#### DMZ (Demilitarisierte Zone)

![[Archive/Attachments/Pasted image 20251209163750.png|400]]

**Drei Zonen:**

- **Private (inside):** Internes Netzwerk
- **DMZ:** Öffentlich zugängliche Server (Webserver, Mailserver)
- **Public (outside):** Internet

**Verkehrsregeln:**

- Internet → DMZ: Selektiv erlaubt
- DMZ → Internet: Selektiv erlaubt
- Internet → Private: Blockiert
- Private → Internet: Geprüft und mit wenig Einschränkungen erlaubt
- Private → DMZ: Blockiert
- DMZ → Private: Blockiert

### Arten der Umsetzung

**Hardware-Firewalls:**

- Dedizierte Appliances (Cisco ASA, Sophos, etc.)
- Router mit Firewall-Funktionalität
- Höhere Leistung für große Netzwerke

**Software-Firewalls:**

- Personal Firewalls (Norton, Windows Firewall)
- Server-basierte Lösungen
- Grafische Konfigurationsoberflächen

> [!info] Firewall OSI-Schichten 
> 
> **Layer 3 (Network):** Paketfilter - Filterung nach IP-Adressen
> 
> **Layer 4 (Transport):** Stateful Inspection - Filterung nach IP, Ports, Protokollen (TCP/UDP), Verbindungszustand (SYN, ACK)
> 
> **Layer 7 (Application):** Application Gateway/Proxy - Protokollspezifische Filterung (HTTP, FTP, SMTP), inhaltliche Überprüfung
> 
> **Next-Generation Firewalls (NGFW):** Multi-Layer (3-7) - Deep Packet Inspection, Anwendungserkennung/-kontrolle

## TCP SYN-Flooding

### DoS (Denial of Service Attack): TCP SYN Flooding

**Angriffsmethode:**

1. **Verwendung "gefälschter" IP-Adresse** (IP-Spoofing)
2. **Aufbau TCP-Verbindung mit gefälschter Absenderadresse:** 
    - Angreifer sendet SYN-Nachricht
    - Server antwortet mit SYN/ACK an gefälschte IP-Adresse
    - Da IP-Adresse nicht existiert, kommt nie die ACK-Antwort
    - Server muss bis zum Time-Out warten

3. **Wiederholung mit verschiedenen gefälschten IP-Adressen:**
    - Viele neue Verbindungsanforderungen
    - Zeit zwischen Anforderungen < Time-Out des Servers
    - Warteschlange für nicht erhaltene ACK-Antworten wird immer länger
    - Server verbraucht Systemressourcen zur Verwaltung der Warteschlange
    - Keine "normalen" Requests können mehr beantwortet werden
    - Überfüllung des Queue-Buffers

### SYN-Flood Angriff

**DoS-Angriff (Denial of Service)**

- Dienstverweigerungs-Angriff
- Blockierung von Dienst(en)
- In der Regel durch Überlastung

**Überflutung mit Verbindungsanfragen (SYN)**

- Gespoofte (gefälschte) Absender-Adressen
- Server-Queue-Buffer wird überfüllt

### Problem bei Abwehrmaßnahmen

**Schwierigkeiten:**

- Angreifer kann nicht ermittelt werden
- Keine Filterung der Pakete möglich

**Oberflächliche Lösungsansätze:**

- Größerer SYN-Queue
- Zufälliges, frühes "Droppen" von Verbindungen

> [!warning]
> Diese Maßnahmen bekämpfen nur Symptome, nicht die Ursache: Informationsspeicherung auf dem Server

### SYN-Cookies

**Konzept:**

- Spezielle TCP Server-Sequenznummern
- Enthalten kodierte Informationen zum Verbindungsaufbau
- **Keine Informationsspeicherung auf dem Server**

#### Aufbau der 32-Bit Sequenznummer

|5 Bits|3 Bits|24 Bits|
|---|---|---|
|**t mod 32**|**MSS**|**Hashfunktion aus:** Source IP-Adresse, Port / Destination IP-Adresse, Port / t|

**Komponenten:**

- **t:** 32-Bit Zeitzähler, inkrementiert alle 64 Sekunden
- **MSS:** Maximum Segment Size
- **Hash:** Berechnet aus IP-Adressen, Ports und Zeitwert

#### SYN-Cookies Ablauf

![[Archive/Attachments/Pasted image 20251209164136.png|400]]

### TCP Proxy (Alternative Lösung)

![[Archive/Attachments/Pasted image 20251209164215.png|400]]

**Funktionsweise:**

1. Host sendet SYN an Firewall
2. Firewall prüft Session → Keine Session gefunden
3. SYN-Cookie wird ausgelöst, ISN (Initial Sequence Number) berechnet
4. Firewall sendet SYN/ACK an Host zurück
5. Host sendet ACK
6. Firewall sendet SYN an Server
7. Server antwortet mit SYN/ACK
8. Firewall sendet ACK an beide Seiten
9. Verbindung hergestellt, Datentransfer möglich

**Vorteile:**

- Server wird vor SYN-Flood geschützt
- Firewall übernimmt Validierung
- SYN-Cookie-Validierung vor Serverbelastung
- MSS-Wiederherstellung möglich


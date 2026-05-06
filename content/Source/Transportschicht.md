## OSI-Modell vs TCP/IP-Modell

| OSI-Modell                            | TCP/IP-Modell                       | Protokolle                                                             |
| ------------------------------------- | ----------------------------------- | ---------------------------------------------------------------------- |
| 7. Anwendungsschicht (Application)    | Anwendungsschicht (Application)     | HTTP, HTTPS, FTP, SMTP, DNS, DHCP, TFTP, SNMP, POP3, IMAP, SSH, Telnet |
| 6. Darstellungsschicht (Presentation) |                                     | -                                                                      |
| 5. Sitzungsschicht (Session)          |                                     | -                                                                      |
| 4. Transportschicht (Transport)       | Transportschicht (Transport)        | TCP, UDP                                                               |
| 3. Netzwerkschicht (Network)          | Internetschicht (Internet)          | IP, ICMP                                                               |
| 2. Sicherungsschicht (Data Link)      | Netzzugangsschicht (Network Access) | Ethernet                                                               |
| 1. Bitübertragungsschicht (Physical)  |                                     | -                                                                      |
|                                       |                                     |                                                                        |
## Datenrolle der Transportschicht
- Verantwortlich für logische Kommunikation zwischen Anwendungen auf verschiedenen Hosts
- Bildet Link zwischen Anwendungsschicht und unteren Schichten
- Untere Schichten sind für Netzwerkübertragung verantwortlich

## Zuständigkeiten der Transportschicht

- ==Verfolgung individueller Konversationen==
- ==Segmentieren  und Multiplexing von Daten und erneutes Zusammensetzen zu Segmenten==
- Hinzufügen von Header-Informationen
- Identifizieren, Separieren und Verwalten mehrerer Unterhaltungen
- Verwendung von Segmentierung und Multiplexing für verschiedene Kommunikationsgespräche im selben Netzwerk
- Legt nicht fest, wie Zustellung oder Transport der Pakete erfolgt
- Transportschichtprotokolle geben an, wie Nachrichten zwischen Hosts übertragen werden sollen
- Verwaltung der Zuverlässigkeitsanforderungen einer Unterhaltung
- Beinhaltet zwei Protokolle: TCP und UDP

>[!info]
>Segmentierung ermöglicht Multiplexing von Konversationen: mehrere Anwendungen können das Netzwerk gleichzeitig nutzen

## Transmission Control Protocol
TCP bietet Zuverlässigkeit und Flusskontrolle.
#### Basisoperationen
- Nummerierung und Nachverfolgung von Datensegmenten von bestimmter Anwendung an bestimmten Host
- Bestätigung empfangener Daten
- Erneute Übertragung unbestätigter Daten nach bestimmtem Zeitraum
- Sequenzierung von Daten, die in falscher Reihenfolge ankommen
- Senden von Daten mit effizienter Rate, die für Empfänger akzeptabel ist

#### Eigenschaften
- Reliable (zuverlässig)
- Acknowledges data (bestätigt Daten)
- Resends lost data (sendet verlorene Daten erneut)
- Delivers data in sequenced order (liefert Daten in sequenzierter Reihenfolge)
#### Anwendungsfälle
- Wenn alle Daten eintreffen müssen
- Daten in richtiger Reihenfolge verarbeitet werden müssen

>[!Beispiele]
>- SMTP/IMAP (Email)
>- HTTP/HTTPS (World Wide Web)

## TCP Funktionen

#### Einrichten einer Verbindung

- Verbindungsorientiertes Protokoll
- Handelt permanente Verbindung (Sitzung) zwischen Quell- und Zielgeräten aus
- Baut Verbindung auf, um Datenverkehr zu übertragen

#### Zuverlässige Zustellung

- Segmente können bei Übertragung im Netzwerk beschädigt werden oder verloren gehen
- TCP stellt sicher, dass jedes Segment von Quelle am Ziel ankommt

#### Zustellung in derselben Reihenfolge

- Netzwerke können mehrere Routen mit unterschiedlichen Übertragungsraten bereitstellen
- Daten kommen möglicherweise in falscher Reihenfolge am Ziel an
- TCP ordnet Daten in ursprüngliche Reihenfolge

#### Flusskontrolle

- Netzwerk-Hosts verfügen über begrenzte Ressourcen (Speicher, Verarbeitungsleistung)
- TCP erkennt wenn Ressourcen überlastet sind
- Protokoll fordert sendende Anwendung auf, Datenflussrate zu reduzieren

## TCP Header
Es besteht aus 10 Feldern in einem 20-Byte-Header:

![[Attachments/Pasted image 20251207210654.png|500]]

- TCP ist ein Stateful-Protokoll
- Verfolgt den Status der Kommunikationssitzung
- Zeichnet auf, welche Informationen gesendet wurden
- Zeichnet auf, welche Informationen bestätigt wurden

#### Headerfelder
| TCP-Header-Feld                             | Beschreibung                                                                                                                       |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Quellport                                   | Ein 16-Bit-Feld, das zur Identifizierung der Quellanwendung anhand der Portnummer verwendet wird.                                  |
| Ziel-Port                                   | Ein 16-Bit-Feld, das zur Identifizierung der Zielanwendung anhand der Portnummer verwendet wird.                                   |
| Folgenummer                                 | Ein 32-Bit-Feld, das für die Wiederzusammenbauung von Daten verwendet wird.                                                        |
| Acknowledgement number (Bestätigungsnummer) | Ein 32-Bit-Feld, das verwendet wird, um anzuzeigen, dass Daten empfangen wurden und das nächste Byte von der Quelle erwartet wird. |
| Länge des Headers                           | Ein 4-Bit-Feld, das als "data offset-Wert" bezeichnet wird, das die Länge des TCP-Segmentheaders angibt.                           |
| Reserviert                                  | Ein 6-Bit-Feld, das für die zukünftige Verwendung reserviert ist.                                                                  |
| Steuer-Bits                                 | Control Bits (Steuer-Bits) (6 Bit) Beinhalten Bit-Codes oder Flags, die den Zweck und die Funktion des TCP-Segments angeben.       |
| Window size (Fenstergröße)                  | Ein 16-Bit-Feld, das verwendet wird, um die Anzahl der Bytes anzugeben, die vom Empfänger empfangen werden können.                 |
| Checksum (Prüfsumme)                        | Ein 16-Bit-Feld, das zur Fehlerüberprüfung des Segmentheaders und der Daten verwendet wird.                                        |
| Dringend                                    | Ein 16-Bit-Feld, das verwendet wird, um anzuzeigen, ob die enthaltenen Daten dringend sind.                                        |

## Anwendungen die TCP verwenden
- FTP (File Transfer Protocol)
- HTTP (Hypertext Transfer Protocol)
- SMTP (Simple Mail Transfer Protocol)
- SSH (Secure Shell)


## User Datagram Protocol (UDP)

- Bietet nur Grundfunktionen für Übertragung von Datensegmenten
- Sehr geringer Overhead
- Nur geringfügige Datenprüfung
- Verbindungsloses Protokoll
- ==Best-Effort Delivery-Protokoll (keine Garantie für Zustellung)==
- Keine Bestätigung, dass Daten am Ziel empfangen wurden

#### Eigenschaften
- Fast (schnell)
- Low overhead (geringer Overhead)
- Does not require acknowledgements (benötigt keine Bestätigungen)
- Does not resend lost data (sendet verlorene Daten nicht erneut)
- Delivers data as it arrives (liefert Daten wie sie ankommen)

#### Anwendungsfälle
- Anforderungs- und Antwort-Anwendungen mit minimalen Datenmengen
- Schnelles erneutes Senden möglich

>[!Beispiele]
>- VoIP (IP Telephony)
>- DNS (Domain Name Resolution)

## UDP-Funktionen
- Daten werden in der Reihenfolge rekonstruiert, in der sie empfangen werden
- Verlorene Segmente werden NICHT erneut gesendet
- Keine Sitzungseinrichtung
- Sender wird NICHT über Verfügbarkeit von Ressourcen informiert

## UDP-Header
Es besteht aus 4 Feldern in einem 8-Byte-Header:

![[Attachments/Pasted image 20251207211700.png|500]]

- Viel einfacher als TCP-Header
- Nur 4 Felder
- Benötigt 8 Bytes (64 Bit)

### Header-Felder
| UDP-Headerfeld                 | Beschreibung                                                                                                                       |
|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| Quellport                      | Ein 16-Bit-Feld, das zur Identifizierung der Quellanwendung anhand der Portnummer verwendet wird.                                  |
| Ziel-Port                      | Ein 16-Bit-Feld, das zur Identifizierung der Zielanwendung anhand der Portnummer verwendet wird.                                   |
| Länge                          | Ein 16-Bit-Feld, das die Länge des UDP-Datagramm-Headers angibt.                                                                    |
| Checksum (Prüfsumme)           | Ein 16-Bit-Feld, das für die Fehlerüberprüfung des Datagramm-Headers und der Daten verwendet wird.                                  |
## Anwendungen die UDP verwenden

#### Live-Video und Multimedia-Anwendungen

- Können Datenverlust tolerieren
- Lassen nur geringfügige oder keine Verzögerungen zu

>[!Example]
>- VoIP (Voice over IP)
>- Live-Video-Streaming
>- Video Conferencing

### Einfache Anfrage- und Antwort-Anwendungen

- Anwendungen mit einfachen Transaktionen
- Host sendet Anfrage und kann Antwort erhalten oder auch nicht

>[!Example]
>- DNS (Domain Name Service)
>- DHCP (Dynamic Host Configuration Protocol)

### Anwendungen mit eigener Zuverlässigkeit

- Unidirektionale Kommunikation
- Flusskontrolle, Fehlererkennung, Bestätigungen und Fehlerbehebung nicht erforderlich
- Oder werden von der Anwendung selbst übernommen

>[!Example]
>- SNMP (Simple Network Management Protocol)
>- TFTP (Trivial File Transfer Protocol)

## Portnummern

- TCP- und UDP-Transportschicht verwenden Portnummern zur Verwaltung mehrerer gleichzeitiger Gespräche
- Source Port (Quellportnummer) identifiziert Ursprungsanwendung auf lokalem Host
- Destination Port (Zielportnummer) identifiziert Zielanwendung auf Remote-Host

## Socket-Paare

- Quell- und Zielports werden in das Segment eingefügt
- Segmente werden in IP-Paket eingekapselt
- Kombination aus Quell-IP-Adresse und Quellport-Nummer = Socket
- Kombination aus Ziel-IP-Adresse und Zielport-Nummer = Socket
- Durch Sockets können mehrere Prozesse auf einem Client sowie mehrere Verbindungen mit einem Serverprozess voneinander unterschieden werden
## Port-Nummern-Gruppen

### Well-Known Ports (0 - 1023)

- Für allgemeine oder beliebte Dienste und Anwendungen reserviert
- Ermöglichen Clients einfache Identifizierung des zugeordneten Dienstes

| Port-Nummer | Protokoll | Anwendung                                         |
| ----------- | --------- | ------------------------------------------------- |
| 20          | TCP       | File Transfer Protocol (Daten)                    |
| 21          | TCP       | File Transfer Protocol (Steuerung)                |
| 22          | TCP       | Secure Shell (SSH)                                |
| 23          | TCP       | Telnet                                            |
| 25          | TCP       | Simple Mail Transfer Protocol (SMTP)              |
| 53          | UDP, TCP  | Domain Name Service (DNS)                         |
| 67          | UDP       | Dynamic Host Configuration Protocol (DHCP)-Server |
| 68          | UDP       | Dynamic Host Configuration Protocol (Client)      |
| 69          | UDP       | Trivial File Transfer Protocol (TFTP)             |
| 80          | TCP       | Hypertext Transfer Protocol (HTTP)                |
| 110         | TCP       | Post Office Protocol Version 3 (POP3)             |
| 143         | TCP       | Internet Message Access Protocol (IMAP)           |
| 161         | UDP       | Simple Network Management Protocol (SNMP)         |
| 443         | TCP       | Hypertext Transfer Protocol Secure (HTTPS)        |

### Registered Ports (1024 - 49151)

- Von IANA einem Antragsteller für spezifische Prozesse oder Anwendungen zugewiesen
- In erster Linie einzelne Anwendungen, die Benutzer installiert hat
- Nicht gängige Anwendungen mit Well-Known-Port-Nummer
- Beispiel: Cisco Port 1812 für RADIUS-Serverauthentifizierungsprozess

### Private und/oder dynamische Ports (49152 - 65535)

- Auch als flüchtige Ports (ephemeral ports) bezeichnet
- Betriebssystem weist Portnummern dynamisch zu bei Verbindungsinitiierung
- Dynamischer Port identifiziert Client-Anwendung bei Kommunikation
## Netstat-Befehl
- Unbekannte TCP-Verbindungen können ernsthafte Sicherheitsbedrohung darstellen
- Netstat ist wichtiges Werkzeug zur Überprüfung von Verbindungen
- es listet das verwendete Protokoll auf, die lokale Adresse und die lokale Port-Nummer, die Remote-Adresse und die Remote-Port-Nummer sowie den Verbindungsstatus

```bash
C:\> netstat
Aktive Verbindungen
Proto  Lokale Adresse        Fremdadresse              Status
TCP    192.168.1.124:3126    192.168.0.2:netbios-ssn   aufgebaut
TCP    192.168.1.124:3158    207.138.126.152:http      aufgebaut
TCP    192.168.1.124:3159    207.138.126.169:http      aufgebaut
TCP    192.168.1.124:3160    207.138.126.169:http      aufgebaut
TCP    192.168.1.124:3161    sc.msn.com:http           aufgebaut
TCP    192.168.1.124:3166    www.cisco.com:http        aufgebaut

```

## TCP Kommunikationsprozess
#### TCP-Server-Prozesse
- Jeder Serverprozess nutzt eine spezifische Portnummer.
- Ein Server kann **nicht zwei Dienste auf derselben Transportschicht mit derselben Portnummer** betreiben.
- Eine Serveranwendung mit zugewiesenem Port gilt als **offen** und verarbeitet eingehende Segmente für diesen Port.
- Client-Anfragen, die an den richtigen Socket adressiert sind, werden akzeptiert und an die Anwendung übergeben.
#### TCP-Verbindungsaufbau (Drei-Wege-Handshake)

![[Attachments/Pasted image 20251207221304.png|400]]
- **Schritt 1:** Client sendet SYN, um eine Sitzung anzufordern.
- **Schritt 2:** Server sendet SYN-ACK zur Bestätigung und fordert seinerseits eine Sitzung an.
- **Schritt 3:** Client bestätigt mit ACK.

#### Funktionen des Drei-Wege-Handshakes
- Prüft, ob das Zielgerät im Netzwerk erreichbar ist.
- Prüft, ob auf dem Zielgerät der Dienst auf der Zielportnummer aktiv ist.
- Informiert das Ziel, dass der Client eine Sitzung aufbauen möchte.
- Mechanismen für Verbindung und Sitzungsverwaltung gewährleisten die TCP-Zuverlässigkeit.

#### TCP-Sitzungsbeendigung
![[Attachments/Pasted image 20251207221351.png|400]]
- **Schritt 1:** Client sendet FIN, wenn er keine Daten mehr hat.
- **Schritt 2:** Server bestätigt mit ACK → Client-Server-Sitzung endet.
- **Schritt 3:** Server sendet FIN, um seine Sitzung zu beenden.
- **Schritt 4:** Client bestätigt mit ACK.

#### TCP-Kontrollbit-Flags (CTL)
- **URG**: dringender Zeiger signifikant
- **ACK**: Bestätigung bei Verbindungsaufbau und -abbau
- **PSH**: Push-Funktion
- **RST**: Verbindung zurücksetzen
- **SYN**: Synchronisierung der Sequenznummern (Handshake)
- **FIN**: keine weiteren Daten; für Sitzungsbeendigung genutzt

## TCP-Zuverlässigkeit 
- TCP stellt **garantierte und geordnete Zustellung** sicher.
- Segmente können unterwegs verloren gehen, TCP **erkennt Verlust** und **sendet erneut**.
- Alle Daten müssen vollständig und korrekt beim Empfänger ankommen.
- Daten müssen wieder in die **ursprüngliche Reihenfolge** zusammengesetzt werden.
- Dafür nutzt TCP **Sequenznummern** in jedem Segment.

#### Quittierungen von erhaltenen Segmenten
![[Attachments/Pasted image 20251207223059.png|500]]

- Empfangene Daten werden vom Zielhost bestätigt (ACK).
- ACK zeigt an, welches Byte als nächstes erwartet wird.
- Fehlende ACKs lösen **erneute Übertragung** der betroffenen Segmente aus.

>[!warning]
>ACK bestätigt immer "bis einschließlich vorheriges Byte
## Einfache Flusskontrolle (Stop-and-Wait)

- Sender sendet einen Block und wartet auf ACK oder Timeout.
- Bei Fehler erfolgt eine erneute Übertragung.

>[!danger]
>Nachteil ist große Wartezeiten, ineffiziente Übertragung, geringe Ausnutzung der Bandbreite.

## Selective Acknowledgment (SACK)
- Moderne Systeme verwenden optional SACK
- SACK wird während des Drei-Wege-Handshake ausgehandelt
- Empfänger kann genau angeben, welche Segmente fehlen bzw. empfangen wurden (auch wenn sie lückenhaft ankamen)
- Erlaubt effizientere Wiederherstellung bei Paketverlust

## Fenstergröße (Window Size)

- TCP passt die Menge der Daten an, die ohne ACK gesendet werden dürfen
- Das Ziel ist es, Überlastung vermeiden und Übertragung stabil halten
- Die Flusssteuerung regelt, wie viel der Empfänger verarbeiten kann
- Sliding Window erlaubt kontinuierliches Senden mehrerer Segmente

## Maximale Segmentgröße (MSS)
- MSS ist die maximale Datenmenge pro TCP-Segment, die das Zielgerät empfangen kann
- Typischer MSS-Wert: **1460 Bytes** bei IPv4
- Berechnung: Ethernet-MTU 1500 – IPv4-Header (20) – TCP-Header (20) = **1460 Bytes**
#### Überlastungsvermeidung (Congestion Avoidance)

Überlastete Router verwerfen Pakete, daher verwendet TCP Mechanismen, Timer und Algorithmen zur Vermeidung/Steuerung:
- z. B. Anpassung der Senderate
- Reduktion des Fensters bei Paketverlust
- langsamer Neustart (Slow Start)

Ziel ist es, das Netzwerk stabil halten und erneute Überlastung verhindern

#### Sliding Window (verschiebbare Fenstergröße)

Sender passt das Sendefenster dynamisch an abhängig von:
- empfangenen ACKs
- Netzwerkzustand
- Verarbeitungsfähigkeit des Empfängers

![[Attachments/Pasted image 20251207224007.png|500]]

Es ermöglicht kontinuierlichen Datenfluss, ohne auf jedes einzelne ACK zu warten.

## UDP-Kommunikation 

**UDP Geringer Overhead und Zuverlässigkeit**

- UDP ist **verbindungslos**: kein Verbindungsaufbau, kein Handshake.
- sehr geringer Overhead durch kleinen Header (8 Byte) und keine Steuer-/Managementnachrichten.
- UDP bietet keine Zuverlässigkeit: keine Bestätigungen (ACKs), keine Neuübertragung bei Verlust und kein Staukontrollmechanismus. Das ermöglicht eine schnelle, effiziente Übertragung

 **Zusammensetzung von Datagrammen**

- UDP verwendet keine Sequenznummern
- UDP kann die Reihenfolge nicht rekonstruieren
- Pakete, die in falscher Reihenfolge ankommen, werden nicht sortiert
- UDP setzt Daten einfach in der Reihenfolge zusammen, in der sie beim Empfänger eintreffen.
- Die Anwendung muss selbst sicherstellen, ob Reihenfolge wichtig ist.

**UDP-Serverprozesse und -Anfragen**

UDP-Serverprozesse verwenden wie TCP, Well-Known-Ports (0–1023) und registrierte Ports (1024–49151)

![[Attachments/Pasted image 20251207224952.png|400]]

>[!Example]
>- DNS: Port 53/UDP
>- DHCP: Port 67/68/UDP

Ein Datagramm, das an einen bestimmten Port gesendet wird,wird vom UDP-Modul empfangen, und anhand der Portnummer der richtigen Anwendung zugestellt.

**UDP-Client-Prozesse**

![[Attachments/Pasted image 20251207225105.png|400]]
- Der Client wählt **dynamisch** einen freien Port aus dem Bereich: **49152–65535** (ephemere Ports)
- Dieser Port dient als **Quellport**.
- Der Zielport ist die dem Server zugeordnete **Well-Known- oder registrierte Portnummer**.
- Sobald Quell- und Zielport festgelegt sind, werden **alle Datagramme einer Sitzung** mit **demselben Portpaar** gesendet.

>[!info]
>Der Serverprozess braucht eine feste, bekannte Portnummer, sonst wüsste der Client gar nicht, wohin er seine Anfrage schicken soll. Der Clientprozess kann irgendeinen freien Port nehmen, weil es ihm nur wichtig ist, die Antwort vom Server auf genau diesem Port wiederzubekommen

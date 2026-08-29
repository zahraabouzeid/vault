## Transport von Daten
**Frage 1**  
Welche Schicht ist für die Einrichtung einer temporären Kommunikationssitzung zwischen Quell- und Zielhost-Anwendungen verantwortlich?

⦿ Transportschicht (Transport Layer)  
○ Anwendungsschicht  
○ Sicherungsschicht (Data Link Layer)  
○ Vermittlungsschicht (Network Layer)  
○ Bitübertragungsschicht (Physical Layer)

**Frage 2**  
Was sind die drei Zuständigkeiten der Transportschicht?

☑ Multiplexing von Konversationen  
☐ Identifizieren von Frames  
☐ Identifizieren von Routinginformationen  
☑ Segmentieren von Daten und erneutes Zusammensetzen zu Segmenten  
☑ Verfolgung individueller Konversationen

**Frage 3**  
Welche Transportschicht-Protokollaussage ist wahr?

☐ TCP hat weniger Felder als UDP.  
☐ TCP ist schneller als UDP.  
⦿ UDP ist ein Best-Effort-Bereitstellungsprotokoll.  
○ UDP bietet Zuverlässigkeit.

**Frage 4**  
Welches Transportschichtprotokoll würde man für VoIP-Anwendungen verwenden?

⦿ User Datagram Protocol (UDP)  
○ Session Initiation Protocol (SIP)  
○ Transmission Control Protocol (TCP)  
○ VoIP Transfer Protocol

## TCP Überblick
**Frage 1**  
Welches Transportschichtprotokoll sorgt für eine zuverlässige Lieferung im selben Auftrag?

⦿ TCP  
○ ICMP  
○ IP  
○ UDP

<div style="page-break-after: always;"></div>


**Frage 2**  
Welche Aussage zum TCP-Header ist wahr?

⦿ Es besteht aus 10 Feldern in einem 20-Byte-Header.  
○ Es besteht aus 4 Feldern in einem 8-Byte-Header.  
○ Es besteht aus 8 Feldern in einem 16-Byte-Header.  
○ Es besteht aus 20 Feldern in einem 40-Byte-Header.

**Frage 3**  
Welche zwei Anwendungen würden das TCP-Transportschichtprotokoll verwenden?

☑ FTP  
☑ HTTP  
☐ ICMP  
☐ TFTP  
☐ VoIP

## UDP Übersicht
**Frage 1**  
Welches der folgenden ist ein zustandsloses Best-Effort-Delivery Transport Layer Protokoll?

⦿ UDP  
○ ICMP  
○ IP  
○ TCP

**Frage 2**  
Welche Aussage zum UDP-Header ist wahr?

⦿ Es besteht aus 4 Feldern in einem 8-Byte-Header.  
○ Es besteht aus 8 Feldern in einem 16-Byte-Header.  
○ Es besteht aus 10 Feldern in einem 20-Byte-Header.  
○ Es besteht aus 20 Feldern in einem 40-Byte-Header.

**Frage 3**  
Welche zwei Anwendungen würden das UDP-Transportschichtprotokoll verwenden?

☑ TFTP  
☑ VoIP  
☐ FTP  
☐ HTTP  
☐ ICMP

**Frage 4**  
Welche beiden Felder sind in einem TCP- und UDP-Header gleich?

☑ Destination port number (Zielport-Nummer)  
☐ Steuer-Bit  
☐ Sequence number (Sequenznummer)  
☑ Source port number (Quellport-Nummer)  
☐ Well-Known-Port-Nummern

<div style="page-break-after: always;"></div>

## Port Nummern
**Frage 1**  
Angenommen, ein Host mit der IP-Adresse 10.1.1.10 möchte Webdienste von einem Server unter 10.1.1.254 anfordern. Was ist das korrekte Socketpaar?

○ 1099:10.1.1.10, 80:10.1.1.254  
○ 10.1.1.10:80, 10.1.1.254:1099  
⦿ 10.1.1.10:1099, 10.1.1.254:80  
○ 80:10.1.1.10, 1099:10.1.1.254

**Frage 2**  
Welche Portgruppe enthält Portnummern für FTP-, HTTP- und TFTP-Anwendungen?

⦿ Standardisierte („well-known“) Ports  
○ Dynamische Ports  
○ Private Ports  
○ Registrierte Ports

**Frage 3**  
Welcher Windows-Befehl listet das verwendete Protokoll, die lokale Adresse und lokale Port-Nummer, die Remote-Adresse und Remote-Port-Nummer sowie den Verbindungsstatus auf?

⦿ Netstat  
○ Ipconfig /all  
○ Ping  
○ Traceroute

## TCP Kommunikationsprozess
**Frage 1**  
Welche der folgenden Optionen wären gültige Quell- und Zielports für einen Host, der eine Verbindung mit einem E-Mail-Server herstellt?

○ Quelle: 25, Ziel: 49152  
○ Quelle: 80, Ziel: 49152  
⦿ Quelle: 49152, Ziel: 25  
○ Quelle: 49152, Ziel: 80

**Frage 2**  
Welche Kontrollbit-Flags werden beim Drei-Wege-Handshake verwendet?

○ ACK und FIN  
○ FIN und RESET  
○ RESET und SYN  
⦿ SYN und ACK

**Frage 3**  
Wie viele Datenaustausche werden benötigt, um beide Sitzungen zwischen zwei Hosts zu beenden?

○ Ein Datenaustausch  
○ Zwei Datenaustausche  
○ Drei Datenaustausche  
⦿ Vier Datenaustausche  
○ Fünf Datenaustausche

<div style="page-break-after: always;"></div>


## Zuverlässigkeit und Flusskontrolle
**Frage 1**  
Welches Feld wird vom Zielhost verwendet, um Segmente in der ursprünglichen Reihenfolge wieder zusammenzusetzen?

○ Steuer-Bit  
○ Ziel-Port  
⦿ Sequenznummer  
○ Quellport  
○ Fenstergröße

**Frage 2**  
Welches Feld wird verwendet, um die Flusssteuerung bereitzustellen?

○ Steuer-Bit  
○ Ziel-Port  
○ Sequenznummer  
○ Quellport  
⦿ Fenstergröße

**Frage 3**  
Was passiert, wenn ein sendender Host einen Stau erkennt?

○ Der empfangende Host erhöht die Anzahl der Bytes, die er sendet, bevor er eine Bestätigung vom sendenden Host erhält.  
○ Der empfangende Host reduziert die Anzahl der Bytes, die er sendet, bevor er eine Bestätigung vom sendenden Host erhält.  
○ Der sendende Host erhöht die Anzahl der Bytes, die er sendet, bevor er eine Bestätigung vom Zielhost erhält.  
⦿ Der sendende Host reduziert die Anzahl der Bytes, die er sendet, bevor er eine Bestätigung vom Zielhost erhält.

## UDP Kommunikation
**Frage 1**  
Warum ist UDP für Protokolle wünschenswert, die einfache Anforderungs- und Antworttransaktionen machen?

○ Flusskontrolle  
⦿ Geringer Overhead  
○ Zuverlässigkeit  
○ Zustellung in derselben Reihenfolge

**Frage 2**  
Welche Aussage über Reassembly bei UDP-Datagrammen ist wahr?

○ UDP fügt die Daten nicht wieder zusammen.  
⦿ UDP setzt die Daten in der Reihenfolge wieder zusammen, in der sie empfangen wurden.  
○ UDP setzt die Daten mithilfe von Steuerbits wieder zusammen.  
○ UDP setzt die Daten mit Sequenznummern wieder zusammen.

**Frage 3**  
Welche der folgenden Werte wären gültige Quell- und Zielports für einen Host, der eine Verbindung mit einem DNS-Server herstellt?

○ Quelle: 53, Ziel: 49152  
○ Quelle: 1812, Ziel: 49152  
⦿ Quelle: 49152, Ziel: 53  
○ Quelle: 49152, Ziel: 1812
## Modulquiz
**Frage 1**  
Welche Transportschichtfunktion wird verwendet, um die Sitzungseinrichtung zu gewährleisten?

○ UDP-ACK-Flag  
⦿ TCP-Drei-Wege-Handshakes  
○ UDP-Sequenznummer  
○ TCP-Portnummer

**Frage 2**  
Was ist die komplette Palette von bekannten TCP- und UDP-Ports?

○ 0 to 255  
⦿ 0 bis 1.023  
○ 256–1023  
○ The combination of the source and destination sequence numbers and port numbers

**Frage 3**  
Was ist ein Socket?

○ Die Kombination aus Quell- und Ziel-IP-Adresse und Quell- und Ziel-Ethernet-Adresse  
⦿ Die Kombination einer Quell-IP-Adresse und Portnummer oder einer Ziel-IP-Adresse und Portnummer  
○ Die Kombination von Quell- und Zielsequenz und Bestätigungsnummern  
○ The combination of the source and destination sequence numbers and port numbers

**Frage 4**  
Wie verwaltet ein Netzwerkserver Anfragen von mehreren Clients für verschiedene Dienste?

○ Der Server sendet alle Anforderungen über ein Standard-Gateway.  
⦿ Jeder Anforderung wird Quell- und Zielportnummern zugewiesen.  
○ Der Server verwendet IP-Adressen, um verschiedene Dienste zu identifizieren.  
○ Jede Anforderung wird über die physische Adresse des Clients verfolgt.

**Frage 5**  
Was passiert, wenn ein Teil einer FTP-Nachricht nicht an das Ziel gesendet wird?

○ Die Nachricht geht verloren, da FTP keine zuverlässige Zustellmethode verwendet.  
○ Der FTP-Quellhost sendet eine Abfrage an den Zielhost.  
⦿ Der verlorene Teil der FTP-Nachricht wird erneut gesendet.  
○ Die gesamte FTP-Nachricht wird erneut gesendet.

**Frage 6**  
Welche Art von Anwendungen eignen sich am besten für die Verwendung von UDP?

⦿ Applications that are sensitive to delay  
○ Applications that need reliable delivery  
○ Applications that require retransmission of lost segments  
○ Applications that are sensitive to packet loss

**Frage 7**  
Was ist eine Möglichkeit, mit der das TCP-Protokoll auf erkannte Netzwerküberlastung reagiert?

⦿ Die Quelle verringert die Datenmenge, die sie überträgt, bevor sie eine Bestätigung vom Ziel erhält.  
○ Die Quelle verringert die Fenstergröße, um die Übertragungsrate vom Ziel zu verringern.  
○ Das Ziel verringert die Fenstergröße.  
○ Das Ziel sendet weniger Bestätigungsnachrichten, um die Bandbreite zu sparen.

**Frage 8**  
Welche zwei Operationen werden von TCP, aber nicht von UDP bereitgestellt?

○ Identifizieren der Anwendungen  
⦿ Acknowledging received data  
○ Identifying individual conversations  
⦿ Erneute Übermittlung von nicht bestätigten Daten  
○ Reconstructing data in the order received

**Frage 9**  
Was ist der Zweck der Verwendung einer Quellportnummer in einer TCP-Kommunikation?

○ To notify the remote device that the conversation is over  
○ To assemble the segments that arrived out of order  
⦿ To keep track of multiple conversations between devices  
○ To inquire for a nonreceived segment

**Frage 10**  
Welche zwei Flags im TCP-Header werden in einem TCP-Dreiwege-Handshake verwendet?

☑ ACK  
○ FIN  
○ PSH  
○ RST  
☑ SYN  
○ URG

**Frage 11**  
Welcher TCP-Mechanismus wird zur Vermeidung von Staus verwendet?

○ Drei-Wege-Handshakes  
○ Socket Paar  
○ Zwei-Wege-Handschlag  
⦿ Verschiebbare Fenstergröße

**Frage 12**  
Welche Aktion wird von einem Client ausgeführt, wenn eine Kommunikation mit einem Server über die Verwendung von UDP auf der Transportschicht hergestellt wird?

○ Der Client legt die Fenstergröße für die Sitzung fest.  
○ Der Client sendet einen ISN an den Server, um den 3-Wege-Handshake zu starten.  
⦿ Der Client wählt zufällig eine Quellportnummer aus.  
○ Der Client sendet ein Synchronisationssegment, um die Sitzung zu beginnen.

**Frage 13**  
Welche zwei Dienste oder Protokolle verwenden das bevorzugte UDP-Protokoll für schnelle Übertragung und geringen Overhead?

○ FTP  
⦿ DNS  
○ HTTP  
○ POP3  
⦿ VoIP

<div style="page-break-after: always;"></div>


**Frage 14**  
Welche Zahl oder Satz von Zahlen stellt einen Socket dar?

○ 01-23-45-67-89-AB  
○ 21  
⦿ 192.168.1.1:80  
○ 10.1.1.15

**Frage 15**  
Was ist eine Aufgabe für Transportschichtprotokolle?

○ Bereitstellung eines Netzwerkzugangs  
⦿ Verfolgung individueller Konversationen  
○ Bestimmung des besten Weiterleitungspfads für Pakete  
○ Übersetzung privater in öffentliche IP-Adressen
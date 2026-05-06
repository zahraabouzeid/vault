**Frage 1**
Welcher Port muss von der IANA angefordert werden, um für eine bestimmte Anwendung verwendet zu werden?

⦿ Ein registrierter Port
○ Ein privater Port
○ Ein dynamischer Port
○ Ein Quellport

**Frage 2**
Welche drei Anwendungsschichtprotokolle verwenden TCP? (Wählen Sie drei Antwortmöglichkeiten aus.)

☑ SMTP
☑ FTP
☐ SNMP
☑ HTTP
☐ TFTP
☐ DHCP

**Frage 3**
Welches Protokoll oder welcher Dienst verwendet UDP für eine Client-zu-Server-Kommunikation und TCP für die Server-zu-Server-Kommunikation?

○ HTTP
○ FTP
⦿ DNS
○ SMTP

**Frage 4**
Welches Flag des TCP-Headers wird als Antwort auf ein empfangenes FIN-Flag verwendet, um die Verbindung zwischen zwei Netzwerkgeräten zu beenden?

○ FIN
⦿ ACK
○ SYN
○ RST

**Frage 5**
Welche Informationen werden von TCP verwendet, um neu empfangene Segmente zusammenzusetzen und neu zu ordnen?

○ Port-Nummern
⦿ Sequenznummern
○ Bestätigungsnummern
○ Fragmentnummern

**Frage 6**
Welche zwei Merkmale treffen auf UDP-Sitzungen zu? (Wählen Sie zwei Antwortmöglichkeiten aus.)

☑ Zielgeräte empfangen Datenverkehr mit minimaler Verzögerung.
☐ Übertragene Datensegmente werden verfolgt.
☐ Zielgeräte setzen Nachrichten wieder zusammen und leiten sie an eine Anwendung weiter.
☑ Empfangene Daten werden nicht bestätigt.
☐ Nicht bestätigte Datenpakete werden erneut übertragen.

**Frage 7**
Welche beiden Felder sind im TCP-Header, aber nicht im UDP-Header enthalten? (Wählen Sie zwei Antwortmöglichkeiten aus.)

☑ Fenster
☐ Prüfsumme
☐ Quellport
☐ Zielport
☑ Sequenznummer

**Frage 8**
Was ist ein Merkmal von UDP?

○ UDP-Datagramme werden auf demselben Pfad übertragen und erreichen das Ziel in der richtigen Reihenfolge.
○ Anwendungen, die UDP verwenden, gelten immer als unzuverlässig.
⦿ UDP setzt die empfangenen Datagramme in der Reihenfolge zusammen, in der sie empfangen wurden.
○ UDP leitet Daten nur an das Netzwerk weiter, wenn das Ziel bereit ist, die Daten zu empfangen.

**Frage 9**
Welche drei Aussagen treffen auf UDP zu? (Wählen Sie drei Antwortmöglichkeiten aus.)

☑ UDP bietet grundlegende verbindungslose Transportschichtfunktionen.
☐ UDP bietet eine verbindungsorientierte schnelle Übertragung von Daten auf Schicht 3.
☑UDP benötigt Anwendungsschichtsprotokolle zur Fehlererkennung.
☑ UDP ist ein Protokoll mit geringem Overhead, das keine Sequenzierungs- oder Flusskontrollmechanismen bietet.
☐ UDP benötigt IP zur Fehlererkennung und Wiederherstellung.
☐ UDP bietet anspruchsvolle Flusskontrollmechanismen.

**Frage 10**
Welche beiden Anwendungen eignen sich am besten für UDP? (Wählen Sie zwei Antwortmöglichkeiten aus.)

☐ Anwendungen, die eine Datenflusssteuerung benötigen
☐ Anwendungen, die eine zuverlässige Übertragung erfordern
☑ Anwendungen, die selbständig für Zuverlässigkeit sorgen
☐ Anwendungen, die eine Neuanordnung von Segmenten erfordern
☑ Anwendungen, die einen gewissen Datenverlust tolerieren, aber keine Verzögerung dulden

**Frage 11**
Warum nutzt HTTP TCP als Protokoll der Transportschicht?

○ um die schnellstmögliche Download-Geschwindigkeit zu erreichen
○ weil HTTP ein Best-Effort-Dienst ist
○ weil Übertragungsfehler problemlos toleriert werden können
⦿ weil HTTP eine zuverlässige Übertragung erfordert

**Frage 12**
Welche wichtigen Informationen werden dem TCP/IP-Transportschicht-Header hinzugefügt, um die Kommunikation und Verbindungen mit einem Remote-Netzwerkgerät sicherzustellen?

○ Timing und Synchronisierung
⦿ Ziel- und Quellport-Nummern
○ Physische Ziel- und Quelladressen
○ Logische Netzwerkadressen für Ziel und Quelle

**Frage 13**
Welches sind drei Aufgaben der Transportschicht? (Wählen Sie drei Antwortmöglichkeiten aus.)

☑ Erfüllung der Zuverlässigkeitsanforderungen von Anwendungen (falls vorhanden)
☑ Multiplexing von mehreren Kommunikationsströmen vieler Benutzer oder Anwendungen im gleichen Netzwerk
☑ Identifizierung der Anwendungen und Dienste auf dem Client und Server, die übertragene Daten bearbeiten sollten
☐ Weiterleitung von Paketen an das Zielnetzwerk
☐ Formatierung der Daten in einem kompatiblen Format für den Empfang durch die Zielgeräte
☐ Durchführung der Fehlererkennung für Inhalte von Frames

**Frage 14**
Was macht ein Client, wenn er UDP-Datagramme senden muss?

⦿ Er sendet die Datagramme einfach.
○ Er fragt den Server, ob dieser bereit ist, Daten zu empfangen.
○ Er sendet einen vereinfachten Drei-Wege-Handshake an den Server.
○ Er sendet dem Server ein Segment mit gesetztem SYN-Flag, um die Kommunikation zu synchronisieren.

**Frage 15**
Was ist ein Beispiel für eine Netzwerkkommunikation nach dem Client-Server-Modell?

○ Ein Benutzer verwendet eMule, um eine Datei, die mit einem Freund geteilt wird, nach Kenntnis des Speicherortes herunterzuladen.
○ Eine Workstation initiiert eine ARP-Anfrage, um die MAC-Adresse eines empfangenden Host zu ermitteln.
○ Ein Benutzer druckt ein Dokument an einem Drucker aus, der mit der Workstation eines Kollegen verbunden ist.
⦿ Eine Workstation initiiert eine DNS-Anfrage, sobald der Benutzer www.cisco.com in der Adressleiste eines Webbrowsers eingibt.

**Frage 16**
Welche Art von Informationen ist in einem DNS-MX-Eintrag enthalten?

○ Der FQDN des Allas, der zur Identifizierung eines Dienstes verwendet wird.
○ Die IP-Adresse für einen FQDN-Eintrag.
⦿ Der Domänenname, der Mail-Exchange-Servern zugeordnet ist.
○ Die IP-Adresse eines autoritativen Namensservers.

**Frage 17**
Welche OSI-Schicht liefert das Interface zwischen der Anwendung und dem darunterliegenden Netzwerk zur Übertragung von Nachrichten?

⦿ Anwendungsschicht
○ Darstellungsschicht
○ Sitzungsschicht
○ Transportschicht

**Frage 18**
Was ist ein wichtiges Merkmal des Peer-to-Peer-Netzwerkmodells?

○ Wireless-Netzwerke
○ Soziale Netzwerke ohne das Internet
○ Drucken im Netzwerk unter Verwendung eines Druckservers
⦿ Freigabe von Ressourcen ohne einen dedizierten Server

**Frage 19**
Die Funktionen welcher drei Schichten des OSI-Modells werden von der Anwendungsschicht des TCP/IP-Modells ausgeführt? (Wählen Sie drei Antwortmöglichkeiten aus.)

☐ Bittübertragungsschicht
☑ Sitzungsschicht
☐ Vermittlungsschicht
☑ Darstellungsschicht
☐ Sicherungsschicht
☐ Transportschicht
☑ Anwendungsschicht

**Frage 20**
Welche beiden Protokolle können Geräte verwenden, um E-Mails zu senden? (Wählen Sie zwei Antwortmöglichkeiten aus.)

☐ HTTP
☑ SMTP
☐ POP
☐ IMAP
☐ DNS
☑ POP3

**Frage 21**
Welche Schicht des TCP/IP-Modells wird zur Datenformatierung, -komprimierung und -verschlüsselung verwendet?

○ Internetwork
○ Sitzungsschicht
○ Darstellungsschicht
⦿ Anwendungsschicht
○ Netzwerkzugriffsschicht

**Frage 22**
Welches Anwendungsschichtprotokoll verwendet Nachrichtentypen wie GET, PUT und POST?

○ DNS
○ DHCP
○ SMTP
⦿ HTTP
○ POP3

**Frage 23**
Eine Fertigungsunternehmen abonniert bestimmte gehostete Dienste bei seinem ISP. Die benötigten Dienste umfassen gehostete Web-, Dateiübertragungs- und E-Mail-Dienste. Welche Protokolle repräsentieren diese drei wichtigen Anwendungen? (Wählen Sie drei Antwortmöglichkeiten aus.)

☑ FTP
☑ HTTP
☐ DNS
☐ SNMP
☐ DHCP
☑ SMTP

**Frage 24**
In welchem Netzwerkmodell würden eDonkey, eMule, BitTorrent, Bitcoin und LionShare verwendet?

⦿ Peer-to-Peer
○ Client/Server
○ Master-Slave
○ Point-to-Point

**Frage 25**
Was haben die Client-Server- und Peer-to-Peer-Netzwerkmodelle gemeinsam?

○ Beide Modelle verfügen über dedizierte Server.
⦿ Beide Modelle unterstützen Geräte in der Rolle des Servers und des Clients.
○ Bei beiden Modellen müssen TCP/IP-basierte Protokolle verwendet werden.
○ Beide Modelle werden nur in kabelgebundenen Netzwerkumgebungen verwendet.

**Frage 26**
Welche Aussage über das Server-Message-Block-Protokoll trifft zu?

○ Verschiedene SMB-Nachrichtentypen haben unterschiedliche Formate.
⦿ Clients bauen eine langfristige Verbindung zum Server auf.
○ SMB-Nachrichten können eine Sitzung nicht authentifizieren.
○ SMB verwendet das FTP-Protokoll für die Kommunikation.

**Frage 27**
Worin besteht ein Vorteil von SMB gegenüber FTP?

○ Nur SMB ermöglicht Datenübertragungen in beide Richtungen.
○ Nur SMB stellt zwei simultane Verbindungen zum Client her, so dass die Datenübertragung beschleunigt wird.
○ SMB ist zuverlässiger als FTP, da SMB TCP und FTP UDP verwendet.
⦿ SMB-Clients stellen eine langfristige Verbindung mit dem Server her.

**Frage 28**
Welches Netzwerkmodell wird verwendet, wenn ein Autor ein Dokument für ein Kapitel auf den Dateiserver eines Buchverlags hochlädt?

○ Peer-to-Peer
○ Master-Slave
⦿ Client-Server
○ Punkt-zu-Punkt

**Frage 29**
Welche drei Schichten des OSI-Modells bieten Netzwerkdienste an, die denen der Anwendungsschicht des TCP/IP-Modells entsprechen? (Wählen Sie drei Antworten.)

☐ Bitübertragungsschicht
☑ Sitzungsschicht
☐ Transportschicht
☑ Anwendungsschicht
☑ Darstellungsschicht
☐ Sicherungsschicht

**Frage 30**
Welches Szenario beschreibt eine Funktion, die von der Transportschicht zur Verfügung gestellt wird?

○ Ein Student ruft mit einem VoIP-Telefon aus dem Klassenzimmer zu Hause an. Die eindeutige Kennung des Telefons ist eine Transport-Layer-Adresse, die es erlaubt, ein anderes Netzwerk-Gerät im selben Netzwerk zu kontaktieren.
○ Ein Student spielt einen kurzen Web-basierten Film mit Ton ab. Der Film und der Ton werden im Transportschicht-Header kodiert.
⦿ Ein Student hat zwei Browser-Fenster geöffnet, um auf zwei Websites zuzugreifen. Die Transportschicht sorgt dafür, dass die korrekte Webseite an das richtige Browser-Fenster gesendet wird.
○ Ein Mitarbeiter eines Unternehmens greift auf einen Webserver zu, der sich im Unternehmensnetzwerk befindet. Die Transportschicht formatiert die Webseite derart, dass sie richtig erscheint, unabhängig davon, welches Gerät zur Anzeige der Webseite verwendet wird.

**Frage 31**
Ein PC, der mit einem Webserver kommuniziert, hat eine TCP-Windowgröße von 6.000 Byte beim Senden von Daten und eine Paketgröße von 1.500 Byte. Welches Byte der Informationen bestätigt der Webserver, nachdem er zwei Datenpakete vom PC erhalten hat?

⦿ 3001
○ 4501
○ 3
○ 1500

**Frage 32**
Ein Client erstellt ein Paket, das an einen Server übertragen werden soll. Der Client fordert den POP3-Dienst an. Welche Nummer wird als Zielportnummer im sendenden Paket eingesetzt?

⦿ 110
○ 443
○ 161
○ 80
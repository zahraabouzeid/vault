## OSI- und TCP/IP-Modell

Die oberen drei Schichten des OSI-Modells (Anwendungsschicht, Darstellungsschicht und Sitzungsschicht) definieren die Funktionen der TCP/IP-Anwendungsschicht.
#### TCP/IP Application Layer Protocols
- Geben Format und Steuerungsinformationen für Internetkommunikation an
- Werden von Quell- und Zielgeräten während Kommunikationssitzung verwendet
- Müssen auf beiden Hosts kompatibel sein für erfolgreiche Kommunikation

| Protokoll | Port                    | Transport | Funktion                          |
| --------- | ----------------------- | --------- | --------------------------------- |
| DNS       | 53                      | TCP, UDP  | Namensauflösung                   |
| DHCP      | 67(Server) / 68(Client) | UDP       | IP-Zuweisung                      |
| HTTP      | 80, 8080                | TCP       | Webinhalte                        |
| HTTPS     | 443                     | TCP       | Sichere Webinhalte                |
| SMTP      | 25                      | TCP       | E-Mail senden                     |
| POP3      | 110                     | TCP       | E-Mail empfangen                  |
| IMAP      | 143                     | TCP       | E-Mail empfangen (synchronisiert) |
| FTP       | 20/21                   | TCP       | Dateiübertragung                  |
| TFTP      | 69                      | UDP       | Einfache Dateiübertragung         |
| SSH       | 22                      | TCP       | Sichere Remote-Verbindung         |

## Anwendungsschicht (Application Layer)

- Stellt Schnittstelle zwischen Anwendungen und dem zugrunde liegenden Netzwerk bereit
- Ermöglicht Datenaustausch zwischen Programmen auf Quell- und Ziel-Hosts
- Bekannte Protokolle: ==HTTP, HTTPS, FTP, TFTP, SMTP, DNS, DHCP, IMAP==

## Darstellungsschicht (Presentation Layer)

Drei Hauptfunktionen:

- **Formatierung:** Daten vom Quellgerät in kompatibles Format für Zielgerät umwandeln
- **Komprimierung:** Daten komprimieren (Sender) und dekomprimieren (Empfänger)
- **Verschlüsselung:** Daten für Übertragung verschlüsseln und bei Empfang entschlüsseln

## Sitzungsschicht (Session Layer)

- Erstellt und verwaltet Dialoge zwischen Quell- und Zielanwendungen
- Handhabt Informationsaustausch zum Initiieren und Aufrechterhalten von Sitzungen
- Startet unterbrochene oder inaktive Sitzungen neu

## Peer-to-Peer

### Client-Server-Modell

- **Client:** Gerät, das Informationen anfordert
- **Server:** Gerät, das auf Anfrage antwortet
- Client- und Server-Prozesse befinden sich in der Anwendungsschicht
- Anwendungsschicht-Protokolle beschreiben Format von Anfragen und Antworten

**Typische Beispiele**
* E-Mail (SMTP, IMAP, POP3)
* Webservices (HTTP/HTTPS)
* Datenbankserver

**Einsatz, wenn sinnvoll**
* Wenn zentrale Kontrolle, Sicherheit, konsistente Datenbestände und einfache Wartung wichtig sind.
* Große Netzwerke und Unternehmen.
### Peer-to-Peer-Netzwerke (P2P)

- Zwei oder mehr Computer über Netzwerk verbunden
- Können Ressourcen (Drucker, Dateien) ohne dedizierten Server teilen
- Jedes angeschlossene Endgerät (Peer) kann als Server und Client fungieren
- Rollen von Client und Server werden pro Anfrage festgelegt

**Einsatz, wenn sinnvoll**
* Wenn keine aufwändige Serverinfrastruktur vorhanden ist.
* Für schnelle, dezentrale Ressourcenteilung in kleinen Gruppen oder beim Filesharing.
### Peer-to-Peer-Anwendungen

- Ermöglichen Gerät, als Client und Server in derselben Kommunikation zu fungieren
- Einige nutzen Hybridsystem: Peers greifen auf Index-Server zu, um Ressourcenstandort zu finden

**Bekannte P2P-Netzwerke:**
- BitTorrent: Teilt einzelne Dateiteile über viele Peers (Schwarm-Prinzip)
- Gnutella: Jeder Benutzer stellt komplette Dateien für andere bereit
- Direct Connect
- eDonkey
- Freenet
- Weitere Clients: μTorrent, qBitTorrent, Deluge, eMule, DC++

**Typischer Einsatz**
Gemeinsame Nutzung großer Dateien, effiziente Lastverteilung, dezentrale Ressourcenteilung.
## Web- und E-Mail-Protokolle

### HTTP und HTML

**URL-Verarbeitung (Beispiel: http://www.cisco.com/index.html)**

**Schritt 1:** Browser interpretiert URL-Teile

- http (Protokoll/Schema)
- www.cisco.com (Servername)
- index.html (angeforderter Dateiname)

**Schritt 2:** Browser fragt DNS-Server nach IP-Adresse

- Initiiert HTTP-GET-Anfrage für index.html-Datei

**Schritt 3:** Server sendet HTML-Code als Antwort

**Schritt 4:** Browser entschlüsselt HTML und formatiert Seite fürs Browser-Fenster

### HTTP-Nachrichtentypen

- **GET:** Client-Anfrage für Daten (z.B. HTML-Seiten)
- **POST:** Lädt Datendateien zum Webserver hoch (z.B. Formulardaten)
- **PUT:** Lädt Ressourcen oder Inhalte zum Webserver hoch (z.B. Bilder)

> [!warning] 
> HTTP ist kein sicheres Protokoll. Für sichere Kommunikation über Internet sollte HTTPS verwendet werden.
>- **HTTPS (Port 443)** nutzt SSL (Secure Socket Layer) zur Verschlüsselung
>- Authentifiziert die Website, mit der Verbindung hergestellt wird
>- Daten werden verschlüsselt, bevor sie über das Netzwerk übertragen werden

### E-Mail-Protokolle

E-Mail ist eine Store-and-Forward-Methode zum Senden, Speichern und Abrufen elektronischer Nachrichten.

![[Archive/Attachments/Pasted image 20251208230927.png|400]]

**Verwendete Protokolle:**

**SMTP (Simple Mail Transfer Protocol)**

- Zum Senden von E-Mails
- Port 25 (TCP)
- Client SMTP-Prozess verbindet sich mit Server SMTP-Prozess
- Server legt Nachricht in lokalem Konto ab oder leitet sie weiter
- Bei Nichtverfügbarkeit: SMTP speichert Nachrichten zur späteren Zustellung

**POP3 (Post Office Protocol)**

![[Archive/Attachments/Pasted image 20251208231018.png|400]]

- Zum Empfangen von E-Mails
- Port 110 (TCP)
- Lädt E-Mails vom Server zum Client herunter
- Nachrichten werden dann vom Server gelöscht
- POP-Server hört TCP-Port 110 ab, begrüßt den Client und tauscht Befehle und Antworten, bis die Verbindung endet
- Keine zentrale Speicherung, daher für Firmen mit Backup-Bedarf ungeeignet

> [!info] 
> POP speichert keine Nachrichten nicht empfohlen für kleine Unternehmen mit zentralisierter Backup-Lösung

**POP3 eignet sich für:**

- Einzelne Geräte
- Offline-Zugriff
- Begrenzte Serverspeicherkapazität

**IMAP (Internet Message Access Protocol)**

- Zum Empfangen von E-Mails
- Port 143 (TCP)
- Lädt Kopien der Nachrichten zum Client herunter
- Originalnachrichten bleiben auf Server bis zur manuellen Löschung
- Server synchronisiert Löschaktionen

**IMAP eignet sich für:**

- Mehrere Geräte
- Zentralisierte Verwaltung
- Synchronisation über verschiedene Clients
- Geschäftliche Umgebungen mit Backup-Anforderungen

## Email Agents

Im E-Mail-System gibt es verschiedene Komponenten, die als "Agents" bezeichnet werden:

### Mail User Agent (MUA)

![[Archive/Attachments/Pasted image 20251208230753.png|400]]
- Client-Anwendung zum Lesen und Schreiben von E-Mails
- Beispiele: Outlook, Thunderbird, Webmail-Clients
- Ermöglicht Benutzern das Verfassen, Senden und Empfangen von Nachrichten

### Mail Transfer Agent (MTA)
![[Archive/Attachments/Pasted image 20251208230826.png|400]]
- Verantwortlich für die Weiterleitung von E-Mails zwischen Servern
- Nutzt SMTP-Protokoll
- Prüft, ob Empfänger lokal ist oder an anderen Server weitergeleitet werden muss
- Kommuniziert mit anderen MTAs über das Internet

> [!info] 
> Der MTA fragt sich: "Ist der Empfänger in meiner Liste der Empfänger? Nein. Weiterleiten der E-Mail an einen anderen Server"

### Mail Delivery Agent (MDA)
![[Archive/Attachments/Pasted image 20251208230850.png|400]]
- Zuständig für die finale Zustellung der E-Mail ins Postfach des Empfängers
- Legt die Nachricht im Mailbox des Empfängers ab
- Arbeitet eng mit dem MTA zusammen
## IP-Adressierungsdienste

### DNS (Domain Name System)

- Wandelt numerische IP-Adressen in einfache, erkennbare Namen um
- Beispiel: www.cisco.com statt 198.133.219.25
- Definiert automatisierten Dienst zur Zuordnung von Ressourcennamen zu Netzwerkadressen

**DNS-Ablauf:**

- **Schritt 1:** Client gibt URL in Browser ein
- **Schritt 2:** Browser fragt DNS-Server nach IP-Adresse für www.cisco.com
- **Schritt 3:** DNS-Server antwortet mit IP-Adresse 198.133.219.25
- **Schritt 4:** Client nutzt IP-Adresse zur Verbindung und sendet HTTP-Anfrage

### DNS-Eintragstypen (Resource Records)

- **A:** IPv4-Adresse eines Endgeräts
- **AAAA:** IPv6-Adresse eines Endgeräts (Quad-A)
- **NS:** Autoritativer Nameserver
- **MX:** Mail-Exchange-Eintrag

>[!info] 
>Wenn ein Client eine Anfrage stellt, prüft der DNS-Server zunächst seine eigenen Einträge zur Namensauflösung. Kann er den Namen nicht mit seinen gespeicherten Einträgen auflösen, kontaktiert er andere Server zur Namensauflösung.
### DNS-Hierarchie

DNS nutzt hierarchisches System zur Namensauflösung:

- Jeder DNS-Server verwaltet spezifische Datenbankdatei
- Verantwortlich nur für eigene Zone
- Bei Anfragen außerhalb der Zone: Weiterleitung an anderen DNS-Server

**Top-Level-Domains:**

- .com (Unternehmen/Industrie)
- .org (Non-Profit-Organisation)
- .au (Australien)

| Bestandteil | Bedeutung |
|-------------|-----------|
| http:// | Protokoll/Schema (Hypertext Transfer Protocol) |
| www | Subdomain (Webserver) |
| cisco | Domain-Name (Organisation) |
| com | Top-Level-Domain (Unternehmensbereich) |
| /index.html | Pfad/Dateiname (angeforderte Ressource) |

>[!info]
www.cisco.com. Das ist der Root (Punkt)
Der Punkt am Ende wird normalerweise nicht geschrieben, ist aber technisch immer da


**nslookup-Befehl**
- Ermöglicht manuelle Abfrage von DNS-Servern
- Zur Auflösung von Hostnamen
- Fehlerbehebung bei Namensauflösungsproblemen
- Überprüfung des Status von Nameservern
- 
```bash
C:\Users> nslookup
Default Server:  dns-sj.cisco.com
Address:  171.70.168.183
> www.cisco.com
Server:  dns-sj.cisco.com
Address:  171.70.168.183
Name:    origin-www.cisco.com
Addresses:  2001:420:1101:1::a
            173.37.145.84
Aliases:  www.cisco.com
```
## DHCP (Dynamic Host Configuration Protocol)

### DHCP-Funktion

- Automatisiert Zuweisung von IPv4-Adressen, Subnetzmasken, Gateways und anderen Parametern
- Dynamische Adressierung im Vergleich zu statischer Adressierung
- Client kontaktiert DHCP-Server und fordert Adresse an
- Server wählt Adresse aus konfiguriertem Adresspool und weist sie (least) dem Host zu

### DHCP-Verwendung

**DHCP wird verwendet für:**

Allgemeine Hosts (Endbenutzergeräte)

**Statische Adressierung wird verwendet für:**

Netzwerkgeräte (Gateway-Router, Switches, Server, Drucker)

> [!info] 
> DHCPv6 bietet ähnliche Dienste für IPv6-Clients, stellt aber keine Standard-Gateway-Adresse bereit, diese wird nur über Router-Advertisement-Nachricht des Routers bezogen (RA)

### DHCP-Prozess (DORA)

**Schritt 1: DHCPDISCOVER**
Client sendet Broadcast-Nachricht zur Identifikation verfügbarer DHCP-Server

**Schritt 2: DHCPOFFER**
DHCP-Server antwortet mit Lease-Angebot an Client

**Schritt 3: DHCPREQUEST**
Client sendet Anfrage mit explizitem Server und akzeptiertem Lease-Angebot

**Schritt 4: DHCPACK**
Server bestätigt, dass Lease finalisiert wurde

**Schritt 5: Lease-Erneuerung**
- Lease muss vor Ablauf erneuert werden
- Client fordert Verlängerung beim DHCP-Server an

**Alternative: DHCPNAK**
- Falls Angebot nicht mehr gültig: Server antwortet mit negativer Bestätigung
- Prozess beginnt erneut mit DHCPDISCOVER

> [!info] 
> DHCPv6 nutzt ähnliche Nachrichten: SOLICIT, ADVERTISE, INFORMATION REQUEST, REPLY

### DHCPv6-Nachrichten:

* **SOLICIT** Client sucht Server
* **ADVERTISE** Server bietet Konfiguration an
* **INFORMATION REQUEST** Client fragt Details an
* **REPLY** Server bestätigt Zuweisung
## Dateifreigabedienste

### FTP (File Transfer Protocol)

FTP ermöglicht Datenübertragungen zwischen Client und Server.

**Schritt 1:** Client stellt erste Verbindung für Kontrollverkehr her
- TCP-Port 21
- Besteht aus Client-Befehlen und Server-Antworten
- Für die Sitzung selbst

**Schritt 2:** Client stellt zweite Verbindung für Datentransfer her
- TCP-Port 20
- Wird bei jedem Datentransfer neu erstellt
- Für den eigentlichen Datenverkehr

>[!info]
>Zwei separate Verbindungen verhindern, dass sich Steuerungsbefehle und Datenübertragung gegenseitig blockieren


**Schritt 3:** Datentransfer in beiden Richtungen möglich

- Download (Pull): Client lädt Daten vom Server
- Upload (Push): Client lädt Daten zum Server hoch

### SMB (Server Message Block)

- Client/Server-Request-Response-Dateifreigabeprotokoll
- Server stellen eigene Ressourcen Clients im Netzwerk zur Verfügung
- Hauptsächlich in **Microsoft-Netzwerken** eingesetzt

**Nachrichtenformat:**
- Header mit fester Größe
- Parameter mit variabler Größe

**Drei Funktionen von SMB-Nachrichten:**
- Sitzungen starten, authentifizieren und beenden
- Datei- und Druckerzugriff steuern
- Anwendung ermöglichen, Nachrichten an/von anderem Gerät zu senden/empfangen

**Plattformunterstützung:**
- **Windows:** Standardmäßig eingebaut (seit Windows 2000 über TCP/IP und DNS)
- **Linux/UNIX:** Über SAMBA
- **macOS:** Unterstützt ebenfalls SMB

**Unterschied zu FTP:**
- Clients stellen **dauerhafte Verbindung** zu Servern her (nicht einmalige Übertragung)
- Nach Verbindungsaufbau: Client kann auf Server-Ressourcen wie auf lokale Ressourcen zugreifen
- Ressourcen erscheinen als **lokal verfügbar**

### TFTP (Trivial File Transfer Protocol)

- Einfaches, verbindungsloses Dateiübertragungsprotokoll
- Port 69 (UDP)
- **Best-Effort-Protokoll:** Keine bestätigte Dateizustellung
- Weniger aufwändig als FTP
- Keine Authentifizierung erforderlich

**Anwendungsfälle:**
- Booten von Geräten über Netzwerk
- Firmware-Updates
- Einfache Dateiübertragungen in geschützten Netzwerken
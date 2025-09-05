## 8.1 Eigenschaften der Vermittlungsschicht
#### Die Vermittlungsschicht  
![[Attachments/Pasted image 20250622212234.png|500]]
Daten von einem Host zum anderen über **Netzwerkgrenzen hinweg weiterleiten**

**Wichtige Protokolle der Schicht 3**
- **IPv4**, **IPv6**  zentrale Netzwerkprotokolle
- **OSPF**  Routingprotokoll
- **ICMP** – Benachrichtigungsprotokoll (z. B. für Fehler oder Echo-Requests)

**Grundfunktionen der Vermittlungsschicht**
- **1. Adressierung**
	Jeder Host erhält eine **eindeutige IP-Adresse**, um im Netzwerk identifizierbar zu sein

- **2. Kapselung**
    - Die Transportschicht-PDU (z. B. TCP-Segment) wird in ein **IP-Paket** verpackt
    - Es wird ein **IP-Header** mit Quell- und Zieladresse hinzugefügt
    - **Wird vom Sender-Host** durchgeführt
- **3. Routing**
    - Pakete werden über **Router** an Zielnetzwerke weitergeleitet
    - Router entscheiden anhand ihrer Routing-Tabelle über den **besten Pfad**
    - Jeder Router unterwegs = ein **Hop**
- **4. Entkapselung**
    - **Ziel-Host** prüft IP-Adresse im Header
    - Wenn sie übereinstimmt → IP-Header wird entfernt
    - **PDU wird an Transportschicht (Layer 4)** übergeben

**Unterschied zur Transportschicht**
- **Vermittlungsschicht (Layer 3)**: kümmert sich um **Host-zu-Host-Kommunikation über Netzwerke**
- **Transportschicht (Layer 4)**: kümmert sich um **Dienst-zu-Dienst-Kommunikation innerhalb der Hosts**
- Layer 3 betrachtet **nicht den Inhalt** der Daten nur Zieladresse & Weiterleitung
#### IP-Kapselung  
![[Attachments/Pasted image 20250622212318.png|500]]
- IP kapselt das Segment der Transportschicht.  
- IP kann entweder ein IPv4- oder IPv6-Paket verwenden, ohne die Schicht-4-Segmente zu beeinflussen.  
- Das IP-Paket wird von allen Schicht-3-Geräten untersucht, während es das Netzwerk durchläuft. 
  Vermittlungsschicht-Kapselung  
- Die IP-Adressierung ändert sich nicht von der Quelle zum Ziel.  

> [!info] NAT ändert die Adressierung, wird aber in einem späteren Modul behandelt.

#### IP – Internet Protocol  
- IETF: RFC 791 (v4), RFC 8200 (v6)  
- Unzuverlässige, bestmögliche Zustellung  
- Adressierung  
	- Netzwerkschnittstelle  
- Routing-Tabellen  
	- Routing basierend auf längstem Präfix-Matching  

## 8.1.3 Merkmale des IP-Protokolls
- **Verbindungslos**
    - Kein Verbindungsaufbau vor dem Senden (→ **kein Handshake**)
    - Jedes Paket wird **einzeln gesendet**, ohne Rückmeldung
- **Unzuverlässig, aber effizient**
    - IP garantiert **keine Zustellung, Reihenfolge oder Fehlerfreiheit**
    - **Zuverlässigkeit wird durch höhere Schichten** (z. B. TCP) bereitgestellt
- **Medienunabhängig**
    - Funktioniert über **alle Übertragungsmedien** hinweg
    - Z. B. **Kupfer, Glasfaser, Funk/Wireless** – kein Einfluss auf IP selbst
- → **Ziel von IP**: minimale Steuerung, maximale Weiterleitungsgeschwindigkeit über beliebige Netze hinweg

## 8.1.4 Verbindungslos
- **IP ist verbindungslos**
    - Es wird **keine feste Verbindung** zwischen Sender und Empfänger aufgebaut
    - Kein **Handshake**, keine Vorab-Kommunikation
- **Analogie**:
    - Wie ein **Brief ohne Vorankündigung** versendet wird
    - Absender schickt Daten, ohne zu wissen, ob der Empfänger bereit oder überhaupt erreichbar ist
- **Folge**:
    - Keine Garantie für Zustellung, Erreichbarkeit oder Reaktion
    - **Einfaches, schnelles Kommunikationsmodell ohne Verbindungsmanagement**
## 8.1.5 Beste Leistung
- **Kein Verbindungsaufbau nötig**
    - IP benötigt **keine Steuerfelder** im Header zur Verbindungspflege
    - → **Geringer Overhead**, hohe Geschwindigkeit
- **"Best-Effort"-Prinzip**
    - IP **garantiert keine Zustellung**
    - Absender weiß nicht:
        - Ob das Zielgerät **existiert oder erreichbar** ist
        - Ob das Paket **ankommt, gelesen oder verarbeitet** wird
- **Ergebnis**:
    - IP ist **schnell und einfach**, aber **nicht zuverlässig**
    - Zuverlässigkeit muss durch **höhere Schichten** (z. B. TCP) ergänzt werden
## 8.1.6 Medienunabhängig  
IP ist unzuverlässig:  
- Es kann nicht zugestellte oder beschädigte Pakete nicht verwalten oder reparieren.  
- IP kann nach einem Fehler keine erneute Übertragung durchführen.  
- IP kann nicht in der Reihenfolge falsch angeordnete Pakete neu ordnen.  
- IP muss sich für diese Funktionen auf andere Protokolle verlassen.  

IP ist medienunabhängig:  
- IP kümmert sich nicht um den Typ des Frames, der auf der Datenverbindungsschicht erforderlich ist, oder um den Medientyp auf der physischen Schicht.  
- IP kann über jeden Medientyp gesendet werden: Kupfer, Glasfaser oder drahtlos. 

## 8.2 IPv4 Paket
![[Attachments/Pasted image 20250622213502.png|500]]
- **Adressknappheit**
    - IPv4 bietet nur ca. **4,3 Milliarden eindeutige Adressen**
    - Nicht ausreichend für den weltweiten Anstieg von **IP-Geräten**, **Always-on-Verbindungen**, etc.

- **Fehlende Ende-zu-Ende-Konnektivität**
    - **NAT (Network Address Translation)** wird eingesetzt, um Adressknappheit zu umgehen
    - Führt dazu, dass die **interne IP-Adresse verborgen** bleibt
    - Problematisch für Dienste, die eine **direkte Verbindung zwischen Endgeräten** benötigen (z. B. P2P, VoIP)

- **Erhöhte Komplexität**
    - NAT war ursprünglich als **Übergangslösung** gedacht
    - Führt zu **mehr Latenz**, **mehr Fehlerquellen** und **erschwerter Netzwerkdiagnose**
    - Unterschiedliche NAT-Implementierungen erschweren Standardisierung und Wartung
## 8.3 IPv6 Paket
- **128-Bit-Adressen statt 32-Bit**  
    → IPv6 bietet ca. **340 Sextillionen Adressen**  
    → Im Vergleich: IPv4 hat ~4,3 Milliarden Adressen

- **Vereinfachter Header**  
    → Weniger Felder im IPv6-Header  
    → **Effizientere Verarbeitung** durch Router und Geräte

- **Kein NAT nötig**  
    → **Jedes Gerät kann eine öffentliche Adresse erhalten**  
    → **Ende-zu-Ende-Konnektivität** wird wieder möglich  
    → Wegfall von NAT-Problemen bei P2P, VoIP, etc.

- **Skalierbarkeit für die Zukunft**  
    → IPv6 wurde **gezielt** entwickelt, um den Anforderungen **wachsender Netzwerke** gerecht zu werden

- **Zusätzliche Features (implizit)**  
    → Verbesserte Autokonfiguration  
    → Integrierte Sicherheitsfunktionen (IPsec verpflichtend in IPv6)  
    → Besseres Multicast-Handling
    
#### IPv6-Header vs IPv4 Header
![[Attachments/Pasted image 20250622213837.png|500]]

![[Attachments/Pasted image 20250622213848.png|500]]
- **Kompakter Aufbau:**  
    → Der **IPv6-Header ist fester Bestandteil** jedes Pakets und besteht aus **nur 8 Feldern** (40 Bytes).  
    → Im Vergleich: IPv4-Header hat **12 Felder + optionale Felder**, kann bis zu 60 Bytes groß werden.
- **Weggefallene IPv4-Felder:**
    - Header-Prüfsumme (wird von unteren Schichten übernommen)
    - Fragmentierung (wird bei IPv6 durch separate Extension Header geregelt)
    - Options-Feld (durch Extension Header ersetzt)

- **Vereinfachte Verarbeitung:**  
    → Router können den Header **schneller analysieren**, da weniger Felder vorhanden sind und die Struktur **nicht variabel** ist.
    
- **Erweiterbarkeit:**  
    → **Extension Header** ermöglichen zusätzliche Funktionen (z. B. Fragmentierung, Routing, Authentifizierung), **ohne den Basis-Header zu verändern**.

Diese Vereinfachung war zentral für die **Performance-Ziele** von IPv6, insbesondere im Hinblick auf skalierbare, zukunftssichere Netzwerke.

#### IP-Adressen  
 - IPv4: 32 Bit, Punkt-Schreibweise, Dezimal  ↔  1.2.3.4  
 - IPv6: 128 Bit, RFC-5952-basierte Schreibweise, Hexadezimal  ↔  2001:db8::1  

#### Netzwerk- und Host-Anteile, Die Subnetzmaske  
- Vergleich der IP-Adresse und der Subnetzmaske  
- Die 1en in der Subnetzmaske identifizieren den Netzwerkanteil, während die  

#### UND-Verknüpfung (ANDing)  

- Logisches UND ist der Vergleich von zwei Bits.  
- Die UND-Verknüpfung zwischen der IP-Adresse und der Subnetzmaske ergibt die Netzwerkadresse.  

#### Die Präfixlänge  
- Kurzschreibweise zur Identifizierung einer Subnetzmaske.  
- Es ist die Anzahl der auf 1 gesetzten Bits in der Subnetzmaske.  
- Wird in "Slash-Notation" geschrieben, ein "/" gefolgt von der Anzahl der auf 1 gesetzten Bits.  
#### Netzwerk, Host- und Broadcast-Adresse
#### Spezielle IPv4-Adressen  
- Loopback-Adressen: 127.0.0.0 /8 oder 127.0.0.1 bis 127.255.255.254  
- Link-Local-Adressen oder automatische private IP-Adressen (APIPA)  
	- 169.254.0.0 /16 oder  
	- 169.254.0.1 bis 169.254.255.254  
- TEST-NET-Adressen  
	- 192.0.2.0/24 oder 
	- 192.0.2.0  bis 192.0.2.255  
#### Klassenbasierte Adressierung (veraltet)  
#### Klassenlose Adressierung  
- Der formale Name ist Classless Inter-Domain Routing (CIDR, ausgesprochen "Zider").  
- Erstellte einen neuen Satz von Standards, der es Dienstanbietern ermöglicht, IPv4-Adressen auf jeder Bit-Grenze (Präfixlänge) zuzuweisen, anstatt nur durch eine Klasse A, B oder C Adresse.  

#### Öffentliche und private IPv4-Adressen  

**Private Adressen:**  
- 10.0.0.0/8 oder 10.0.0.0 bis 10.255.255.255  
- 172.16.0.0/12 oder 172.16.0.0 bis 172.31.255.255  
- 192.168.0.0/16 oder 192.168.0.0 bis 192.168.255.255  
Private Adressen können nicht über das Internet geroutet werden  
#### Grenzen von IPv4  
- Erschöpfung der IP-Adressen  
- Ausweitung der Internet-Routing-Tabellen  
- Fehlende End-to-End-Konnektivität  
#### IPv6-Adressdarstellung  
Hextette – 4 hexadezimale Ziffern = 16 binäre Ziffern  
#### IPv6-Adressen kanonische Darstellung (RFC 5952)  
- Vollständiges Format:  2001:0db8:0000:0000:456c:346f:54d6:e931  
- Kleinbuchstaben  
- Führende Nullen in 16-Bit-Feldern weglassen: 2001:db8:0:0:456c:346f:54d6:e931  
- Nachfolgende 0-Felder mit :: kürzen  
	- Mindestens zwei Felder  
		- Die längste Gruppe nachfolgender Felder  
		- Gleich lang? → die am weitesten links stehende  
- 2001:db8::456c:346f:54d6:e931  
#### Motivation für kanonische Darstellung  
- Adressen werden in Konfigurationsdateien und anderen Dateien geschrieben  
- Textsuche  
	- Klartext statt fehleranfälliger regulärer Ausdrücke  
- Vergleich für Personen ohne Netzwerkkentnisse erleichtern  
	- Z.B. Richter  
- Nachteile: Nicht alle Geräte unterstützen die kanonische Darstellung  
	- Einschließlich Cisco-Geräte  

## 8.4 Wie ein Host routet  
#### Weiterleitungsentscheidung des Hosts  
- Pakete werden immer an der Quelle erstellt.  
- Jedes Host-Gerät erstellt seine eigene Routing-Tabelle.  
- Ein Host kann Pakete an Folgendes senden:  
	- **Sich selbst** – 127.0.0.1 (IPv4), ::1 (IPv6)  
	- **Lokale Hosts** – Ziel befindet sich im selben LAN  
	- **Entfernte Hosts** – Geräte befinden sich nicht im selben LAN  
- Das Quellgerät bestimmt, ob das Ziel lokal oder entfernt ist  
- Bestimmungsmethode:  
	- IPv4 – Quelle verwendet ihre eigene IP-Adresse und Subnetzmaske zusammen mit der Ziel-IP-Adresse  
	- IPv6 – Quelle verwendet die Netzwerkadresse und das Präfix, das vom lokalen Router angekündigt wird  
- Lokaler Verkehr wird an die Host-Schnittstelle ausgegeben, um von einem Zwischengerät verarbeitet zu werden.  
- Entfernter Verkehr wird direkt an das Standard-Gateway im LAN weitergeleitet.  
#### Standard-Gateway  
Ein Router oder Layer-3-Switch kann ein Standard-Gateway sein.  

Merkmale eines Standard-Gateways (DGW):  
- Es muss eine IP-Adresse im gleichen Bereich wie der Rest des LANs haben.  
- Es kann Daten vom LAN akzeptieren und ist in der Lage, Datenverkehr vom LAN weiterzuleiten. 
- Es kann zu anderen Netzwerken routen.  

Wenn ein Gerät kein Standard-Gateway oder ein fehlerhaftes Standard-Gateway hat, kann sein Datenverkehr das LAN nicht verlassen.  
#### Ein Host routet zum Standard-Gateway  
- Der Host kennt das Standard-Gateway (DGW) entweder statisch oder durch DHCP in IPv4.  
- IPv6 sendet das DGW durch eine Router Solicitation (RS) oder kann manuell konfiguriert werden.  
- Ein DGW ist eine statische Route, die eine letzte Zufluchtsroute in der Routing-Tabelle sein wird.
- Alle Geräte im LAN benötigen das DGW des Routers, wenn sie Datenverkehr remote senden möchten.  

#### IP Routing Tabelle
`netstat -r` oder `route print` zeigt:

- **Schnittstellenliste**: MAC-Adressen & Nummern aller Netzwerkadapter
- **IPv4-Routentabelle**: Bekannte IPv4-Routen (direkt, lokal, Standardroute)
- **IPv6-Routentabelle**: Bekannte IPv6-Routen (direkt, lokal, Standardroute)
## 8.5 Einführung ins Routing  
#### Router-Paket-Weiterleitungsentscheidung  
![[Attachments/Pasted image 20250622215146.png]]
Was passiert, wenn der Router den Frame vom Host-Gerät empfängt?  
1. Das Paket trifft auf der Gigabit Ethernet 0/0/0-Schnittstelle des Routers R1 ein. R1 entfernt den Layer-2-Ethernet-Header und Trailer.  
2. Router R1 untersucht die Ziel-IPv4-Adresse des Pakets und sucht nach der besten Übereinstimmung in seiner IPv4-Routing-Tabelle. Der Routeneintrag zeigt an, dass dieses Paket an Router R2 weitergeleitet werden soll.  
3. Router R1 kapselt das Paket in einen neuen Ethernet-Header und Trailer und leitet das Paket an den nächsten Hop-Router R2 weiter.  

**R1-Routing-Tabelle**  

| Route                   | Nächster Hop oder Ausgangsschnittstelle |
| ----------------------- | --------------------------------------- |
| 192.168.10.0 /24        | G0/0/0                                  |
| 209.165.200.224/30      | G0/0/1                                  |
| 10.1.1.0/24             | über R2                                 |
| Standardroute 0.0.0.0/0 | über R2                                 |

#### IP-Router-Routing-Tabelle  
Es gibt drei Arten von Routen in der Routing-Tabelle eines Routers:  
- **Direkt verbunden** – Diese Routen werden automatisch vom Router hinzugefügt, vorausgesetzt, die Schnittstelle ist aktiv und hat eine Adressierung.  
- **Entfernt** – Dies sind die Routen, zu denen der Router keine direkte Verbindung hat und die gelernt werden können:  
	- Manuell – mit einer statischen Route  
	- Dynamisch – durch Verwendung eines Routing-Protokolls, damit die Router ihre Informationen miteinander teilen  
- **Standardroute** – diese leitet den gesamten Datenverkehr in eine bestimmte Richtung, wenn es keine Übereinstimmung in der Routing-Tabelle gibt  

#### Statisches Routing  
![[Attachments/Pasted image 20250622215220.png|500]]

![[Attachments/Pasted image 20250622215229.png|500]]
Merkmale statischer Routen:  
- Müssen manuell konfiguriert werden  
- Müssen manuell vom Administrator angepasst werden, wenn es eine Änderung in der Topologie gibt  
- Gut für kleine, nicht redundante Netzwerke  
- Oft in Verbindung mit einem dynamischen Routing-Protokoll zur Konfiguration einer Standardroute verwendet  

#### Dynamisches Routing  
![[Attachments/Pasted image 20250622215407.png|500]]
![[Attachments/Pasted image 20250622215416.png|500]]
Dynamische Routen entdecken automatisch:  
- Entfernte Netzwerke  
- Aktuelle Informationen  
- Den besten Pfad zum Ziel  
- Neue beste Pfade, wenn es eine Topologieänderung gibt  
Dynamisches Routing kann auch statische Standardrouten mit den anderen Routern teilen.  

#### Einführung in eine IPv4-Routing-Tabelle  
![[Attachments/Pasted image 20250622215516.png]]

Der Befehl **show ip route** zeigt folgende Routenquellen an:  

- **L** - Direkt verbundene lokale Schnittstellen-IP-Adresse  
- **C** - Direkt verbundenes Netzwerk  
- **S** - Statische Route wurde manuell von einem Administrator konfiguriert  
- **O** - OSPF: Open Shortest Path First  
- **D** - EIGRP: Enhanced Interior Gateway Routing Protocol

Dieser Befehl zeigt Arten von Routen an:  

- Direkt verbunden – C und L  
- Entfernte Routen – O, D, usw.  
- Standardrouten – S*  

## Quiz 1

- **Welche OSI-Schicht sendet Segmente, die in einem IPv4- oder IPv6-Paket gekapselt werden?** Transportschicht (Transport Layer)
    
- **Welche Schicht ist verantwortlich für die Übernahme eines IP-Pakets und dessen Vorbereitung für die Übertragung über das Kommunikationsmedium?** Sicherungsschicht (Data Link Layer)
    
- **Wie lautet der Begriff für die Aufteilung eines IP-Pakets beim Weiterleiten auf ein Medium mit einer kleineren MTU?** Fragmentierung
    
- **Welche Zustellmethode übernimmt keine Garantie für eine fehlerfreie Übermittlung des Pakets.** Beste Leistung

## Quiz 2
- **Welche drei Optionen benennen Hauptprobleme im Zusammenhang mit IPv4?** Erschöpfung des IP-Adressbereichs, Erhöhte Netzwerkkomplexität und Ausdehnung der Internet-Routingtabelle, Fehlende Ende-zu-Ende-Konnektivität
    
- **Welche beiden Optionen sind Verbesserungen von IPv6 im Vergleich zu IPv4?** Vergrößerter IP-Adressraum, Die Verwendung eines einfacheren Headers ermöglicht eine verbesserte Paketbearbeitung
    
- **Welche Aussage über den IP-Header ist korrekt?** Er besteht aus 40 Oktetten; Er enthält acht Header-Felder.
    
- **Welche Aussage über den Header des IP-Pakets ist korrekt?** Das Feld „Hop Limit“ ersetzt das Feld „Time to Live“ bei IPv4

## Quiz 3
- **Welche Aussage über Host-Weiterleitungsentscheidungen ist richtig?**  
    Lokale Hosts können sich ohne die Notwendigkeit eines Routers gegenseitig erreichen.
    
- **Welche Aussage über Standard-Gateways ist richtig?**  
    Die Standard-Gateway-Adresse ist die IP-Adresse des Routers im lokalen Netzwerk.
    
- **Welche beiden Befehle können auf einem Windows-Host eingegeben werden, um seine IPv4- sowie IPv6-Routing-Tabelle anzuzeigen?**  
    netstat -r  
    route print

## Quiz 4
- **Welcher Befehl wird auf einem Cisco IOS-Router verwendet, um die Routing-Tabelle anzuzeigen?** show ip route
    
- **Welche Bedeutung hat der Code „O“ neben einer Route in der Routingtabelle?** Eine Route, die dynamisch über OSPF gelernt wurde
    
- **Dieser Routentyp wird auch als Gateway of Last Resort bezeichnet.** Standardroute
    
- **Wählen Sie eine Eigenschaft einer statischen Route.** Sie muss manuell konfiguriert werden
    
- **Richtig oder falsch? Ein Router kann mit einer Kombination aus statischen Routen und einem dynamischen Routingprotokoll konfiguriert werden.** Richtig
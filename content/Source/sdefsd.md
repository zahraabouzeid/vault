## Email Protokolle und Agents

## Email Protokolle

E-Mail nutzt zur Kommunikation mehrere Protokolle, die sich auf die Anwendungsschicht beziehen:

**Grundprinzip:** E-Mail ist eine Store-and-Forward-Methode. Nachrichten werden in Datenbanken auf Mail-Servern gespeichert, und Clients kommunizieren mit diesen Servern zum Senden und Empfangen.

### Verwendete Protokolle

**SMTP (Simple Mail Transfer Protocol)**

- Zum Versenden von E-Mails
- Port 25 (TCP)
- Verbindungsorientiert

**POP3 (Post Office Protocol Version 3)**

- Zum Empfangen von E-Mails
- Port 110 (TCP)
- Lädt Nachrichten herunter und löscht sie vom Server

**IMAP (Internet Message Access Protocol)**

- Zum Empfangen von E-Mails
- Port 143 (TCP)
- Behält Nachrichten auf dem Server



## E-Mail Versandprozess

#### Ablauf beim Versenden

**Schritt 1:** Absender sendet E-Mail über MUA mit SMTP

**Schritt 2:** MTA des Absender-Servers empfängt die Nachricht

**Schritt 3:** MTA prüft, ob Empfänger lokal ist

- Falls ja → Weiterleitung an lokalen MDA
- Falls nein → Weiterleitung an MTA des Zielservers via SMTP

**Schritt 4:** MTA des Empfänger-Servers empfängt die Nachricht

**Schritt 5:** MDA legt die E-Mail im Postfach des Empfängers ab

## E-Mail Empfangsprozess

### POP3-Ablauf

**Schritt 1:** Client verbindet sich mit Port 110 des Mail-Servers

**Schritt 2:** Server sendet Begrüßung

**Schritt 3:** Client authentifiziert sich

**Schritt 4:** Client lädt E-Mails herunter

**Schritt 5:** E-Mails werden vom Server gelöscht

> [!warning] POP3 speichert keine Nachrichten auf dem Server – nicht empfehlenswert für zentralisierte Backup-Lösungen

### IMAP-Ablauf

**Schritt 1:** Client verbindet sich mit IMAP-Server

**Schritt 2:** Kopien der Nachrichten werden heruntergeladen

**Schritt 3:** Originalnachrichten bleiben auf Server gespeichert

**Schritt 4:** Bei Löschung durch Benutzer synchronisiert Server und löscht die Nachricht

> [!info] IMAP ermöglicht Zugriff von mehreren Geräten auf dieselben E-Mails, da alles auf dem Server verbleibt

## SMTP-Details

### SMTP-Nachrichtenformat

SMTP-Nachrichten bestehen aus:

- **Header:** Empfänger- und Absender-E-Mail-Adresse
- **Body:** Eigentlicher Nachrichteninhalt

### SMTP-Funktionsweise

- Client SMTP-Prozess verbindet sich mit Server SMTP-Prozess auf Port 25
- Nach Verbindungsaufbau sendet Client die E-Mail an den Server
- Server legt Nachricht entweder in lokalem Konto ab oder leitet sie weiter
- Falls Ziel-Server nicht verfügbar: SMTP speichert Nachricht zur späteren Zustellung (Spooling)

## Protokollvergleich

|Protokoll|Funktion|Port|Transportprotokoll|Speicherverhalten|
|---|---|---|---|---|
|SMTP|E-Mail senden|25|TCP|-|
|POP3|E-Mail empfangen|110|TCP|Löscht vom Server|
|IMAP|E-Mail empfangen|143|TCP|Behält auf Server|

## Anwendungsfälle


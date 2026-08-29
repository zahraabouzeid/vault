## Symmetrische Verschlüsselung

Sender und Empfänger verwenden denselben Schlüssel zum Ver- und Entschlüsseln.

- Schlüsselanzahl für n Teilnehmer: n × (n-1) / 2
- Jede Person benötigt n-1 Schlüssel
- Problem: sicherer Schlüsselaustausch ist schwierig
- Vorteil: sehr schnell, geeignet für große Datenmengen

Wichtige Algorithmen:

- AES (Advanced Encryption Standard): aktueller Standard, Schlüssellängen 128, 192 oder 256 bit, gilt als sicher
- DES / 3DES: veraltet, unsicher (DES: 56 bit Schlüssel)
- ChaCha20: modernes symmetrisches Verfahren, oft in TLS verwendet

## Asymmetrische Verschlüsselung

Jede Person besitzt ein Schlüsselpaar: einen öffentlichen Schlüssel (public key) und einen privaten Schlüssel (private key).

- Der öffentliche Schlüssel darf frei verteilt werden.
- Der private Schlüssel muss geheim gehalten werden.
- Was mit dem öffentlichen Schlüssel verschlüsselt wird, kann nur mit dem privaten Schlüssel entschlüsselt werden und umgekehrt.
- Vorteil: kein sicherer Schlüsselaustausch notwendig
- Nachteil: deutlich langsamer als symmetrische Verschlüsselung

Einsatz:

- Sender verschlüsselt mit dem öffentlichen Schlüssel des Empfängers
- Empfänger entschlüsselt mit seinem privaten Schlüssel

## RSA

RSA ist das bekannteste asymmetrische Verschlüsselungsverfahren.

Schlüsselerzeugung:

- Wähle zwei große Primzahlen p und q
- Modulus N = p × q
- Öffentlicher Schlüssel: (N, e)
- Privater Schlüssel: (N, d)

Sicherheit:

- Basiert auf der Schwierigkeit, N in seine Primfaktoren p und q zu zerlegen (Faktorisierungsproblem)
- Eine erfolgreiche Faktorisierung von N bedeutet, dass der private Schlüssel berechnet werden kann und das Verfahren gebrochen ist
- Faktorisierung kann verhindert werden durch sehr große Schlüssellängen
- Empfohlene Schlüssellänge laut BSI: mindestens 3072 bit
- RSA-1024 gilt als unsicher

Warum ist eine PIN-Eingabe bei der Schlüsselerzeugung notwendig?

- Die PIN verschlüsselt den privaten Schlüssel lokal
- Schutz vor Diebstahl des privaten Schlüssels
- Zwei-Faktor-Sicherheit: Schlüsseldatei + PIN

Blocklänge bei RSA:

- Die Blocklänge sollte möglichst groß gewählt werden, da kleinere Blöcke anfälliger für Angriffe sind
- Maximale Blocklänge: kleiner als N (Modulus)

Wichtige weitere asymmetrische Algorithmen:

- ECC (Elliptic Curve Cryptography): moderner, kürzere Schlüssel bei gleicher Sicherheit, empfohlen
- ECDSA: ECC-basierte digitale Signatur
- Diffie-Hellman / ECDH: Schlüsselaustauschverfahren

## Hybride Verschlüsselung

Hybride Verschlüsselung kombiniert die Vorteile beider Verfahren: die Geschwindigkeit der symmetrischen und die sichere Schlüsselübertragung der asymmetrischen Verschlüsselung.

Ablauf:

1. Sender erzeugt einen zufälligen symmetrischen Schlüssel (Session Key)
2. Nachricht wird symmetrisch mit dem Session Key verschlüsselt
3. Der Session Key wird asymmetrisch mit dem öffentlichen Schlüssel des Empfängers verschlüsselt
4. Beides (verschlüsselte Nachricht + verschlüsselter Session Key) wird gesendet
5. Empfänger entschlüsselt den Session Key mit seinem privaten Schlüssel
6. Empfänger entschlüsselt die Nachricht mit dem Session Key

Wird bei TLS/SSL, PGP und S/MIME eingesetzt.

## Hashverfahren

Eine Hashfunktion bildet eine beliebig lange Eingabe auf einen Hashwert fester Länge ab. Der Hashwert wird auch als Fingerabdruck, Prüfsumme oder Message Digest bezeichnet.

#### Eigenschaften einer sicheren Hashfunktion:

- Deterministisch: gleiche Eingabe ergibt immer denselben Hashwert
- Einwegfunktion (Preimage Resistance): aus dem Hashwert kann die ursprüngliche Eingabe nicht rekonstruiert werden
- Kollisionsresistenz (Collision Resistance): es soll praktisch unmöglich sein, zwei verschiedene Eingaben zu finden, die denselben Hashwert erzeugen
- Second Preimage Resistance: zu einer gegebenen Eingabe soll es praktisch unmöglich sein, eine zweite andere Eingabe mit demselben Hashwert zu finden
- Lawineneffekt (Avalanche Effect): kleinste Änderung an der Eingabe (z.B. ein einziges Bit) verändert den Hashwert komplett und unvorhersehbar
- Schnell berechenbar: der Hash muss effizient berechnet werden können
- Feste Ausgabelänge: unabhängig von der Länge der Eingabe hat der Hash immer dieselbe Länge

#### Wozu dient ein Hashwert?

- Integritätsprüfung: Prüfen, ob eine Datei oder Nachricht verändert wurde
- Digitale Signaturen: nicht die gesamte Nachricht, sondern nur ihr Hash wird signiert (effizienter)
- Passwortspeicherung: Passwörter werden niemals im Klartext gespeichert, sondern nur als Hashwert
- Message Authentication Code (MAC): Sicherstellung der Integrität bei der Datenübertragung, z.B. in TLS

#### Wichtige Algorithmen:

- SHA-256 / SHA-3: aktuell sicher, empfohlen (SHA-256 erzeugt 256-bit-Hashwert)
- MD5: veraltet, kollisionsbehaftet, unsicher nicht mehr verwenden
- SHA-1: veraltet, kollisionsbehaftet, unsicher nicht mehr verwenden

#### Angriff auf den Hashwert (Geburtstagsangriff):

- Der Angreifer sucht nicht nach einer bestimmten Kollision, sondern nach irgendeiner Kollision zwischen zwei beliebigen Dokumenten
- Bei kurzer signifikanter Bitlänge (z.B. 16 oder 32 bit) ist es realistisch, eine Kollision zu erzeugen
- Bei 64 bit dauert es bereits sehr lange
- Bei 128 bit und mehr wird ein Angriff praktisch unmöglich
- Fazit: Je kürzer der Hashwert, desto leichter ist ein Kollisionsangriff daher sind MD5 (128 bit) und SHA-1 (160 bit) heute nicht mehr sicher genug

#### Passwortspeicherung und Salting:

Ohne Salting: Wird ein Passwort einfach gehasht gespeichert (z.B. hash("passwort123")), kann ein Angreifer mit vorberechneten Tabellen (Rainbow Tables) den Hash sofort einem bekannten Passwort zuordnen. Gleiche Passwörter erzeugen immer denselben Hash, das ist erkennbar.

#### Rainbow Table Angriff:

Eine Rainbow Table ist eine vorberechnete Tabelle, die für eine große Menge bekannter Passwörter den jeweiligen Hashwert enthält. Ein Angreifer, der eine Passwort-Datenbank mit Hashwerten stiehlt, schlägt jeden Hash einfach in der Tabelle nach und kennt sofort das Passwort, ohne einen einzigen Hash selbst berechnen zu müssen.

#### Beispiel Rainbow Table (ohne Salt):

```
Passwort         Hash (MD5)
"passwort123"    482c811da5d5b4bc6d497ffa98491e38
"hallo"          5d41402abc4b2a76b9719d911017c592
"qwerty"         d8578edf8458ce06fbc5bb76a58c5ca4
```

Der Angreifer sieht in der Datenbank den Hash 482c811d... und weiß sofort: das Passwort ist "passwort123". Gleiche Passwörter erzeugen immer denselben Hash. Wenn zwei Nutzer dasselbe Passwort haben, sind ihre Hashwerte identisch, das ist für den Angreifer sofort erkennbar.

#### Salting: 
Vor dem Hashen wird dem Passwort ein zufälliger, einzigartiger Wert (Salt) hinzugefügt.

```
salt = "xK92mP"
gespeicherter_hash = hash(passwort + salt)
```

Die Rainbow Table wurde für "passwort123" berechnet, nicht für "passwort123xK92mP". Für jeden möglichen Salt müsste eine eigene Rainbow Table existieren, das ist mit vertretbarem Aufwand unmöglich.

- Gleiche Passwörter erzeugen durch unterschiedliche Salts unterschiedliche Hashwerte
- Der Salt muss nicht geheim sein, er muss nur einzigartig pro Nutzer sein
- Ohne den Salt des jeweiligen Nutzers ist eine Rainbow Table nutzlos
- Empfohlene Verfahren für Passwortspeicherung: bcrypt, Argon2, PBKDF2 diese sind bewusst rechenintensiv, um Brute-Force-Angriffe zu verlangsamen

## Digitale Signatur

Eine digitale Signatur bestätigt die Authentizität und Integrität eines Dokuments.

Erstellung der Signatur (durch Sender):

1. Hashwert des Dokuments berechnen
2. Hashwert mit dem privaten Schlüssel des Senders verschlüsseln (= Signatur)
3. Dokument + Signatur senden

Überprüfung der Signatur (durch Empfänger):

1. Signatur mit dem öffentlichen Schlüssel des Senders entschlüsseln → ergibt den gesendeten Hash
2. Hashwert des empfangenen Dokuments selbst berechnen
3. Vergleich: sind beide Hashwerte gleich, ist die Signatur gültig

Warum wird vor der Signatur eine PIN benötigt? Der private Schlüssel ist PIN-geschützt; ohne PIN kann der private Schlüssel nicht verwendet werden.

Eigenschaften einer digitalen Signatur:

- Authentizität: beweist, wer das Dokument signiert hat
- Integrität: beweist, dass das Dokument nicht verändert wurde
- Nicht-Abstreitbarkeit (Non-Repudiation): der Sender kann die Signatur nicht leugnen

Was bedeutet es, wenn zwei Hashwerte gleich sind? Das Dokument wurde nicht verändert und stammt vom angegebenen Sender.

## Zertifikate

Ein digitales Zertifikat verbindet einen öffentlichen Schlüssel mit einer Identität (Person, Organisation, Server).

Inhalt eines Zertifikats:

- Name des Inhabers
- Öffentlicher Schlüssel des Inhabers
- Aussteller (Certification Authority)
- Gültigkeitszeitraum
- Digitale Signatur der CA

Wozu dienen Zertifikate? Sie stellen sicher, dass ein öffentlicher Schlüssel tatsächlich zur angegebenen Person oder Organisation gehört und nicht ausgetauscht wurde (Schutz vor Man-in-the-Middle-Angriffen).

Standard: X.509

## Certification Authority (CA)

Eine Certification Authority ist eine vertrauenswürdige Instanz, die digitale Zertifikate ausstellt und signiert.

- Die CA prüft die Identität des Antragstellers
- Sie signiert das Zertifikat mit ihrem eigenen privaten Schlüssel
- Browser und Betriebssysteme vertrauen einer Liste bekannter Root-CAs
- Hierarchisches System: Root-CA → Intermediate-CA → End-Entity-Zertifikat

Public Key Infrastructure (PKI): das Gesamtsystem aus CAs, Zertifikaten, Sperrlisten (CRL) und Prozessen zur Verwaltung öffentlicher Schlüssel.

Wie kann die Echtheit einer Signatur / eines Zertifikats überprüft werden? Indem das Zertifikat der ausstellenden CA herangezogen wird und die Signatur der CA mit deren öffentlichem Schlüssel verifiziert wird.

## Zertifikatsantrag (CSR)

Ein CSR (Certificate Signing Request) ist ein Antrag, den eine Person oder Organisation an eine Certification Authority (CA) schickt, um ein signiertes Zertifikat zu erhalten.

Inhalt eines CSR:
- Öffentlicher Schlüssel des Antragstellers
- Identitätsdaten (Name, Organisation, Domain usw.)
- Digitale Signatur mit dem eigenen privaten Schlüssel als Echtheitsbeweis

Ablauf:
1. Antragsteller erzeugt ein Schlüsselpaar (public key + private key)
2. Antragsteller erstellt einen CSR mit dem öffentlichen Schlüssel und seinen Identitätsdaten
3. CSR wird an die CA geschickt
4. CA prüft die Identität des Antragstellers
5. CA signiert den öffentlichen Schlüssel und stellt das fertige Zertifikat aus
6. Antragsteller verwendet das Zertifikat zusammen mit seinem privaten Schlüssel

Der private Schlüssel verlässt dabei niemals den Antragsteller, die CA bekommt ihn nie zu sehen.

## TLS / SSL

SSL (Secure Socket Layer) ist der Vorgänger von TLS (Transport Layer Security). TLS 1.0 entspricht SSL 3.1. SSL und TLS werden oft synonym verwendet, aktuell sollte aber nur TLS 1.2 oder TLS 1.3 eingesetzt werden.

TLS ist ein hybrides Verschlüsselungsverfahren und arbeitet in zwei Phasen.

Phase 1: Handshake

Ziel: Authentifizierung und Aushandlung eines gemeinsamen symmetrischen Schlüssels (Master Secret).

#### Ablauf:

1. Client sendet client_hello mit unterstützten Cipher Suites und einer Zufallszahl (RNc)
2. Server antwortet mit server_hello, wählt Cipher Suite und sendet eigene Zufallszahl (RNs)
3. Server sendet sein Zertifikat (inkl. öffentlichem Schlüssel)
4. Server fordert optional ein Client-Zertifikat an
5. Client prüft das Server-Zertifikat
6. Client sendet ggf. sein Zertifikat
7. Client erzeugt Pre-Master-Secret (PMS), verschlüsselt es mit dem öffentlichen Schlüssel des Servers und sendet es
8. Beide Seiten berechnen das Master Secret aus PMS, RNc und RNs
9. Ab jetzt: verschlüsselte Kommunikation mit dem Master Secret als symmetrischem Schlüssel

#### Datenübertragung

- HTTP-Daten werden in Record Protocol Units gleicher Größe aufgeteilt
- Für jedes Paket wird ein Message Authentication Code (MAC) berechnet
- Paket + MAC werden symmetrisch mit dem Master Secret verschlüsselt
- Übertragung per TCP/IP

#### Aktuelle empfohlene Cipher Suites (TLS 1.3):

- TLS_AES_256_GCM_SHA384
- TLS_CHACHA20_POLY1305_SHA256
- Schlüsselaustausch: ECDHE (Ephemeral Elliptic Curve Diffie-Hellman)

## OpenSSL

OpenSSL ist ein weit verbreitetes Open-Source-Tool zur Arbeit mit kryptographischen Funktionen über die Kommandozeile.

> [!info]
> PEM (Privacy Enhanced Mail) ist ein Dateiformat zur Speicherung kryptographischer Objekte wie Schlüssel, Zertifikate oder CSRs. Es ist textbasiert, Base64-kodiert und erkennbar an Kopf- und Fußzeilen wie `-----BEGIN CERTIFICATE-----`. Dateiendungen sind .pem, .crt, .cer oder .key — der Inhalt entscheidet, nicht die Endung. Das Gegenstück ist DER: dasselbe Objekt, aber binär kodiert und nicht als Text lesbar.

#### Schlüsselpaar erzeugen (RSA, 4096 bit)

```bash
openssl genrsa -out private.pem 4096
```

#### Öffentlichen Schlüssel extrahieren

```bash
openssl rsa -in private.pem -pubout -out public.pem
```

#### Zertifikat selbst signieren (self-signed)

```bash
openssl req -new -x509 -key private.pem -out cert.pem -days 365
```

#### Datei verschlüsseln (symmetrisch, AES-256)

```bash
openssl enc -aes-256-cbc -in klartext.txt -out verschluesselt.bin
```

#### Datei entschlüsseln

```bash
openssl enc -d -aes-256-cbc -in verschluesselt.bin -out klartext.txt
```

#### Hash berechnen

```bash
openssl dgst -sha256 datei.txt
```

#### Datei signieren

```bash
openssl dgst -sha256 -sign private.pem -out signatur.bin datei.txt
```

#### Signatur prüfen

```bash
openssl dgst -sha256 -verify public.pem -signature signatur.bin datei.txt
```

#### TLS-Verbindung testen

```bash
openssl s_client -connect example.com:443
```

#### Zertifikat anzeigen

```bash
openssl x509 -in cert.pem -text -noout
```
## Linux Grundbefehle 

#### Verzeichnis wechseln

Wechselt in ein anderes Verzeichnis.

```bash
cd verzeichnis
```

#### Ein Verzeichnis nach oben wechseln

Geht eine Ebene zurück.

```bash
cd ..
```

#### Verzeichnisinhalt anzeigen

Zeigt Dateien und Ordner im aktuellen Verzeichnis an.

```bash
ls
```

#### Detaillierte Ansicht anzeigen

Zeigt auch versteckte Dateien und zusätzliche Informationen.

```bash
ls -la
```

#### Aktuellen Pfad anzeigen

Gibt das aktuelle Arbeitsverzeichnis aus.

```bash
pwd
```

#### Neues Verzeichnis erstellen

Erstellt einen neuen Ordner.

```bash
mkdir ordnername
```

#### Datei löschen

Entfernt eine Datei dauerhaft.

```bash
rm datei.txt
```

#### Ordner rekursiv löschen

Löscht einen Ordner inklusive Inhalt.

```bash
rm -r ordner
```

#### Datei kopieren

Kopiert eine Datei an einen anderen Ort.

```bash
cp quelle ziel
```

#### Datei verschieben oder umbenennen

Verschiebt Dateien oder benennt sie um.

```bash
mv quelle ziel
```

#### Leere Datei erstellen

Erstellt eine neue leere Datei.

```bash
touch datei.txt
```

#### Dateiinhalt anzeigen

Gibt den Inhalt einer Datei aus.

```bash
cat datei.txt
```

#### Ausgabe in Datei schreiben

Speichert die Ausgabe in einer Datei und überschreibt vorhandenen Inhalt.

```bash
befehl > output.txt
```

#### Ausgabe an Datei anhängen

Fügt neue Ausgabe an das Ende der Datei an.

```bash
befehl >> output.txt
```

#### Ausgabe anzeigen und speichern

Zeigt die Ausgabe im Terminal und speichert sie zusätzlich in einer Datei. tee liest von stdin und schreibt gleichzeitig auf stdout und in eine Datei. Nützlich, wenn man eine Ausgabe sowohl sehen als auch speichern möchte.

```bash
befehl | tee datei.txt
```

#### Ausgabe anhängend speichern

Wie `tee`, aber ohne vorhandenen Inhalt zu überschreiben.

```bash
befehl | tee -a datei.txt
```

#### Befehle mit Pipe verbinden

Leitet die Ausgabe eines Befehls direkt an den nächsten weiter.

```bash
befehl1 | befehl2
```

#### Nach Text suchen

Durchsucht eine Datei nach bestimmten Begriffen.

```bash
grep "suchbegriff" datei.txt
```

---
## Pseudocode Übungen

Verwendete Funktionen in allen Aufgaben:

- enc(data, key): verschlüsselt data mit key
- dec(data, key): entschlüsselt data mit key
- hash(data): berechnet den Hashwert von data
- randkey(seed): erzeugt einen zufälligen symmetrischen Schlüssel
- send(...) / receive(...): Übertragung der Daten

#### 1. Aufgabe

Alice möchte eine Nachricht "message" an Bob senden. Die Nachricht soll hybrid verschlüsselt und digital signiert werden. Alice besitzt das Schlüsselpaar (alice_pub, alice_priv), Bob besitzt (bob_pub, bob_priv). Schreiben Sie den Pseudocode für Alice (Senden) und Bob (Empfangen + Verifizieren).

```bash
# Sender
key = randkey(seed)
encrypted_data = enc(data, key)
encrypted_key = enc(key, bob_pub)
data_hash = hash(data)
sig = enc(data_hash, alice_priv)
send(encrypted_data, encrypted_key, sig)


# Empfänger
receive(encrypted_data, encrypted_key, sig)
key = dec(encrypted_key, bob_priv)
data = dec(encrypted_data, key)
data_hash = hash(data)
signature_hash = dec(sig, alice_pub)
valid = (data_hash == signature_hash)
```

#### 2. Aufgabe: 

Schreiben Sie Pseudocode für eine einfache digitale Signatur ohne Verschlüsselung der Nachricht. Der Empfänger soll prüfen können, ob die Nachricht unverändert ist und vom richtigen Sender stammt.

```bash 
# Sender 
data_hash = hash(data)
sig = enc(data_hash, sender_priv)
send(data, sig)


# Empfänger
receive(data, sig)
data_hash = hash(data)
sig_hash = dec(sig, sender_pub)
valid = (data_hash == sig_hash)
```

#### 3. Aufgabe: 
Schreiben Sie Pseudocode für eine symmetrische Verschlüsselung. Sender und Empfänger besitzen denselben geheimen Schlüssel shared_key.

```bash
# Sender
encrypted = enc(data, shared_key)
send(encrypted)


# Empfänger 
receive(encrypted)
data = dec(encrypted, shared_key)
```

#### 4. Aufgabe: 
Beschreiben Sie den TLS-Handshake in Pseudocode. Erklären Sie dabei die Bedeutung von RNc, RNs, PMS und Master Secret. Ziel ist die sichere Aushandlung eines gemeinsamen symmetrischen Schlüssels.

```bash 
# Client
RNc = random()
send(client_hello, RNc, supported_cipher_suites)


# Server 
RNs = random()
send(server_hello, RNs, chosen_cipher_suite, server_certificate)


# Client 
verify(server_certificate)
PMS = random()
encrypted_PMS = enc(PMS, server_pub)
send(encrypted_PMS)


# Server 
PMS = dec(encrypted_PMS, server_priv)


# Beide Seiten unabhängig voneinander
master_secret = PRF(PMS, RNc, RNs)
```

**Begriffe:**

|Begriff|Bedeutung|
|---|---|
|RNc (Random Number Client)|Zufällige Zahl, die der Client zu Beginn erzeugt. Verhindert, dass ein Angreifer eine alte aufgezeichnete Verbindung wiederholt (Replay-Angriff).|
|RNs (Random Number Server)|Zufällige Zahl, die der Server erzeugt. Gleicher Zweck wie RNc, aber vom Server.|
|PMS (Pre-Master-Secret)|Zufallswert, den der Client erzeugt. Wird asymmetrisch mit dem öffentlichen Schlüssel des Servers verschlüsselt, nur der Server kann ihn entschlüsseln.|
|MS (Master Secret)|Der eigentliche symmetrische Schlüssel für die gesamte Verbindung. Wird von beiden Seiten unabhängig aus PMS + RNc + RNs berechnet, kein Angreifer kann ihn ableiten, weil PMS nur Server und Client bekannt ist.|
|PRF (Pseudo Random Function)|Funktion, die aus mehreren Eingaben einen deterministischen, aber kryptographisch sicheren Ausgabewert berechnet. Beide Seiten berechnen damit denselben Master Secret, ohne ihn zu übertragen.|

---
## Moodle Übungen

#### Symmetrische Verschlüsselung

**Frage 1.1: Wie viele Schlüssel werden benötigt, wenn 3 Personen miteinander kommunizieren wollen?**

Für 3 Personen werden insgesamt 3 Schlüssel benötigt, da jedes Personenpaar einen gemeinsamen Schlüssel braucht.

**Frage 1.2: Wer hat bei diesem Szenario welche Schlüssel?**

- Person A: K_AB (mit B) und K_AC (mit C)
- Person B: K_AB (mit A) und K_BC (mit C)
- Person C: K_AC (mit A) und K_BC (mit B)

**Frage 1.3: Wie viele Schlüssel hat jede Person?**

Jede Person hat 2 Schlüssel (einen für jede andere Person).

**Frage 2.1: Wie viele Schlüssel werden für eine Klasse mit n Personen benötigt?**

Anzahl Schlüssel = n × (n-1) / 2

**Frage 2.2: Wer hat welche Schlüssel?**

Jede Person besitzt einen eigenen Schlüssel für jede andere Person in der Klasse.

**Frage 2.3: Wie viele Schlüssel hat jede Person?**

Schlüssel pro Person = n - 1

**Frage 2.5: Wie bezeichnet man die Schlüssel?**

K_[Name1]_[Name2] oder K_[Kürzel1][Kürzel2], z.B. K_AB für den Schlüssel zwischen A und B.

**Frage 3.1: Wie viele Schlüssel werden allgemein für n Teilnehmer benötigt?**

Anzahl Schlüssel = n × (n-1) / 2

**Frage 3.2: Wie viele Schlüssel hat jede Person?**

Schlüssel pro Person = n - 1


#### Asymmetrische Verschlüsselung / RSA

**Frage 1.1: Welche Daten werden bei der Schlüsselerzeugung erfasst?**

- Name und Vorname
- Verfahren (z.B. RSA-1024)
- Schlüsselerkennung (optional)
- PIN-Code

**Frage 1.2: Was fällt bei der Schlüsselerzeugung auf?**

- Persönliche Daten sind im Schlüssel sichtbar
- RSA-1024 gilt als unsicher
- Für die Schlüsselerzeugung wird Zufälligkeit (Entropie) benötigt, die durch zufällige Nutzereingaben gesammelt wird

**Frage 1.3: Welche Länge des RSA-Moduls gilt heute als sicher?**

Mindestens 3072 bit (Quelle: BSI).

**Frage 2.1: Was ist am Schlüsselpaar für andere Nutzer sichtbar, was fehlt?**

Sichtbar: Modulus N und öffentlicher Exponent e. Nicht sichtbar: der private Schlüssel und die PIN.

**Frage 2.2: Wie lange ist ein Schlüsselpaar gültig?**

In der Regel 1-2 Jahre ab Erzeugung, abhängig von den Einstellungen bei der Schlüsselerzeugung.

**Frage 2.3: Wie viele Schlüssel hat jede Person bei asymmetrischer Verschlüsselung?**

Jede Person hat genau zwei Schlüssel: einen öffentlichen und einen privaten.

**Frage 3.1: Wie ist ein RSA-Schlüsselpaar zusammengesetzt?**

- Modulus N = p × q (Produkt zweier großer Primzahlen)
- Öffentlicher Schlüssel: (N, e)
- Privater Schlüssel: (N, d)

**Frage 3.2: Was besagt die Länge des RSA-Moduls?**

Die Länge gibt die Größe von N in Bit an. Je länger der Modul, desto schwieriger ist es, N in seine Primfaktoren p und q zu zerlegen, und desto sicherer ist der Schlüssel.

**Frage 3.3: Warum ist eine PIN-Eingabe bei der Schlüsselerzeugung erforderlich?**

- Die PIN verschlüsselt den privaten Schlüssel lokal
- Schutz vor Diebstahl der Schlüsseldatei
- Zwei-Faktor-Sicherheit: Schlüsseldatei + PIN
- Verhindert Missbrauch bei unberechtigtem Zugriff


#### RSA Demo

**Frage 2.2: Welche Schritte werden bei der Ver- und Entschlüsselung vorgenommen?**

Verschlüsselung: Klartext wird in Blöcke aufgeteilt, jeder Block wird mit dem öffentlichen Schlüssel des Empfängers verschlüsselt.
Entschlüsselung: Jeder Block wird mit dem privaten Schlüssel des Empfängers entschlüsselt und wieder zusammengesetzt.

**Frage 2.2: Welcher Schlüssel wird zur Ver- und Entschlüsselung genutzt?**

Verschlüsselung: öffentlicher Schlüssel des Empfängers. Entschlüsselung: privater Schlüssel des Empfängers.

**Frage 2.2: Warum sollte die Blocklänge möglichst groß gewählt werden?**

Kleine Blöcke sind anfälliger für statistische Angriffe. Größere Blöcke machen Angriffe deutlich schwieriger.

**Frage 2.2: Wie groß kann die Blocklänge sein?**

Die Blocklänge muss kleiner sein als der Modulus N.

**Frage 2.2: Falls nur die öffentlichen Parameter einsehbar sind, was ist möglich?**

Mit dem öffentlichen Schlüssel kann man Nachrichten verschlüsseln und Signaturen verifizieren. Entschlüsseln oder Signieren ist ohne den privaten Schlüssel nicht möglich.

**Frage 2.3: Was heißt Faktorisierung?**

Faktorisierung bedeutet, eine Zahl in ihre Primfaktoren zu zerlegen. Bei RSA: N in p und q zerlegen.

**Frage 2.3: Was bedeutet es, wenn eine Faktorisierung des RSA-Moduls möglich ist?**

Wenn N in p und q zerlegt werden kann, lässt sich der private Schlüssel berechnen, das Verfahren ist gebrochen.

**Frage 2.3: Wie kann der Möglichkeit der Faktorisierung vorgebeugt werden?**

Durch sehr große Schlüssellängen (mindestens 3072 bit laut BSI), da die Faktorisierung dann mit heutigen Mitteln praktisch unmöglich ist.


#### Dokument Ver- und Entschlüsseln

**Frage 3.1: Wie ist ein RSA-verschlüsseltes Dokument aufgebaut?**

Das verschlüsselte Dokument besteht aus mehreren Blöcken. Jeder Block enthält einen verschlüsselten Teil des Originaltexts. Die Blöcke sind in der Regel Base64-kodiert dargestellt.

**Frage 3.3: Welcher Teil des Schlüsselpaares wird vom Sender, welcher vom Empfänger verwendet?**

- Sender: verschlüsselt mit dem öffentlichen Schlüssel des Empfängers
- Empfänger: entschlüsselt mit seinem eigenen privaten Schlüssel


#### Hash-Verfahren

**Frage 4.1: Was passiert mit dem Hashwert, wenn das Dokument verändert wird?**

Bereits eine kleinste Änderung verändert den Hashwert komplett und unvorhersehbar (Lawineneffekt). Der neue Hashwert hat keinerlei erkennbare Ähnlichkeit mit dem alten.

**Frage 4.2: Geburtstagsangriff, wie ist das Ergebnis bei verschiedenen Bitlängen zu bewerten?**

- 16 bit: Kollision sehr schnell gefunden, praktisch sofort
- 32 bit: Kollision in kurzer Zeit gefunden
- 64 bit: Kollision dauert bereits sehr lange
- 128 bit: Kollision praktisch unmöglich, Angriff nicht durchführbar

Fazit: Je kürzer der Hashwert, desto leichter ist ein Kollisionsangriff. Ab 128 bit aufwärts sind Hashverfahren als sicher anzusehen.

**Frage 4.3: Welche Eigenschaften sollte eine Hashfunktion haben?**

- Deterministisch: gleiche Eingabe ergibt immer denselben Hash
- Einwegfunktion: aus dem Hash kann die Eingabe nicht rekonstruiert werden
- Kollisionsresistenz: keine zwei verschiedenen Eingaben mit demselben Hash
- Lawineneffekt: kleinste Änderung verändert den Hash komplett
- Feste Ausgabelänge: unabhängig von der Eingabelänge

**Frage 4.3: Wozu dient ein Hashwert?**

- Integritätsprüfung von Dateien und Nachrichten
- Grundlage digitaler Signaturen
- Sichere Passwortspeicherung


#### Digitale Signatur

**Frage 5: Welcher Schlüssel wird zur Erstellung der Signatur verwendet?**

Der private Schlüssel des Senders.

**Frage 5: Welcher Schlüssel wird zur Verifizierung der Signatur verwendet?**

Der öffentliche Schlüssel des Senders.

**Frage 5: Warum ist vor der Signatur-Erstellung eine PIN-Eingabe notwendig?**

Der private Schlüssel ist durch eine PIN geschützt. Ohne PIN kann der private Schlüssel nicht verwendet werden, was Missbrauch verhindert.

**Frage 5: Wie kann die Echtheit einer Signatur überprüft werden?**

Die Signatur wird mit dem öffentlichen Schlüssel des Senders entschlüsselt. Der erhaltene Hashwert wird mit dem selbst berechneten Hashwert des Dokuments verglichen. Stimmen beide überein, ist die Signatur echt.

**Frage 5: Was kann daraus geschlossen werden, wenn zwei Hashwerte gleich sind?**

Das Dokument wurde seit der Signatur nicht verändert und stammt tatsächlich vom angegebenen Sender.

**Frage 5: Welche Eigenschaften hat eine digitale Signatur?**

- Authentizität: beweist, wer das Dokument signiert hat
- Integrität: beweist, dass das Dokument nicht verändert wurde
- Nicht-Abstreitbarkeit: der Sender kann die Signatur nicht leugnen


#### TLS-Traffic

**Frage: Ist TLS-verschlüsselter Datenverkehr wirklich sicher?**

Grundsätzlich ja solange der private Schlüssel des Servers geheim bleibt und das Zertifikat vertrauenswürdig ist. Auf dem eigenen Rechner kann man TLS jedoch lokal entschlüsseln, wenn man Zugang zu den Session Keys hat.

**Frage: Wie kann man bei Firefox einen TLS-verschlüsselten Datenstrom lokal entschlüsseln?**

Firefox kann über die Umgebungsvariable SSLKEYLOGFILE dazu gebracht werden, alle Session Keys in eine Datei zu schreiben. Wireshark kann diese Datei einlesen und damit den aufgezeichneten verschlüsselten Traffic entschlüsseln.

Anleitung:
1. Umgebungsvariable setzen: SSLKEYLOGFILE=/pfad/zur/keys.log
2. Firefox über die Kommandozeile starten, damit die Variable aktiv ist
3. Wireshark starten und den Netzwerkverkehr aufzeichnen
4. In Wireshark unter Einstellungen → Protocols → TLS den Pfad zur Key-Log-Datei eintragen
5. Wireshark entschlüsselt nun den TLS-Traffic automatisch

**Frage: Wie könnte dieses Verfahren zum Ausspähen von HTTPS-Datenverkehr genutzt werden?**

Wenn ein Angreifer Zugang zum Rechner des Opfers hat und die SSLKEYLOGFILE-Variable setzt, kann er danach den gesamten HTTPS-Verkehr des Browsers mitlesen, inklusive Passwörter, Formulardaten und Login-Tokens. Das Verfahren funktioniert aber nur lokal auf dem eigenen Rechner, nicht aus der Ferne ohne vorherigen Zugriff.
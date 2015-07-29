
# Passwörter

**1. Was ist eine Identität? Worin besteht beim Einloggen an Rechnern die Identifizierung und worin die Authentifizierung?**
* Identifizierung: Bestimmung der beteiligten Personen (Identität der Subjekte)
* Authentifikation: Prüfung der Identität des Subjekts
* Identifizierung ist der Benutzername und Authentifizierung das Passwort

**2. Was wird unter Autorisierung verstanden?**
* Autorisierung: Zuordnung von Rechten an Subjekte in Bezug auf Objekte

**3. Worin besteht der wesentliche Unterschied zwischen einem Passwort und einem Schlüssel?**
* Passwort stellt die Identität des Benutzers fest
* Schlüssel beinhalten alle möglichen Bitkombinationen, während Passwörter nur eingeschränkte Bitkombinationen (Zeichensatz) verwenden
* Schlüssel sind in der Regel länger als Passworte
* Schlüssel kann die Integrität von Daten durch eine Signatur sicherstellen

**4. Was sind die Kriterien eines guten Passworts? Nennen Sie drei Kriterien, die maschinell geprüft werden können.**
* Länge, Unterschiedliche Zeichen (Großbuchstaben, Kleinbuchstaben, Sonderzeichen), Kein Wort natürlicher Sprache

**5. Skizzieren Sie ein Merkverfahren für einigermaßen gute Passwörter, die auch vergessliche Menschen behalten können (sollten).**
* Einen Satz (z.B. ein Zitat oder eine Zeile aus einem Gedicht) bei dem nur die Anfangsbuchstaben der Wörter genommen werden und diese inkl. Satzzeichen zu einem Passwort zusammengesetzt wird
* Leet-Speak

**6. Welcher Vor- und welche Nachteile hat ein zwangsweises häufiges Ändern der Passwörter?**
* Vorteile: ein Angreifer der Zugriff auf ein System hat kann nicht mehr zugreifen nachdem das Passwort geändert wurde (es sei denn er hat sich schon anders Zugriff beschafft)
* Nachteile: Passwörter können vergessen werden, vertleitet dazu besonders einfache Passwörter zu benutzen oder sich diese aufzuschreiben
**7. Beschreiben Sie die prinzipiellen Vorgehensweisen bei der Passwortdefinition und Prüfung, wenn (a) DES oder (b) MD5 verwendet wird.**
* MD5: PW nehmen, verschlüsseln, Hashen, Hash wird abgelegt (PW wird also nicht im Klartext abgelegt)
* DES:  im Prinzip das Selbe...

## Angriffe

**8. Wie arbeitet der Wörterbuchangriff? Gehört dieser zu den Brute Force Methoden?**
* Alle Einträge eines Wörterbuchs (Worte, Silben, …) in die entsprechende Passwortform (MD5, DES, ...) überführen und es mit dem vorhandenen Passwort abgleichen
* Nein, da eine übersichtliche Menge an Daten (nicht alle Kombinationen der definierten Zeichen) verwendet wird und diese nicht erst generiert werden wie bei Brute Force

**9. Was ist bei der Verschlüsselung von Passwörtern das Salz? Wozu dient es? Muss es geschützt werden?**
* Salz = Zufälliger, dem Angreifer (möglichst) unbekannter Wert, der in die Verschlüsselung eingeht
* Durch den zufälligen Anteil entstehen verschiedene Hashwerte aus Passwörtern
* Es muss geschützt werden, kann unter bestimmten Bedingungen aber auch bekannt sein (siehe Linux Passwörter)

**10. Welchen gravierenden Nachteil haben Key-Stores (verschlüsselte Dateien mit Passwörtern), die nach einer initialen Eingabe des Schlüssels eine ganze Sitzung lang benutzt werden können?**
* Wenn Masterkey bekannt dann Zugriff auf alle Passwörter die gespeichert sind
* durch Schadsoftware auf dem System nach dem Öffnen auslesbar
* durch Kopierbarkeit Brute-Force/Wörterbuchangriff-anfälliger

**11. Nennen Sie mindestens zwei Passwort-Crack-Werkzeuge.**
* John the Ripper, Hashcat, Cain & Abel

**12. Beschreiben Sie den typischen Infektionsweg von VBA-Viren.**
* Word Dokumente (Makro)

**13. Charakterisieren Sie die Idee, die hinter einem Bufferoverflow-Angriff liegt. Welcher Fehler ist die Ursache für solche Möglichkeiten?**
* Bufferoverflow = Programmierfehler, der dazu führt, dass zu viele Daten in einen Puffer gelesen und dadurch Bereiche dahinter überschrieben werden
* Keine Überprüfung der Eingabelänge

**14.Warum ist das Montieren von externen Datenträgern mit einem Filesystem bei jedem Betriebssystem kritisch? Worin besteht dabei das Problem?**
* Auf dem Datenträger kann ein Betriebssystem sein welches beim Bootvorgang gestartet wird. Von diesem kann auf das Dateisystem des Rechners zugegriffen werden. Hier können nicht nur Daten kopiert sondern ggf. auch verändert werden (z.B. Installation eines Rootkits/Trojaners)
* Rechte des eigentlichen Dateisystems werden nicht beachtet, wenn auf dem externen Datenträger beispielsweise eine Linux-Live Distribution gestartet wird

**15. Skizzieren Sie die Smurf-Attacke. Was wäre das Ziel dieser Attacke? Wie lässt sie sich verhindern?**

Es handelt sich um einen DoS-Angriff, der mit Broadcast-Pings versucht ein bestimmtes System zu stören

Ablauf:
1. Zusammenbau eines Ping-Paketes
2. Zusammenbau eines IP-Paketes mit Absender-Adresse des Opfers (Spoofing)
3. (Mehrfaches) Absenden des Paketes mit Broadcast-Adresse

Folge:
* Die meisten Systeme schicken ein ECHO Reply an das Opfer, das mit einem Schlag eventuell hunderte von IP-Paketen bekommt
* Jetzt entscheidet die Implementierungsgüte des TCP/IP-Stacks über Leben und Tod
* Verhinderung: Broadcast durch Router nicht zulassen

**16.Was wird unter OS-Fingerprinting verstanden? Was für ein Ziel wird bei derartigen Verfahren verfolgt?**
Durch dieses Verfahren werden anhand von Netzwerkreaktionen des Zielsystems Rückschlüsse auf das eingesetzt Betriebssystem gezogen. z.B. wie das System auf einen fehlerhafter Verbindungsaufbau zum Port 443 reagiert. Sobald man das Betriebssystem kennt, kann man versuchen, bestimmte Sicherheitslücken dieses Betriebssystems auszunutzen.

**17.Was ist Banner Grabbing? Was für ein Ziel wird bei derartigen Verfahren verfolgt?**
Beim Zugriff auf FTP-Server, Webserver o.Ä. wird manchmal ein Banner (Einleitungstext) mit der Softwareversion und weiteren Informationen mitgesendet. Diese Informationen können teilweise sensible Daten (Version ,...) beinhalten und somit von Angreifern für spezialisierte Exploits ausgenutzt werden.

## Rechtesystem von Unix

**18. Wie werden Benutzer und wie Gruppen in Unix intern identifiziert? Wo werden diese definiert?**
* /etc/group Datei (Zuordnung Benutzer: alle Gruppen-Id’s)
* Durch Benutzer-Id uid und Gruppen-Id gid

**19. Was waren die Gründe für die Einführung des Shadow-Systems? Was macht der Login-Prozess beim Shadow-System anders als beim alten hergebrachten System?**
* Separierung der Informationen für Login und Benutzer
* Shadow-System dient dem Schutz der /etc/passwd-Datei, in der die Zugangspasswörter der Benutzer des UNIX-Systems abgelegt sind. 
* Trennung von user id und (verschlüsselten) Passwörtern in zwei Dateien Zuordnung unterschiedlicher permissions

**20. Für die Repräsentation der Rechte in UNIX reichen 9 bit. Welche Bedeutung haben diese?**
* 3Bit User, 3Bit Group 3Bit Other
* Bit 1: Read, Bit 2: Write, Bit 3: Execute

**21. Beschreiben Sie den Algorithmus zur Bestimmung der Rechte eines Prozesses, wenn dieser eine Datei eröffnet.**
* Überprüfung in der Reihenfolge: User? Group? Other!
* syscall open -> Datei öffnen -> entspricht UID == Datei UID -> owner GID == GID -> Group...

**22. Welche Wirkungen haben die Set-UID bzw. Set-GID-Bits?**
* Leider benötigen einige harmlose Programme root-Rechte, z. B. mkdir oder rmdir.
* Daher werden pro Prozess zwei weitere 16-bit-Werte eingeführt: Effektive UID und effektive GID.
* Diese bestimmen die wirksamen Rechte. Die bisher vorgestellten IDs heißen reale UID und reale GID.
* Wird eine ausführbare Datei gestartet, so läuft folgendes Verfahren ab: 
* Ist ein Set-UID-Bit der Datei zugeordnet, erhält der Prozess als effektive UID die UID des Datei-Owners.
* Ist ein Set-GID-Bit der Datei zugeordnet, erhält der Prozess als effektive GID die GID der Datei-Gruppe.
* Ist kein Set-Bit gesetzt, behält der Prozess seine alten UID/GIDWerte.
* Initial sind reale und effektive UID/GID gleich.

**23. Warum wurden die Set-UID bzw. Set-GID-Bits eingeführt?**
* Damit können für ein Programmlauf besondere Rechte ausgeliehen werden.

**24. Welche Sonderregelungen betreffen Prozesse mit einer UID = 0?**
* 0 gehört Root
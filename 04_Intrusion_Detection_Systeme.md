# Intrusion Detection Systeme (IDS)

**1. Was wird unter einer Intrusion verstanden? Nennen Sie auch andere Erklärungen dieses Begriffs. Was spricht für den Begriff Incident? Was würde dieser bedeuten?**
* Intrusion (Störung, Verletzung, Eindringen) = Erfolgreicher lesender oder schreibender, aber nicht erlaubter Zugriff auf Daten bzw. Ausführung von Programmen durch organisationsfremde Personen, also von Außen
* Misuse = Missbrauch = Erfolgreicher lesender oder schreibender, aber nicht erlaubter Zugriff auf Daten bzw. Ausführung von Programmen durch Personen der eigenen Organisation, also von Innen
* Incident = Zusammenfassender Oberbegriff von Intrusion und Misuse, Vorfall, bei dem etwas unerlaubtes geschah

**2. Nennen Sie mindestens fünf Aufgaben, die ein gutes IDS realisieren sollte.**
* Feststellen
* Erkennen aktuell laufender Angriffe
* Erkennen früher erfolgter Angriffe
* Feststellen von nicht erlaubten Modifikationen und Zugriffen
* Analyse der Probleme und deren Einschätzung
* Reagieren
* "Unterbrechen" betroffener Verbindungen, Abschotten
* Beenden betroffener Prozesse, z. B. Ausloggen und Sperren des betreffenden Logins
* Berichten bzw. Melden
* Zusammenfassung verschiedener Datenbestände
* Erstellung Berichte unterschiedlicher Detailliertheit
* Versenden von Alarm-Nachrichten, z.B. Mail, SMS

**3. Wie kann ein IDS feststellen, warum eine Modifikation bestimmter Dateien während eines Angriffs erfolgte?**
* Weil eine Kopie der Datei / einen Hash vorher erstellt wurde mit der das IDS die aktuelle Datei / den Hash in bestimmten Zeitabständen abgleicht
* Kann nur ein Mensch feststellen, warum eine Modifikation der Datei vorgenommen wurde

**4. Was wird im Rahmen des Computer Forensics getan? Nennen Sie mindestens zwei typische Arbeiten.**
* Erfassen von relevanten "Spuren"
* Beweis der Originalität der Spuren, d.h. dass Spuren nicht nachträglich verändert oder geschaffen wurden
* Nachweis der Herkunft der Spuren

**5. Nennen Sie mindestens drei Beispiele für Anomalien, die Hinweise auf eine Intrusion liefern, und erläutern Sie für welche Ereignisse diese Anomalien Indizien sind.**
* [Anomalie = außergewöhnliches Verhalten (von Software) Anormal ist ein Verhalten, das sich vom "Durchschnitt" wesentlich unterscheide]
* Ein verreister Mitarbeiter loggt sicht ein -> nicht der Mitarbeiter sondern Hacker
* Eine langschläfrige Mitarbeiterin loggt sich um 7:00Uhr früh ein -> nicht der Mitarbeiter sondern Hacker
* Zugriff auf Daten aus Backups -> Daten werden geklaut

**6. Worin unterscheiden sich die NIDS von den HIDS? Scannen die NIDS ein Netzwerk?**
* Host-basierte IDS = HIDS = IDS zur Überwachung eines Systems, wobei das IDS auf diesem System auch arbeitet
* Netzwerk-basierte IDS = NIDS = IDS zur Überwachung von Netzwerkverbindungen
* vor einer Firewall ("draußen")
* hinter einer Firewall in der DMZ
* in Netzsegmenten des Innenbereichs
* Nein, die NIDS scannen kein Netzwerk

**7. Eine Firma hat ein lokales Netzwerk und über eine Firewall einen Anschluss ans Internet. Wo könnten die HIDS und wo die NIDS sinnvollerweise positioniert werden?**
* HIDS:
* alle Server und Endgeräte wo Kommunikation von außen stattfindet
* Firewalls
* NIDS:
* hinter der Firewall 

**8. Was ist ein Honeypot? Durch welche Maßnahmen bzw. welche Art von Software wird ein Honeypot typischerweise realisiert?**
* Honeypot = Spezielles System, das absichtlich Angriffe zulässt, um die Art und Technik der Angriffe studieren zu können
* Rechner mit “gewollten” Sicherheitslücken
* Software mit Monitor-Funktion
* Virtuelle Machine

**9. Eine Firma hat ein lokales Netzwerk und über eine Firewall einen Anschluss ans Internet. Wo sollten sinnvollerweise die Honeypots positioniert werden?**
* Honeypot = Spezielles System, das absichtlich Angriffe zulässt, um die Art und Technik der Angriffe studieren zu können
* vor der Firewall
* hinter einer Firewall in der DMZ

**10. Wie kann ein IDS zu einem DoS-Angriff mißbraucht werden? Ist das zu verhindern?**
* Absichtlich produzierte Fehlalarme
* Einschränkung bei der Überwachung von Ports, Fehlermeldungen, etc.

**11. Was ist eine Policy? Welche Aufgabe wird mit der expliziten Formulierung von Policies gelöst?**
* Policy = Politik = Sicherheitsrichtlinie oder Regelsystem, das den Umgang mit der EDV aus dem Blickwinkel der Sicherheit festlegt
* was ein Angriff ist, 
* wie der Schutz vor Angriffen gestaltet werden soll, 
* wer was tun darf bzw. muss (Rechte/Pflichten)
* Dies betrifft häufig Rollen innerhalb von Organisationen.
* Organisatorische Aspekte der Sicherheit, z.B. Aufgaben des Sicherheitsbeauftragten

**12. Die Software tripwire gehört zu der Gruppe der HIDS. Wie arbeitet tripwire?**
1. Policy für die Überwachung definieren (twpol.txt, twpol)
2. Datenbank der zu überwachenden Dateien erstellen ()
3. tripwire starten und Logdateien regelmäßig überprüfen

**13. Wie können IDS, wie z.B. tripwire oder aide, selbst angegriffen werden? Durch welche Maßnahmen können Sie diese Gefährdung abwenden (nennen Sie zwei Möglichkeiten)?**
* Angriff: provozierte Fehlalarme, Sicherheitslücken in der Software, Änderung der Policy-Datei
* Gegenmaßnahmen: Hashen der Policy Datei und speichern des Schlüssels auf einem USB-Stick

**14. Die Software snort ist ein NIDS. Kann snort Portscanns erkennen? Wie arbeitet snort?**
* Snort kann Portscanns erkennen, wenn die ICMP-Pakete vom selben Host an verschiedene Ports des Systems in kurzen Zeitabständen kommen

**15. Kann snort Zugänge bei Feststellung eines Angriffs sperren?**
* Snort kann keine Zugänge sperren, sondern nur Netzwerkverkehr analysieren und auswerten
# Scanner

**1. Was ist allgemein ein Scanner? Was ist dabei ein Netzwerk- und was ein System-Scanner?**
* Scanner = Programm, das ein System systematisch auf Schwachstellen oder Probleme prüft und teilweise repariert
* System-Scanner = Scanner, der als Teil des zu analysierenden Systems arbeitet, z. B. von CDROM gestartet
* Netzwerk-Scanner = Scanner, der Systeme über Netze scannt
* Prüfen der Erreichbarkeit von Servern, z.B. Drucker
* Prüfung von Firewalls (offene Ports)

**2. Nennen Sie mind. vier Schwachstellen, die ein guter System-Scanner aufdecken sollte.**
* Fehlende Passwörter
* Zu leichte oder zu kurze Passwörter
* Laxe/fehlerhafte Dateirechte, z. B. suid root von Benutzerprogammen
* Laxe/fehlerhafte Konfigurationen, z. B. fehlerhafte .htaccess-, host.equiv-Dateien etc. oder freies Upload bei FTP-Servern
* Viren, Trojanische Pferde
* Modifikationen von Programmen

**3. Nennen Sie ein Beispiel für einen System-Scanner - außer Viren und Spywarescannern.**
* tiger, tara

**4. Was ist ein Exploit und was ein Rootkit?**

**Exploit**: systematische Möglichkeit, Schwachstellen auszunutzen, die bei der Entwicklung eines Programms nicht berücksichtigt wurden. Meist um sich Zugang zu Ressourcen zu verschaffen oder in Computersysteme einzudringen, bzw. diese zu beeinträchtigen.

**Rootkit**: Sammlung von Programmen, die Teile des Betriebssystems ersetzen, um einen leichten Zugang von außen zu realisieren

**5. Exploits sind häufig frei im Internet verfügbar. Mit welcher Begründung werden diese Exploits von den Autoren veröffentlicht? Was spricht gegen die Veröffentlichung im Internet?**
1. Dafür: Um den Druck für dessen Behebung aufzubauen
2. Dagegen: Ausnutzung des Exploits durch “jedermann”

**6. Bei den Rootkits gibt es mehrere Gefährlichkeitsstufen - skizzieren Sie für drei Stufen die technische Verfahrensweise des Rootkits.**
* Application-Rootkits =  bestehen lediglich aus modifizierten Systemprogrammen. 
* Kernel-Rootkits = ersetzen Teile des Kernels durch eigenen Code, um sich selbst zu tarnen und dem Angreifer zusätzliche Funktionen zur Verfügung zu stellen, die nur im Kontext des Kernels ausgeführt werden können. 
* Userland-Rootkits = Sie stellen jeweils eine DLL bereit, die sich anhand verschiedener API-Methoden direkt in alle Prozesse einklinkt. Ist diese DLL einmal im System geladen, modifiziert sie ausgewählte API-Funktionen und leitet deren Ausführung auf sich selbst um („redirect“). Dadurch gelangt das Rootkit gezielt an Informationen, welche dann gefiltert oder manipuliert werden können.
* Speicher-Rootkits = existieren nur im Arbeitsspeicher des laufenden Systems. Nach dem Neustart des Systems sind diese Rootkits nicht mehr vorhanden.

**7. Nennen Sie mindestens zwei Beispiele für Netzwerk-Scanner.**
* nmap, strobe, ping, traceroute, Xprobe2, SuperScan

**8. Was lässt sich alles mit nmap innerhalb des eigenen LANs herausfinden?**
* offene Ports (TCP, UDP)
* Rechner (IPs) im Netz
* Fingerprint einer Anwendung (Banner-Grabbing) nach erfolgreichem 3-Wege-Handshake (TCP)
* OS-Detection

**9. Wie lassen sich Ports von Systemen scannen, ohne dass das scannende System als solches in den Logfiles auftaucht? Skizzieren Sie eine Möglichkeit. Ist das auch ein praktikables Verfahren?**
* Es wird eine unbelastete Maschine M gesucht
* Diese wird mit hping -r (Verwendung inkrementeller IP-IDs) beobachtet: Steigen die IP-IDs um 1, so ist M unbelastet
* Die Hacker-Maschine H überwacht mit ping M kontinuierlich und wertet die IP-ID-Differenzen aus
* Die Hacker-Maschine H testet parallel einen Port auf der Opfermaschine O mit der Absenderadresse von M
* Antwortet O an M (und arbeitet sonst niemand auf M), so ist IP-ID um 2 erhöht, was durch das ping durch H festgestellt wird
* Mit einem gewissen Risiko können die Ergebnisse als ein Portscan ausgewertet werden.

**10. Wie arbeitet beim Portscannen ein Full-connect- und wie ein Halfconnect-Scann?**
* Protokollablauf (H = Hackerhost, O = Opferhost)
* 1. H->O: SYN-Paket
* 2. O->H: SYN/ACK oder RST
* RST: Entweder zu diesem Zeitpunkt kein Verbindungsaufbau möglich oder "mit DIR rede ich nicht"
* Ist der Port geschlossen, gib es eine ICMP-Meldung oder gar nichts
* 3. H->O: ACK
* 4. O->H: Banner etc.
* 5. H->O: ACK und Abbau mit ordentlichen FIN

* bei Half-Connect wird bei Schritt 3 FIN mitgeschickt (Schritt 4 findet nicht statt) 5 wieder wie oben

**11. Wie arbeitet der Xmas-Scan und wie der NUL-Scan?**
* Xmas-Scan:
* Protokollablauf: Es wird ein FIN-Paket mit allen Flags gesetzt gesendet.
* Darauf muss bei geschlossenem Port mit einem RST geantwortet werden, ansonsten wie bei FIN-Scan.
* Null-Scan:
* Protokollablauf: Es wird ein FIN-Paket ohne ein einziges gesetztes Flag gesendet
* Darauf muss bei geschlossenem Port mit einem RSTgeantwortet werden, ansonsten wie bei FIN-Scan

**12. Was macht der Scanner SATAN?**
* Prüft Schwachstellen bei FTP, TFTP, NFS, Rsh, (R-Tools), Sendmail, X
* Ähnlich wie Nessus

**13. Was prüft SAINT als Weiterentwicklung von SATAN über SATAN hinaus?**
* CGI-Probleme
* DoS-Angriffe
* POP-Server-Probleme
* SSH-Probleme
* Pufferüberläufe

**14. Nessus arbeitet mit vielen Plugins. Was wird in diesen definiert?**
* Plugins erweitern Nessus um weitere Tests

**15. Die Plugins sind eine der Ursachen für den Erfolg von Nessus. Wie entstehen diese Plugins? Wie werden sie realisiert?**
* Die Plugins werden in NASL oder C geschrieben, davon ca. 99% in NASL (Nessus Scripting Language)
* Damit kann Nessus sehr leicht auf aktuelle Probleme bzw. Lücken angepasst werden
* Werden von der Community gemacht

**16.Wie arbeitet Nessus? Skizzieren Sie dazu die globale Software-Architektur
und erläutern Sie daran, was zu einem Scann alles gehört.**
* Client: Über Browser gesteuert
* Server: Läuft als Dienst im Hintergrund und erledigt Scann
* Plugins: Erweiterung um Module zum Scanner bestimmter Schwachstellen

**17.Gibt es für Scanner Tests, die für das zu scannende System gefährlich
sein könnten? Falls ja, nennen Sie mindestens zwei Beispiele.**
* Ping of Death: Senden eines fehlerhaften ICMP-Paketes (führt zu Bufferoverflow)
* Smurf-DoS-Attacke: Kurzeitig hohe Belastung des Netzes
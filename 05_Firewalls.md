# Firewalls

**1. Was wird allgemein unter einer Firewall verstanden?**
* Firewall = Gerät, Betriebssystemkomponente oder Programm, das oder die eine Zugriffskontrolle mit Hilfe eines Filters realisiert

**2. Worin besteht der Unterschied zwischen einer Proxy-Firewall und einem Packet-Filter?**
* Packet-Filter = Firewall, die Pakete der Ebenen 3 und/oder 4 ohne Betrachtung der Dateninhalte prüft
* Proxy-Firewall = Firewall, die Pakete der Ebenen 3, 4 bis 7 einschließlich der Daten prüft
* Typische Aufgaben der Proxies in Firewalls sind: 
* Prüfung auf aktive Inhalte bei HTTP
* Prüfung auf "ungesunde" Kommandos bei SMTP oder FTP
* Prüfung auf zulässige Web Services, z. B. über SOAP

**3. Skizzieren Sie einen Angriff auf eine Firewall, der mit fragmentierten Paketen arbeitet.**
* Tear-Drop: 
* Kopf vom ersten Fragment in Ordnung, erlaubte Ports werden angesprochen und Paket durchgelassen
* zweites Fragment kann bspw Portnummern des ersten Fragments überschreiben, wird aber auch durchgelassen, da 1. Fragment okay war

**4. Skizzieren Sie Situationen, in denen das Verbieten von Fragmentierung bzw. das Unterdrücken von korrespondierenden zu Problemen führt.**
* kein Standards für die maximale Packetgröße von IP-Paketen (MTU)
* verschiedene Hardware nutzt unterschiedliche Packetgrößen
* da der beste Durchsatz durch die Nutzung der maximalen Paketgröße erreicht wird, handelt die Software die Paketgröße mit den einzelnen Endgeräten aus
* deshalb ist der Verbot von IP-Fragmentierung und korrespondierenden Paketen nicht sinnvoll

**5. Wie sähe eine allgemeine Architektur von Firewalls aus? Was wäre dabei der minimale und was der maximale Ausbau?**
* Architektur: Das WAN wird über eine Firewall getrennt mit einem DMZ oder Intranet verbunden.
* Minimal: Komponente auf einem Host, dessen Netzschnittstellen mit Filtern versehen sind, und auf dem die zu schützenden Applikationen laufen
* Maximal: Aufteilung in äußeren und inneren Bereich

**6. Was ist eine Personal Firewall? Kann diese mit Proxies arbeiten? Wo würden dann diese laufen?**
* Personal Firewalls = Firewalls auf den Endsystemen. 
* Diese Firewalls sind bei Ende-zu-Ende-Verschlüsselung notwendig.
* Leider müssen sie von den Benutzern administriert werden.
* Auch kommen häufig Benutzer mit den Meldungen der Firewalls nicht zurecht 
* Ja, sie kann mit Proxies arbeiten, wobei die Firwall dann auf dem Proxy-Server eingerichtet wird und die Clients vor Angriffen/unsicheren Paketen schützt

**7. Unter welchen Umständen kann auf Personal Firewalls nicht verzichtet werden? Wann würde daher eine zentrale Firewall beim Übergang in das betreffende Netz nicht ausreichen?**
* Bei Ende-zu-Ende Verschlüsselung

**8. Was wird unter einem Dual Homed Host verstanden?**
* Dual-homed host: haben zwei Netzschnittstellen mit jeweils zwei Filtern

**9. Worin besteht der Unterschied zwischen einem zustandslosen und einem zustandsbehafteten Packet-Filter?**
* Zustandslose Firewall = stateless firewall = statische Firewall = 
* Firewall, bei der jedes Paket isoliert von allen anderen untersucht wird
* Manchmal auch: stateless filtering genannt
* Kontextsensitive Firewall = statefull firewall = dynamische Firewall = 
* Firewall, bei der mehrere im Zusammenhang stehende Pakete zur Grundlage der Entscheidung über das Filtern gemacht werden
* Manchmal auch: statefull filtering genannt

**10. Welche Vor- und welche Nachteile hat ein statisches Packet-Filter? Und welche ein dynamisches?**

**Zustandslos**

Vorteile
* Schnell – Einfache Regeln, überschaubar

Nachteile
* Leicht zu überwinden, z. B. mit Fragmentieren

**Zustandbehaftet**

Vorteile:
* Fängt sehr viel ab

Nachteile:
* Langsam
* Schwer zu implementieren
* Hohe Qualität schwer zu erreichen
* Für DoS-Angriffe gefährdet, da Tabellen überlaufen können (Was passiert in diesem Fall? Sperren? "Rückfall" in den zustandslosen Betrieb?

**11. Welche Arten von Absenderadressen können bei einer Personal Firewall mit einem Übergang zum Internet von Außen in jedem Fall herausgefiltert werden? Nennen Sie drei Beispiele.**
* (einzelne) Absenderadresse
* Adressbereich
* Absendernetz (Subnetz)

**12. Welche Arten von Absenderadressen können bei einer Dual-Homed-Firewall, mit einem Übergang zum Internet, von Außen in jedem Fall herausgefiltert werden? Nennen Sie drei Beispiele.**
* gleiche wie bei 11. ?

**13. Welche Arten von ICMP-Paketen sollten als kritisch eingestuft und ihre Herausfilterung in Betracht gezogen werden bzw. welche ICMP-Pakete sind relativ ungefährlich?**
* Ping ist von Fall zu Fall zu entscheiden
* Gefährlich
* Port (unreachable)
* alles was mit Routerkommunikation zu tun hat (es sein denn es gibt tatsächlich mehrere Router in dem Netzwerk)
* Ungefährlich
* Domain Name Request, Reply
* Timestamp, Reply
* Parameterfehler
* TTL

**14. Was ist bei iptables eine Chain (Kette)? Skizzieren Sie den allgemeinen Algorithmus bei der Bearbeitung dieser Ketten.**
* Eine Regelkette wird solange durchlaufen bis das Ende erreicht wird oder die erste Bedingung zutrifft (hierbei gibt es Ausnahmen).
* Eine Ausnahme sind Logging-Aktionen, nach denen weiter gelaufen wird.
* Bei einem Zutreffen der Bedingung wird eine Aktion durchgeführt.
* Ist das Ende einer Tabelle erreicht, wird eine allgemeine Regel angewandt: die Policy

**15. Das Filtermodul von iptables arbeitet mit 3 Regelketten. Welche sind dies und welche Bedeutung haben diese?**

**Dirk**
* Input: Alle Pakete die als Destination der eigenen IP-Adresse entsprechen
* Forward: Alle Packete die als Destination oder als Source nicht der eigenen IP-Adresse entsprechen
* Output: Alle Packete die als Source der eigenen IP-Adresse entsprechen

**Messer**
* Input-Chain: Filter für eingehende Pakete an Prozesse
* Output-Chain: Filter für ausgehende Pakete von Prozessen
* Forward-Chain: Filter für Pakete, die durchgeleitet werden

**16. Was macht ganz allgemein das Kommando iptables?**
* iptables setzt, ändert, löscht Regelen und Policies für die einzelnen Chains Input, Output und Forward

**17. Worin besteht der Unterschied zwischen den iptables-Aktionen REJECT und DROP?**
* Reject: Verwerfen und mit ICMP-Fehlermeldung ablehnen
* Drop: Verwerfen

**18. Wodurch wird entschieden, ob ein empfangenes Paket durch die INPUT- oder durch die FORWARD-Chain „läuft“?**
* Alle Pakete die als Destination der eigenen IP-Adresse entsprechen gehen in die Input-Chain und alle Pakete mit eine anderen Destination-Adresse gehen in die Forward Chain
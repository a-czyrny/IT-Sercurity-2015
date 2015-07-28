# Grundlagen der Sicherheit

**1. Was beinhaltet der Begriff der Sicherheit? Nennen Sie mindestens drei Aspekte.**
* Verlässlichkeit der zu erbringenden Dienstleistungen in der gewünschten Qualität
* Schutz der Daten gegen Änderungen aus Versehen, mit Absicht oder aufgrund von Mängeln der Technik
* Zugang zu den Daten nur für berechtigte Personen auf berechtigte Art und Weise

**2. Was wird unter Authentifizierung verstanden, was unter Autorisierung und was unter Identifizierung?**
* Authentifikation: Prüfung der Identität des Subjekts
* Autorisierung: Zuordnung von Rechten an Subjekte in Bezug auf Objekte
* Identifizierung: Bestimmung der beteiligten Person (Identität der Subjekte)

**3. Womit beschäftigt sich primär der Datenschutz?**
Datenschutz ergänzt Sicherheit noch durch:
* Beschränkungen für Personen mit erlaubten Zugang
* Beschränkungen der Datenerfassung, Abgleich und Weitergabe (jedoch nur für Daten mit Bezug auf Personen)

**4. In welchen Schritten können Hacker systematisch von außen in ein Netzwerk eindringen? Skizzieren Sie eine sinnvolle Methodik.***
* Schritt 1: Auskundschaften (Suchmaschinen, Mitarbeiter, News,...)
* Schritt 2: Analyse des technischen Ziels (Scans, Analyse v. Servern/Bannergrabbing,...)
* Schritt 3: Angriffe (Ausnutzen v. Lücken, Denial of Service)
* Schritt 4: Übernahme des Systems (Backdoor, modifizieren v. Rechten, Rootkits, …)

**5. Welches ist das schwächste Glied in der Sicherheitskette?**
* “2/3 aller ernsthaften Probleme entstehen durch die eigenen Mitarbeiter/innen.”

**6. Auf welchen Mängeln von Systemen beruht das Hacken von Computern in Netzen?**
1. Qualitätsmängel in der Herstellung der Software
* Beispiel: Bufferoverflow-Probleme
2. Qualitätsmängel bei der Konzeption
3. Bewusst in Kauf genommene Mängel durch das Management
* Beispiele: Reduktion des Budgets, Terminverkürzungen
4. Konfigurationsmängel
* Beispiele: Kein Einfahren von Aktualisierungen, Beibehalten von Standard-Passwörtern, Ausschalten von Sicherheitslösungen, z.B. Virenscanner

**7. Was ist ein klassischer Virus? An welchen Stellen können in einem System Viren existieren?**
* Programmstück, das sich an ein anderes Programm anfügt oder teilweise überschreibt und neben seiner Verbreitung eine Aktion durchführt
* Ein Virus kann z.b. den Read()-Syscall manipulieren, um so eigenen Code auszuführen

**8. Was ist ein Trojaner, was ist eine Hintertür (backdoor)?**
* Trojaner = Programm(teil), das neben einer offensichtlichen eine versteckte Funktion ausführt 
* Back Doors = Server, die nach Außen Dienste anbieten und dies möglichst versteckt tun

**9. Was sind Würmer (bei Netzwerken)?**
* Würmer = Programme, die von Rechner zu Rechner - auch Plattformübergreifend – kopiert werden und auf jedem Rechner eine Aktion ähnlich den von Viren durchführen

**10.Sind die heutigen Viren, die auf Visual Basic beruhen, wirklich Viren?**
Wie könnten Sie besser kategorisiert werden?
* Würmer, da sie sich verteilen

**11.Was wird unter Malware verstanden? Und was unter Spyware?**
*Malware = Shadprogramme, Zusammenfassung von (Trojanern, Back Doors, Viren, Würmer, Spyware)
*Spyware = Software, die Daten über die Benutzung des Rechners sammelt und an Dritte übermittelt oder durch Identifizierung diese Sammlung erst ermöglicht

**12. Wie arbeiten Anti-Viren-Programme? Und woher kennen eigentlich die Hersteller von Anti-Viren-Programmen die Viren bzw. die Malware? Schreiben sie diese selbst?**
* Erkennung: Mustererkennung (Signaturen) durch Virenscanner, Heuristiken (problematisch)
* Woher? : Honeypot, selbst geschrieben => unbewiesende Behauptung (eher unwahrscheinlich)

**13. Was ist ein Hoax?**
* Hoax: Scherzhafte oder böswillige Warnung vor einer fiktiven (Viren-)Gefahr

**14. Mit welchen technischen Verfahren kann die Authentifizierung realisiert werden? Nennen Sie drei Beispiele unterschiedlicher Verfahren.**
* Passwörter
* Standard, eingabe eines Passworts auf einer Website 
* Chipkarten
* EC Karte
* Biometrie
* Fingerabdruck-Scanner 

**15. Bei der Biometrie werden typische Eigenschaften des Körpers einer bestimmten Person erfasst und zur Prüfung der Identität benutzt. Welche technischen Probleme haben heute biometrische Verfahren?**
* Lassen sich teilweise einfach fälschen (siehe CCC Fingerabdruck)
* Abgeschnittener Daumen
* Unsicher, Ungenau, hohe Fehlerrate
* Nichterkennug von Lebendigkeit

**16. Welches Problem aus der Sicht des Datenschutzes ist mit biometrischen Daten verbunden - außer dass sie personenbezogen sind? Skizzieren Sie eine (fiktive?) Missbrauchsmöglichkeit biometrischer Daten.**
* Fingerabdruck lässt sich nicht ändern, falls ihn jemand klaut
* Nachweisprobleme, dass man es bei Missbrauch nicht selbst war
* Biometrie lässt sich “klauen” (Augen ausscharben) und “fälschen”

**18. Was passiert beim Social Engineering? Durch welche Maßnahmen lässt sich die Wahrscheinlichkeit für Social Engineering in einem Unternehmen vermindern? Lässt sich Social Engineering grundsätzlich verhindern?**
* Systematisches Auskundschaften des (sozialen) Umfelds der Organisation oder der Personen, die Zugang zum gewünschten System haben, sowie das Ausnutzen dieser Erkenntnisse [S. 32]
* Es lässt sich nicht grundsätzlich verhindern
* Mitarbeiter schulen (nie Passwörter rausgeben etc.), Administratoren gut bezahlen

**19. Was machen Port Scanner und was Sniffer?**
* Port Scanner scannen Ports von Computern und Servern mit Hilfe verschiedener Methoden (ICMP-Flags)
* Sniffer sammeln Netzwerkspackete und analysieren diese gegebenenfalls

**20. Beim Surfen im Web sind aktive Inhalte problematisch. Nennen Sie mindestens zwei Beispiele mit ihren Gefahren.**
* Aktive Inhalte = Programme als Teile von anderen Daten, die (unkontrolliert) nach dem Laden gestartet werden
* Javascript → XSS
* Cookies → Session-Hijacking
* Java, Flash → Sicherheitslücken (Buffer-Overflow)

**21. Was ist ein Quarantäne-Rechner? Wären Netze aus Quarantäne Rechnern sinnvoll? Falls ja, für welche Zwecke?**
* Rechner der nicht an das Netzwerk eines beispielsweise Unternehmens angeschlossen ist und für den test neuer Software eingesetzt wird (damit andere Rechner nicht infiziert werden)
* Ja, da um Software zu testen, die eine Kommunikation über Netzwerke realisiert

**22. Was ist (IP-)Spoofing?**
* Paket mit falscher Source-IP Adresse

**23. Was passiert beim Denial-of-Service-Angriff? Was bei der verteilten Version?**
* Denial of Service-Angriff = DoS-Angriff = Eine Funktion oder ein ganzes System wird außer Kraft gesetzt oder so gestört, dass die Dienstleistung nicht erbracht werden kann (Große Anzahl von Paketen, fehlerhafte ICMP Packete, fehlerhafte Handshakes)
* Distributed = das gleiche auf mehreren Systemen (Brief-Bomben, Große Anzahl verteilter Pakete)

**24. Welche Aufgaben hat eine Firewall?**
* Pakete anhand festgelegter Regeln filtern und somit keine unerwünschten Pakete erhalten/senden

**25. Was ist eine Demilitarisierte Zone (DMZ)? Was ist ein Grenznetz?**
* Grenznetz deutsche Bezeichnung für DMZ
* enthält Bastionen, Server mit Schutzfunktionen und Server mit öffentlichem Zugang

**26. Eine Firma betreibt einen eigenen Webserver. Wie würden Sie diesen Webserver mit Firewalls schützen?**
* Server in DMZ, auf keinen Fall in gleichen Netzwerk wie Firmenrechner
* Ein Firewall vor und eine hinter den Webserver, hinter 2. Firewall kommt lokales Netz

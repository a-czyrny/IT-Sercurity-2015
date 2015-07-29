
# Asymmetrische Verschlüsselung

**1. Worin besteht der wesentliche Unterschied zwischen asymmetrischen und symmetrischen Verschlüsselungsalgorithmen, wenn die Implementierungen des Verfahrens betrachtet werden?**
* Die symmetrischen Verschlüsselungsverfahren basieren auf logischen Bit-Operationen
* Die asymmetrischen Verschlüsselungsverfahren basieren darauf, dass Blöcke von Informationen als lange INTEGER-Werte aufgefasst werden, die arithmetisch nach der Modulo-Arithmetik behandelt werden.

**2. Erläutern Sie die typischen Rechenoperationen bei asymmetrischen Verschlüsselungsverfahren. Orientieren Sie sich hierbei an dem RSA-Verfahren.**
* Modulo, Eulersche Funktion, GGT, erweiterter euklidischer Algorithmus [S. Folie 36]

**3. Was wird bei der Modulo-Arithmetik (manchmal) als Modul bezeichnet?**
* der Modulowert zB 5 mod 7 --> 7 = Modul

**4. Was wird bei algebraischen Strukturen als neutrales und was als inverses Element bezeichnet? Nennen Sie jeweils ein Beispiel für die Addition und Multiplikation.**
* a ° e = a ← e neutrale Element
* 0 neutrales Element bei Addition
* a ° -a = e ← -a inverses Element

**5. Sie wollen entsprechend der Modulo-Arithmetik zwei Zahlen dividieren. Unter welcher Bedingung ist dies möglich?**
* Die Zahlen müssen Ganzzahlen sein und ungleich 0

**6. Was lässt sich durch den einfachen Euklid‘schen Algorithmus berechnen?**
* der GGT (Größter gemeinsamer Teiler)

**7. Was bedeutet teilerfremd (relativ prim)? Was bestimmt die Euler‘sche Φ-Funktion?**
* zwei Zahllen sind teilerfremd sobald sie keinen gemeinsamen Teiler außer 1 besitzen
* Φ: Anzahl der positiven ganzen Zahlen, die kleiner als n und zu n teilerfremd sind.

**8. Für welche Werte ist der Wert der Φ-Funktion sehr leicht zu berechnen?**
* für Primzahlen

**9. Wie können Sie testen, ob zwei positive ungleiche Zahlen teilerfremd sind?**

[Siehe S. 26]

* Es gilt: a^Φ(m) ≡ 1 (mod m), mit a>0 und ggT(a,m)=1

**10. Skizzieren Sie die Idee der schnellen Exponentiation. In welchen kryptographischen Verfahren wird dieses Potenzieren z.B. benötigt?**
* Exponent wird als Binärzahl dargestellt.
* Für jede 1 wird ein Summand als entsprechende 2er-Potenz berechnet.
* Dann werden alle Summanden addiert
* RSA – Kryptosystem (zur beschleunigten Berechnung)

**11. Was für ein Ziel hat das Verfahren von Diffie-Hellman?**
* Verfahren zum Schlüsselaustausch ohne Algorithmus (Public-Key-Verfahren)

**12. Lassen sich mit dem Verfahren von Diffie-Hellman Daten verschlüsseln?**
* Nein, weil es nur ein Verfahren zum Schlüsselaustausch ist

**13. Ist das Verfahren von Diffie-Hellman robust gegen den Man-in-theMiddle-Angriff?**
* Nein (Zusätliche Authentifizierung wäre notwendig)

**14. Auf welchem rechnerisch sehr aufwendigen Verfahren beruht die Sicherheit des Diffie-Hellman-Verfahrens?**
* Diskreter Logarithmus (siehe Seite 18)

**15. Beschreiben Sie den Algorithmus des Diffie-Hellman-Verfahrens in einer Freistil-Notation jeweils aus der Sicht der Kommunikationspartner.**

![DH](/img/dh.png?raw=true "Diffie-Hellman-Verfahrens")

**16. Erläutern Sie das Diffie-Hellman-Verfahren anhand eines kleinen Zahlenbeispiels.**

![DHZ](/img/dhz.png?raw=true "Diffie-Hellman-Verfahren Beispiel")

**17. Kann irgendein Schlüssel des RSA-Schlüsselpaares zum öffentlichen und der andere zum privaten gemacht werden? Bitte begründen Sie die Antwort.**
* Nein, der geheime Schlüssel wird gebildet mit einem geheimen Anteil. Würde man den geheimen Schlüssel zum öffentlichen machen, würde man diesen geheimen Anteil preisgeben

**18. Benutzt das RSA-Verfahren eine feste Schlüssellänge sowie z.B. das DES-Verfahren?**

Nein

**19. Nennen Sie für das RSA-Verfahren eine „vernünftige“ Schlüssellänge in bit.**
* mindestens 1024 Bit empfohlen

**20. Wie läuft prinzipiell die Wahl der Schlüsselpaare beim RSA-Verfahren ab. Skizzieren Sie dazu einen Algorithmus in Freistilnotation.**

(1) Wähle 2 zufällige Primzahlen p, q (100 bis 200 Dezimalstellen)
(2) Berechne n= q*p und Φ(n)=(p-1)*(q-1)
(3) Wähle ein e und berechne c, d und GGT(e, Φ(n)), so dass e*d + Φ(n)*c=GGT(e,Φ(n)) ist Erweiterter Euklid'scher Algorithmus,Falls GGT(e,Φ(n))<>1 wähle ein neues e
(4) Öffentlicher Schlüssel ist {e,n}
(5) Geheimer Schlüssel ist {d,n}

**21. Beschreiben Sie das Ver- und das Entschlüsseln nach dem RSA-Verfahren, indem Sie einen Algorithmus in Freistilnotation definieren.**

(1) p und q sind ungleiche, positive große Primzahlen: n= p * q
(2) e und d sind Î Z und so gewählt, dass d * e º 1 mod F(n)
(3) P ist Î Z+ und repräsentiert den Klartext
(4) Verschlüsseln: C = Pe MOD n
(5) Entschlüsseln: P' = Cd MOD n mit P' = P

* Öffentlicher Schlüssel: {e, n}
* Geheimer Schlüssel: {d, n}

**22. Erläutern Sie das Ver- und das Entschlüsseln nach dem RSA-Verfahren anhand kleiner Zahlen.**
* Siehe Seite 37 (und vorherige)

**23. Wie verläuft die Faktorisierungsattacke auf das RSA-Verfahren? Skizzieren Sie dessen Idee.**
* Zerlegung von n in p und q (RSA → n = p*q)
* p und q sind die beiden Primzahlen in die anhand von n faktorisiert werden soll

**24. Für das RSA-Verfahren werden zwei große zufällig gewählte Primzahlen benötigt. Sie haben eine Zufallszahl erhalten. Können Sie definitiv feststellen, ob es eine Primzahl ist? Welches Problem müssen Sie dabei lösen?**
* es ist möglich, jedoch sehr aufwändig

**25. Nehmen wir an, dass Sie aus Versehen eine nicht-Primzahl für das RSA-Verfahren gewählt haben. Was hat das für Konsequenzen?**
* nicht primzahl -> schlechte Verschlüsselung 
* mehrere Kombinationen könenn zum gleichen Ergebnis führen
* somit für Angreifer leichter

**26. Auf welchem rechnerisch sehr aufwendigen Verfahren beruht die Sicherheit des RSA-Verfahrens?**
* Die Sicherheit des RSA-Verfahrens beruht daraus, dass es rechnerisch sehr aufwändig ist, die Zahl n wieder in ihre beiden Faktoren zu zerlegen.
* siehe http://www.mathematik.uni-muenchen.de/~gerkmann/probestudium/probe1.pdf S.37

**27. Gehört das RSA-Verfahren zu den Blockchiffren? Sie wollen eine Datenbank mit RSA verschlüsseln, wie gehen Sie algorithmisch dabei vor?**
* Nein
* Für jede Tabelle einen Schlüssel
* Zeilenweise verschlüsseln

# Zufall und Zeit

**1. Wodurch unterscheidet sich ein Zufallsbitgenerator von einem Pseudozufallsbitgenerator?**
* Zufallsbitgenerator = Random Bit Generator = Gerät oder Verfahren, das eine Sequenz statistisch unabhängiger und gleich verteilter Bitfolgen erzeugt.
* Pseudozufallsbitgenerator = PZBG = Pseudo Random Number Generator = Gerät oder Verfahren, das einen deterministischen Algorithmus realisiert, als Eingabe eine zufällige Bitfolge der Länge k (Seed) erhält und eine Bitfolge der Länge l produziert, die den Eindruck der Zufälligkeit erweckt. 

**2. Wie lassen sich „echte“ Zufallszahlen auf einem PC erzeugen? Warum geht das so schwer?**
* ein PC ist eine deteministische Maschine die keinen Zufall kennt 
* einbinden von externen physikalischen Werten (z.B. Spannungsunterschiede benachbarter Halbleitern, Zugriffszeiten auf Festplatten,...)

**3. Nennen Sie ein paar Quellen für Zufall, die auf (fast) jedem PC benutzt werden können, also ohne Spezialhardware.**
* Analyse der Tastatureingaben
* Analyse von Mausbewegungen
* Uhrzeit auf ms genau
* Positionierungszeiten der Platte
* Analyse von Transfers auf dem LAN

**4. Was ist ein Seed (bei Pseudozufallsbitgeneratoren)?**
* Seed = möglichst zufälliger Startwert eines PZBG 

**5. Beschreiben Sie ein einfaches Zeitstempelverfahren mit einer dritten neutralen Partei.**

1. A erzeugt einen Hash-Wert des Dokuments .
2. A übermittelt TTP den Hash-Wert.
3. TTP fügt Datum und Uhrzeit an den Hash-Wert.
4. TTP unterschreibt das Ganze.
5. TTP übermittelt A unterschriebenen Hash-Wert mit Zeitstempel

**6. Mit dem Diffie-Helmann-Verfahren vereinbaren Sie eine Zahl, die aber als Schlüssel zu klein ist. Wie könnten Sie z.B. einen Schlüssel mit der richtigen Länge erzeugen?**
* Bilden eines Hashcodes, das jedes Mal erneut bis die Länge erreichtist
* Schlüssel als Startwert für Zufallsgenerator verwenden
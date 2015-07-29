
# Hash-Verfahren

**1. Was ist eine Authentifizierung von Nachrichten? Wird dabei auch die Integrität des Inhalts geprüft?**
* Prüfung, ob eine Nachricht in der vorliegenden Form von einer bestimmten Identität stammt, d.h. Inhalt und Herkunft werden geprüft.
* mit MAC (Message Authentication Code = MAC) wird auch integrität geprüft

**2. Wenn Sie eine Nachricht erfolgreich authentifiziert haben. Was wissen Sie dann unter welchen Bedingungen sicher?**
* Die Nachricht wurde nicht verändert und stammt vom Versender
* Bedingungen: wenn das Verfahren nicht kompromittiert und der Schlüssel nicht veröffentlicht wurde

**3. Wie sehen drei Variationen zur Benutzung von Hash-Funktionen zur Feststellung der Authentizität einer Nachricht bzw. eines Dokuments aus?**
1. Es wird ein gemeinsames Geheimnis (key) auf beiden Seiten zur Verschlüsselung des Hashwertes benutzt.

* Dies ist der symmetrischen Verschlüsselung sehr ähnlich.

2. Es wird das Prinzip der elektronischen Unterschrift (Signatur) angewandt. (Asymetrisch, Public-Private Key)
3. Es wird an die Nachricht ein Geheimnis, das beide Seiten kennen müssen, angehängt und den Hash über beide Teile gebildet.

**4. Was ist allgemein eine Hash-Funktion? Welchen weiter gehenden Bedingungen muss eine kryptographische gegenüber einer „normalen“ Hash-Funktion genügen?**
* Hash-Funktion = Funktion h(x), für die folgendes gilt:
* Kompression: Abbildung eines beliebigen Bitstrings auf einen Ausgabewert mit einer festen in der Regel kurzen Länge. Dieser ist der Hash-Wert.
* Effizienz: Für jeden Eingabewert x lasst sich die Funktion h(x) mit geringem Aufwand berechnen. Das muss nicht umgekehrt gelten.

* Kryptographische Hash-Funktion = Hash-Funktion h(x), für die zusätzlich noch folgendes gilt:
* Unbestimmbarkeit von Urbildern: Nur mit erheblichen Aufwand ist das x für ein gegebenes y bei y=h(x) zu bestimmen. 
* Unbestimmbarkeit eines weiteren Urbildes: Nur mit erheblichen Aufwand ist für ein gegebenes x ein weiteres x' zu bestimmen, wobei h(x)=h(x') gilt.
* Kollisionsfreiheit (Collision Resistance): Nur mit erheblichen Aufwand sind zwei beliebige x und x' zu bestimmen, wobei h(x)=h(x') gilt.

**5. Was ist bei Hash-Funktionen eine Kollision?**
* Wenn die Hash-Funktion ausgeführt auf verschiedene Eingaben die selben Ergebnisse liefert
* Kollision = Eine Kollision liegt vor, wenn derselbe Hash-Wert anhand verschiedener Urbilder erzeugt werden kann.

**6. Sind bei einer kryptographischen Hash-Funktion Kollisionen ausgeschlossen? Falls nicht, was für einen Sinn haben dann diese? Oder anders gefragt: worauf beruht die Sicherheit von kryptographischen Hash-Funktionen?**
* kollisionen sind theoretisch nicht ausgeschlossen 
* Praktisch haben Kollisionen nur in wenigen Fällen Relevanz, da menschlich lesbare Texte, z. B. Verträge, nur eine sehr kleine Teilmenge aller Bitkombinationen benutzen
* Nur mit erheblichen Aufwand sind zwei beliebige x und x' zu bestimmen, wobei h(x)=h(x') gilt.

**7. Unter welchen Voraussetzungen gelingt ein Angriff mittels RainbowTabellen oder allgemeiner: vorgefertigter Tabellen?**
* bei ungesalzenen Hashes

**8. Wie verläuft ein Geburtstagsangriff? Skizzieren Sie dessen Idee.**
* Es gibt zwei Nachrichten m1 und m2, wobei m1 für den Angreifer schlecht und m2 gut ist.
* Der Angreifer variiert m1 und m2 - z. B. Einfügen von Blanks oder Zeichen, die mit einem nachfolgenden Backspace unsichtbar gemacht werden o.ä. - und bestimmt die Hash-Werte.
* Nach durchschnittlich 2r/2 Versuchen, wobei r die Länge des Hash-Wertes ist, hat der Angreifer zwei Variationen m1' und m2', gefunden, die denselben Hash-Wert besitzen.
* Nun lässt der Angreifer m1' unterschreiben.
* Der Angreifer tauscht den unterschriebenen Text m1' mit dem anderen Text m2' aus...
* Um das zu verhindern, sollte man Hashverfahren nutzen, die möglichst lange Hashes erstellen (z.B. 256 Bit statt 160 Bit) -> hier ist die Wahrscheinlichkeit geringer, dass man zwei Dokumente findet, die denselben Hash haben

**9. Wenn Sie das HMAC-Verfahren anwenden: was können Sie dabei erreichen?**
* Unveränderter Gebrauch verfügbarer Hash-Funktionen
* Ersetzbarkeit durch andere Hash-Funktionen
* Einfache Verwendung von Schlüsseln
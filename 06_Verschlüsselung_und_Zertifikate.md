# Verschlüsselung und Zertifikate

**1. Lassen sich allein mit symmetrischen Verschlüsselungsverfahren Dokumente signieren? Was ist das Charakteristische dieser Verfahren?**
* Nein, da die Signatur nur bei der asymmetrischen Verschlüsselung funktioniert
* die Signatur wird für die zur Überprüfung der Integrität genutzt
* dazu wird ein privater Schlüssel benötigt, der einer Person zugeordent sein muss
* bei der symmetrischen Verschlüsselung kennen beide Personen den Schlüssel und bestitzen keinen privaten
* Symmetrische Verschlüsselung = Verschlüsselung mit einem Schlüssel zum Ver- und Entschlüsseln (SSL, DES, AES)
* Asymmetrische Verschlüsselung = Verschlüsselung mit einem öffentlichen Schlüssel und Entschlüsselung mit einem privaten Schlüssel

**2. Wie arbeiten asymmetrische Verschlüsselungsverfahren?**
* Bei der asymmetrischen Verschlüsselung wird ein Schlüsselpaar verwendet, das folgende Eigenschaften hat:
* Es ist zufällig gewählt.
* Aus dem einen Schlüssel kann nicht der andere rekonstruiert werden.
* Wenn ein Text mit dem einen Schlüssel verschlüsselt wurde, kann er nur von dem anderen entschlüsselt werden
* Einer der beiden Schlüssel wird öffentlich gemacht, der andere bleibt geheim:
* Public Key = Schlüssel einer Identität, der bekannt gegeben werden kann
* Secret Key = Geheimer Teil des Schlüsselpaares, der immer gegenüber allen anderen Identitäten geheim gehalten werden muss

**3. Worin besteht der wesentliche Unterschied zwischen der symmetrischen und der asymmetrischen Verschlüsselung?**

Bei der symmetrischen Verschlüsselung wird derselbe Schlüssel für die Ver- und Entschlüsselung verwendet. Diese murr beiden Teilnehmern bekannt sein. Bei der asymetrischen Verschlüsselung verfügen die Teilnehmer über ein Schlüsselpaar (Public- / Privatkey). Die Verschlüsselung erfolgt jeweils mit dem Public-Key des anderen Teilnehmers und die Entschlüsselung mit dem eignen Privat-Key.

**4. Wie läuft das elektronische Unterschreiben eines Dokuments ab? Beschreiben Sie die einzelnen Schritte.**
* Bilden eines Hash-Werts der zu verschickenden Nachricht
* Verschlüsselung mit Private-Key
* Versand der Signatur und der verschlüsselten Nachricht

**5. Wie läuft die Prüfung einer elektronischen Unterschrift eines Dokuments ab? Beschreiben Sie die einzelnen Schritte.**
* Empfangende Signatur des Hash-Wertes wird mit dem öffentlichen Schlüssel des Absenders entschlüsselt
* Ist Verifizierung erfolgreich, dann ist die Nachricht vom Absender

**6. Was ist ein Schlüssel, was eine Signatur und was ein Zertifikat?**
* Schlüssel 
* Bitkette, deren Werte statistisch gleich verteilt und lang genug ist, um nicht unter definierten Bedingungen durch Ausprobieren bestimmt werden zu können
* Signatur
* Wird nun ein Fingerabdruck mit dem geheimen Schlüssel verschlüsselt, so wird das Resultat digitale Unterschrift oder Signatur genannt
* Eine Signatur ist deshalb eindeutig, da nur derjenige, der im Besitz des geheimen Schlüssels ist, in der Lage ist, sie zu erstellen.
* Zertifikat 
* besteht aus Identität, öffentlichem Schlüssel der Identität und Signatur der CA

**7. Welche Aufgaben hat eine CA? Wofür steht das Kürzel CA? Und was ist ein Trustcenter?**
* Eine Certification Authority (CA) - oder Trustcenter genannt - hat ein Verzeichnis von öffentlichen Schlüsseln samt Identitätsbeschreibungen und beglaubigt die Verbindung zwischen Identität und öffentlichen Schlüssel durch ein Zertifikat.

**8. Werden beim Erstellen einer Signatur die Nutzdaten verschlüsselt?**
* Nur signieren: Nein

**9. Lassen sich Zertifikate fälschen? Skizzieren Sie dazu ein Verfahren.**
* Variante 1: in eine CA einbrechen und sich selbst eins ausstellen
* Variante 2: geheimen Schlüssel zum öffentlichen finden

**10. Wie erhält eine Person das Zertifikat eines Schlüssels einer fremden Person? Nennen Sie mindestens zwei Möglichkeiten, die möglichst legal sind.**
1. Server, der Cert hat übergibt es beim Handshake an den Client (falls Client ein Cert hat, kann er es auch gleich übergeben)
2. Zertifikats- und FTP-Server, wo Zertifikate runtergeladen werden können (da öffentliche Dokumente)

**11. Unter welchen Umständen müssen Zertifikate noch innerhalb ihres Gültigkeitszeitraums zurückgenommen werden? Nennen Sie dazu zwei Beispiele.**
* Geheimer Schlüssel der Identität ist aufgedeckt
* Identität wird von CA nicht länger akzeptiert
* Geheimer Schlüssel der CA ist aufgedeckt

**12. Wie wird das Zurücknehmen ausgegebener Zertifikate realisiert? Was bedeutet das für den Prozess des Prüfens eines Zertifikats?**
* Ein Rückruf muss bei der CA vorgenommen werden und wird in eine entsprechende Liste eingetragen
* Bei der Überprüfung des Zertifikats wird geprüft, ob es einen Rückruf zum Zertifikat gab

**13. Was muss alles getan werden, um die Korrektheit eines Zertifikats prüfen?**
* Wie kann sich Person A von der Glaubwürdigkeit des Zertifikats überzeugen? Indem A mit dem öffentlichen Schlüssel vom Trustcenter dessen Unterschrift prüft (mit demselben Verfahren, wie jede Unterschrift geprüft wird).
* Dadurch entsteht eine Kette von Zertifikaten, die sich jeweils – bis auf das erste – bestätigen. Das erste muss geglaubt werden

**14. Warum sind im X.509-Zertifikat Angaben zu den verwendeten kryptographischen Verfahren enthalten?**
* das Verfahren soll austauschbar bleiben, falls ein verfahren sich als angreifbar heraustellt soll einfach ein anderes benutzt werden können

**15. In einem X.509-Zertifikat sind u.a. persönliche Daten, wie z.B. die EMail-Adresse enthalten. Ist das nicht Futter für die Spammer, die nun geprüfte Mailadressen erhalten?**
* Ja
* Aber Attributzertifikate können helfen (Firmenintern)

**16.Nennen Sie zwei symmetrische Verschlüsselungsverfahren, die weite Verbreitung gefunden haben.**
* Diffie-Hellman-Verfahren
* RSA-Verfahren

**17. Wenn zwei Personen über weite Entfernungen ihre Kommunikation mit einem symmetrischen Verfahren verschlüssel wollen: welches schwerwiegendes Problem muss dazu gelöst werden?**

Sichere Übermittlung des Schlüssels.

**18.Wie können zwei sich nicht persönlich kennende Personen ein Geheimnis, z.B. einen Schlüssel oder ein Passwort, austauschen, ohne dass Fremde das Geheimnis erfahren?**

Mit dem Diffie-Hellman Verfahren (A und B einigen sich auf einem Prim- und natürliche Zahl welche öffentlich sind)

**19.Skizzieren Sie das Prinzip des Man-in-the-Middle-Angriffs.**

Der Kommunikationskanal zweier Teilnehmer wird durch einen dritten abgehört. Hierbei können die Nachrichten durch diesen auch manipuliert werden.

**20.Beschreiben Sie ein möglichst sicheres Verfahren, mit dem Sie feststellen können, mit wem Sie kommunizieren.**

Signierung mit asynchroner Verschlüsselung (Privatkey-Signierung eines Hashes).

**21.Wie werden die Organisationen bzw. Firmen genannt, die Zertifikate heraus geben? Auf welche Weise prüfen diese Organisationen, ob die im Zertifikat angegebenen Personen tatsächlich die richtigen sind? Machen Sie dazu einen Vorschlag.**
* CA - certificate authority
* Persönliche Identifikation gegenüber der CA (z.B. Personaldokumente z.B. Personalausweis)

**22. Was wird unter einem Zertifizierungpfad verstanden?**
* Die Echtheit und Unversehrtheit eines Zertifikates, also des mitgesendeten öffentlichen Schlüssels, wird über die Signatur des Herausgebers geprüft: Jedes persönliche Zertifikat ist von einem Trustcenter (CA) signiert. Ist diese Signatur gültig, wurde auch das Zertifikat nicht geändert. Natürlich kann auch die Echtheit des Herausgeberzertifikats geprüft werden, das oft wieder von einer anderen Instanz herausgegeben wurde.
* Ermöglicht die Rückverfolgung zum Ersteller / Aussteller.

**23. Jemand möchte elektronisch sein Testament machen. Welche technischen Probleme müssen dabei überwunden werden? Machen Sie einen Vorschlag zur Lösung.**
* Es muss sichergestellt werden, dass der öffentliche Schlüssel einer Person wirklich dieser gehört
* Über den Eintrag in eine CA kann sichergestellt werden, dass die Identität der Person und des öffenltichen Schlüssels übereinstimmen
* (Wenn der CA vertraut wird!!!!)
* Uhrzeit muss vor Tod sein
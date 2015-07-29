
# Symmetrische Verschlüsselung

**1. Worin besteht ein Ciphertext-Only-Angriff bzw. worin ein KnownPlaintext-Angriff?**
* Ciphertext-Only-Attack (Geheimtextanalyse): Der Angreifer kennt nur den Chiffretext.
* Dies ist der häufigste und schwierigste Angriff.
* Es wird u.a. ausgenutzt, dass bestimmte Eigenschaften des Klartextes bei der Verschlüsselung erhalten bleiben.
* Ziel: möglichst viele Klartextanteile oder den Schlüssel bestimmen

* Known-Plaintext-Attack: Der Angreifer kennt zu einem Chiffretext den Klartext bzw. einen Teil davon.
* Öfter vorkommenden Passagen, wie z.B. Anreden, Grüße
* Response-Challenge-Verfahren
* Bekannt sind Paare von Chiffre-/Klartexten mit demselben Schlüssel

**2. Schildern Sie eine Situation bzw. ein Verfahren, bei dem Sie als Angreifer mindestens ein Paar(Cipher-Text,Plain-Text) zu einem bestimmten Schlüssel (leicht) erhalten, das Sie zum Brechen der Verschlüsselung benutzen können.**
* Challenge and Response verfahren

**3. Beschreiben Sie das Verfahren der Verschlüsselung bei One-TimePads? Sind diese sicher?**
* Ja, da einmalig verwendet (keine Analyse über mehrere verschlüsselte Texte möglich → Übereinstimmungen)
* Es wird eine Tabelle (Pad) mit wirklich zufälligen Zeichen der Länge L erstellt.
* Der Klartext hat dieselbe Länge L.
* Verschlüsselung:
* Jedes Zeichen des Klartextes wird mit dem korrespondierenden Zeichen der Tabelle verknüpft, z. B. per XOR.
* Entschlüsselung:
* Jedes Zeichen des Chiffretextes wird mit dem korrespondierenden Zeichen der Tabelle mit einer inversen Funktion verknüpft, z. B. auch per XOR

**4. Worin liegen die wesentlichen Probleme bei der Benutzung von OneTime-Pads? Nennen Sie zwei.**
* beide Seiten müssen den Schlüssel besitzen (Tabelle)
* nur einmalig verwendbar
* Schlüssel wächt proportional zum zu verschlüssselnden Text

**5. Was ist eine Blockchiffre und was eine Stromchiffre?**
* Blockchiffre = Unabhängige Verschlüsselung von Blöcken gleicher Länge, meist 64 bit
* Jeder Block wird für sich getrennt von anderen behandelt.
* Die kryptographischen Nachteile werden durch Blockmodi beseitigt.
* Stromchiffre = Kontinuierliche Verschlüsselung unterschiedlich langer Blöcke, von 1 bit bis viele Bytes auch variierend

**6. Bei welchen Anwendungen sollten am besten Block- und bei welchen eher Stromchiffren eingesetzt werden?**

**Stromchiffre**

* es muss sich keine bestimmte Datenmenge angesammelt haben, damit die Verschlüsselung erfolgen kann
* es kann bereits nach den ersten Bits starten
* Bsp.: Echtzeitübertragung Mobilfunk
* Blockchiffre:
* Bei großen Datenbeständen (Dateien)

**7. Erläutern Sie die typischen Bitoperationen bei symmetrischen Verschlüsselungsverfahren.**
* XOR-Verknüpfung 
* Permutation (Änderung der Bitreihenfolge)
* Substitution (Ersetzen der Bitfolge)

**8. Charakterisieren Sie das DES-Verfahren anhand der Schlüssellänge, Blocklänge und Sicherheit.**
* 56 Bit Schlüssellänge
* 64 Bit Blocklänge
* nicht mehr sicher genug (Ablösung furch AES)

**9. Worin liegt das größte Problem beim DES?**
* Schlüssellänge zu gering

**10. Wodurch unterscheidet sich das DES-Verfahren bei der Ver- und Entschlüsselung?**
* Teilschlüssel werden in umgekehrter Reihenfolge angewandt

**11. Wenn Sie einen Datenblock mit zwei Schlüsseln zwei Mal hintereinander mithilfe des DES-Verfahrens verschlüsseln, verdoppelt sich damit die effektive Schlüssellänge?**
* Nein, da Meet-in-the-middle-Angriff (durch Probieren aufgrund des bekannten und unverschlüsselten Textes)

**12. Was wird unter effektiver Schlüssellänge gemeint?**
* Reduktion des Schlüssels (2x DES ist 57, statt normaler 2x56 = 112)

**13.Wie groß ist etwa die effektive Schlüssellänge von 2DES (zwei-fachmit zwei unterschiedlichen Schlüsseln) und wie die von 3DES (dreifachmit zwei Schlüsseln)?**
* 2xDES: 57 Bit Schlüssellänge
* 3xDES: 112 Bit Schlüssellänge 

**14.Worin besteht die Idee des Meet-in-the-Middle-Angriffs? Skizzieren Sie das Verfahren anhand eines fiktiven Beispiels.**
* Für den Meet-In-the-Middle-Angriff wird der ein Paar des unverschlüsselten und verschlüsselten Textes benötigt
* Ausgehend von einer 2xDES-Verschlüsselung werden alle 256 Varianten für den unverschlüsselten Text durchprobiert und in einer Datenbank gespeichert
* Anschließend werden auch alle 256 Varianten für den verschlüsslten Text probiert und in einer weiteren Datenbank gespeichert, da es mehrere mögliche Kandidaten gibt
* Mit einem weiteren Paar aus unverschlüsselten und verschlüsslten Text kann die Liste der möglichen Kandidaten eingeschränkt werden

**15. Wie arbeitet das üblich Triple-DES (3DES)? Welche effektive Schlüssellänge wird dabei benutzt?**
* 3xDES mit 2 Schlüsseln: 112Bit Schlüssellänge
* 1. A = Verschlüsselung des Klartextes mit einem 56Bit Schlüssel K1
* 2. B = Entschlüsselung des verschlüsselten Text A mit mit K2
* 3. C = Verschlüsselung des verschlüsselten Text B mit K3
* K1 = K3

**16. Welchen Vorteil und welchen Nachteil hat das 3DES-Verfahren?**
* Vorteil: auch nach heutigem Standard sichere Verschlüsselung
* Nachteil: wegen der dreifachen verschlüsselung auch dreimal zeitaufwändiger als DES 

**17. Was beschreibt eine Betriebsart?**
* Betriebsart = Verfahren, das beschreibt, wie mit einer Blockchiffre Nachrichten verschlüsselt werden

**18. Worin besteht der Grund zur Benutzung von Betriebsarten bei der Verschlüsselung?**
* Erst die Kombination von Blockchiffre und Betriebsmodus erlaubt es, Nachrichten zu verschlüsseln, die länger sind als die Blocklänge

**19.Was charakterisiert die Betriebsart Electronic Codebook (ECB)? Welches Problem hat diese Betriebsart?**

**Probleme**

* Angriff durch Häufigkeitsanalyse
* Gleiche Blöcke werden gleich verschlüsselt

**20. Beschreiben Sie das Verfahren der Betriebsart Output-FeedbackMode (OFD).**
1. Verschlüsselung eines Intalivektors I (128Bit) = I1
2. XOR Verknüpfung von I1 mit Klartextblock K1 = E2 (erster verschlüsselter Block)
3. Verschlüsselung des verschlüsselten Initialsverkors I1 = I2
4. XOR Verknüpfung von I2 mit Klartextblock K2 = E3 (zweiter verschlüsselter Block)
5. siehe 3. mit I2 und 4. mit I3 und K3

![OFD](/img/ofd.png?raw=true "Output-FeedbackMode")

**21. Was macht die Betriebsart Output-Feedback-Mode (OFD) so performant? Hat der Electronic Codebook (ECB) denselben Performanzvorteil?**
* Die Verschlüsselungsketten können im Voraus/parallel berechnet werden, so dass hohe Parallelität erreicht werden kann.
* Klartexte können mit ECB auch parallel verschlüsselt werden, da die Nachricht in 128Bit-Blöcke aufgeteilt wird und jeder Block mit dem gleichen Schlüssel verschlüsselt wird

**22. Beschreiben Sie das prinzipielle Ablaufschema für die Verschlüsseling bei Stromchiffren.**
* sofortige Verarbeitung des Klartextes ohne auf eine bestimmte Blocklänge zu warten
* Stromchiffren = Verschlüsselungsalgorithmen, die keine Einheiten mit festgelegter Größe (Blöcke) benötigen und bei denen die Einheiten ähnlich den Blockmodi verknüpft sind.

![SC](/img/sc.png?raw=true "Stromchiffren")

**23. Nennen Sie ein Beispiel für ein Stromchiffre-Verfahren.**
* RC4

**24. In welchem Zusammenhang stehen Stromchiffre-Verfahren und Pseudozufallsgeneratoren?**
* Forschaltfuntion erzeugt ähnlich wie ein Pseudozufallsgenerator aus einem übergebenen Startwert zufällige Werte (mit denen Ver-/Entschlüsselt wird)
* Forschaltfunktion muss beiden Parteien bekannt sein
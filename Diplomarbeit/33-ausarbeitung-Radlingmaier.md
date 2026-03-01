# Teilaufgabe Schüler Radlingmaier
\textauthor{Radlingmaier Christian}

## Theorie

Dieses Kapitel dient der Vermittlung der notwendigen Grundlagen, die ein fachlich versierter Leser benötigt, um die praktische Umsetzung des Projekts nachvollziehen zu können. Es fasst relevante theoretische Inhalte zusammen und stellt sicher, dass ein durchgängiger und logisch aufgebauter Zusammenhang zwischen den einzelnen Themenbereichen entsteht.

Behandelt werden dabei unter anderem:
- grundlegende Begriffsdefinitionen
- eingesetzte Software-Frameworks
- fachbezogene Methoden und Vorgehensweisen


Darüber hinaus werden in diesem Kapitel sowohl die theoretischen als auch die praktischen Grundlagen zur Realisierung eines Smart-Home-Systems für ein Modellhaus vorgestellt. Ergänzend wird aufgezeigt, inwiefern sich die beschriebenen Konzepte auf ein reales Wohngebäude übertragen lassen.

Ein besonderer Schwerpunkt liegt auf der Installation und Nutzung von Docker auf einem Raspberry Pi sowie auf der Kommunikation zwischen dem Raspberry Pi, dem Arduino Uno und den angebundenen Sensoren und Aktoren.

### Verwendete Aktoren

- 100Pcs 1/4W 5% Toleranz 150Ohm Wiederstand
- 3mm Leuchtdioden

### Zusätzlich Benötigt

- IWILCS Dupont Crimp Set 790tlg inkl. Crimpzange
- Kabel 0,5mm²
- 4x PLA Basic Hellgrau (10104)
- 2x PLA Basic Dunkelgrau (10105)

### Verwendete Frameworks

- FHEM:
- Node-Red:   
- MQTT:
- Portainer:

# Teilaufgabe – Smart-Home-Umsetzung mit FHEM und Node-RED

**Schüler:** Christian Radlingmaier

## Theoretische Grundlagen
Unter einem Smart Home versteht man ein Haus, in dem verschiedene technische Komponenten miteinander vernetzt sind und zentral überwacht sowie gesteuert werden können. Diese Steuerung kann sowohl automatisch durch definierte Abläufe als auch manuell durch den Nutzer erfolgen. So ist es beispielsweise möglich, Beleuchtung oder Heizsysteme über ein mobiles Endgerät zu bedienen oder Rollläden zeitgesteuert automatisch zu bewegen.

In dieser Diplomarbeit kommt ein Arduino als Mikrocontroller zum Einsatz, der für die Erfassung von Sensordaten sowie die Ansteuerung von Aktoren verantwortlich ist. Als zentrale Kontrolleinheit dient ein Raspberry Pi, auf dem die Smart-Home-Software FHEM betrieben wird. FHEM übernimmt die zentrale Verwaltung der angeschlossenen Geräte, verarbeitet eingehende Daten und setzt definierte Automatisierungsregeln um.

Der Datenaustausch zwischen den einzelnen Systemkomponenten erfolgt über das MQTT-Protokoll. Dieses ermöglicht eine effiziente und zuverlässige Kommunikation zwischen Sensoren, Aktoren und der zentralen FHEM-Instanz.

### Sensorik, Aktorik und Steuerung    

#### Sensorik
Sensorik bildet eine zentrale Grundlage eines Smart-Home-Systems, da sie die Erfassung von physikalischen und umgebungsbezogenen Zuständen ermöglicht. Sensoren dienen dazu, Informationen aus der realen Umgebung aufzunehmen und diese in elektrische Signale umzuwandeln, die von Mikrocontrollern oder zentralen Steuereinheiten weiterverarbeitet werden können.

In Smart-Home-Anwendungen kommen unterschiedliche Sensortypen zum Einsatz. Dazu zählen unter anderem Temperatursensoren, Feuchtigkeits- und Helligkeitssensoren sowie Bewegungs- und Kontaktsensoren. Diese erfassen kontinuierlich relevante Umgebungsdaten, die als Grundlage für automatisierte Entscheidungen und Steuerungsprozesse dienen.

Die erfassten Sensordaten werden in der Regel von Mikrocontrollern, wie beispielsweise einem Arduino, ausgelesen und anschließend an eine zentrale Automatisierungsplattform übertragen. Dort können die Daten analysiert, visualisiert und für die Umsetzung von Automatisierungsregeln genutzt werden. Auf diese Weise ist es möglich, auf bestimmte Zustände gezielt zu reagieren, etwa durch das Einschalten der Beleuchtung bei Bewegung oder das Anpassen der Heizleistung in Abhängigkeit von der Raumtemperatur.

Ein wesentlicher Vorteil moderner Sensorik ist ihre hohe Genauigkeit sowie der geringe Energieverbrauch. In Kombination mit standardisierten Kommunikationsprotokollen lassen sich Sensoren flexibel in bestehende Smart-Home-Systeme integrieren und bei Bedarf erweitern.

In dieser Diplomarbeit wird Sensorik eingesetzt, um relevante Umgebungsparameter zu erfassen und als Grundlage für die Automatisierung und Steuerung innerhalb des Smart-Home-Systems zu dienen.

#### Aktorik
Aktorik bezeichnet die Gesamtheit aller Komponenten in einem Smart-Home-System, die auf Basis von Steuerbefehlen physische Aktionen ausführen. Aktoren setzen digitale Signale aus der Steuerungslogik in konkrete mechanische, elektrische oder optische Vorgänge um und stellen damit das Gegenstück zur Sensorik dar.

In Smart-Home-Anwendungen werden unterschiedliche Aktortypen eingesetzt. Dazu zählen unter anderem Relaismodule zum Schalten von elektrischen Verbrauchern, Aktoren für Beleuchtungssysteme, Motoren zur Steuerung von Rolllaeden sowie Stellventile für Heizungs- oder Lueftungssysteme. Diese Aktoren reagieren auf Steuerbefehle, die entweder manuell durch den Benutzer oder automatisch durch definierte Regeln ausgelöst werden.

Die Ansteuerung der Aktoren erfolgt in der Regel über Mikrocontroller wie den Arduino, der die von der zentralen Steuereinheit empfangenen Befehle interpretiert und entsprechende Schaltsignale erzeugt. Die zentrale Steuerlogik wird dabei von einer Automatisierungsplattform wie Node-RED oder FHEM übernommen, während die Kommunikation häufig über das MQTT-Protokoll realisiert wird.

Ein wichtiger Aspekt der Aktorik ist die Zuverlässigkeit und Sicherheit der ausgefuehrten Aktionen. Insbesondere bei netzspannungsbetriebenen Geraeten muessen geeignete Schutzmaßnahmen, wie Relais mit ausreichender Belastbarkeit, beruecksichtigt werden. Dadurch wird ein sicherer Betrieb des Smart-Home-Systems gewaehrleistet.

In dieser Diplomarbeit wird Aktorik eingesetzt, um auf Basis von Sensordaten und definierten Automatisierungsregeln gezielt in die Umgebung einzugreifen und den gewuenschten Komfort-, Sicherheits- und Energieeffizienzgewinn zu realisieren.

#### Steuerung(Arduino UNO)
Die Steuerung stellt eine zentrale Funktion innerhalb des Smart-Home-Systems dar und ist für die Verarbeitung von Sensordaten sowie die Ansteuerung der Aktoren verantwortlich. In dieser Diplomarbeit wird der Arduino Uno als Mikrocontroller eingesetzt, um diese Aufgaben zuverlässig und effizient zu übernehmen.

Der Arduino Uno fungiert als dezentrale Steuereinheit, an die verschiedene Sensoren und Aktoren angeschlossen sind. Die vom System erfassten Sensordaten werden vom Mikrocontroller eingelesen, vorverarbeitet und anschließend an die zentrale Automatisierungsplattform weitergeleitet. Gleichzeitig empfängt der Arduino Uno Steuerbefehle von der Zentrale und setzt diese in entsprechende Schalt- oder Regelvorgänge um.

Die Programmierung des Arduino Uno erfolgt über die Arduino-Entwicklungsumgebung und ermöglicht eine strukturierte Umsetzung der Steuerungslogik. Der Mikrocontroller arbeitet dabei ereignisgesteuert und reagiert auf definierte Zustände oder empfangene Nachrichten. Die Kommunikation mit der zentralen Steuerungseinheit erfolgt über standardisierte Schnittstellen und Protokolle, beispielsweise unter Verwendung von MQTT.

Durch den Einsatz des Arduino Uno wird eine klare Trennung zwischen der hardwarebezogenen Steuerungsebene und der zentralen Automatisierungs- und Logikebene erreicht. Dies erhöht die Modularität des Systems und erleichtert sowohl Erweiterungen als auch Wartungsarbeiten.

In dieser Diplomarbeit übernimmt der Arduino Uno somit die Aufgabe der direkten Steuerung von Sensoren und Aktoren und bildet die Verbindung zwischen der physischen Umgebung und der übergeordneten Smart-Home-Logik.

#### Raspberry Pi
Der Raspberry Pi ist ein kompakter Einplatinencomputer, der für eine Vielzahl von Anwendungen im Bildungs-, Entwicklungs- und Embedded-Bereich eingesetzt wird. Trotz seiner geringen Größe bietet er ausreichende Rechenleistung, um als zentrale Steuereinheit in Smart-Home-Systemen zu fungieren. Der Betrieb erfolgt in der Regel mit einem Linux-basierten Betriebssystem, wodurch der Einsatz zahlreicher Open-Source-Anwendungen möglich ist.

Im Rahmen dieser Diplomarbeit übernimmt der Raspberry Pi die Rolle der zentralen Steuer- und Kommunikationseinheit. Auf ihm werden mehrere Dienste ausgeführt, darunter Automatisierungs- und Management-Software wie Node-RED, MQTT-Broker sowie weitere containerisierte Anwendungen. Durch den Einsatz von Docker können diese Dienste voneinander getrennt betrieben und effizient verwaltet werden.

Der Raspberry Pi ist für die Verarbeitung und Weiterleitung von Sensordaten verantwortlich und stellt die Verbindung zwischen den dezentralen Mikrocontrollern, wie dem Arduino Uno, und der zentralen Steuerlogik her. Über standardisierte Netzwerkprotokolle werden Daten empfangen, verarbeitet und Steuerbefehle an die entsprechenden Aktoren weitergegeben.

Ein weiterer Vorteil des Raspberry Pi ist seine geringe Leistungsaufnahme bei gleichzeitig hoher Flexibilität. Dank integrierter Netzwerk- und Schnittstellenfunktionen kann er problemlos in bestehende Smart-Home-Infrastrukturen integriert und bei Bedarf erweitert werden.

Aufgrund seiner Vielseitigkeit, der guten Unterstützung durch die Community sowie der Eignung für den Dauerbetrieb wird der Raspberry Pi in dieser Diplomarbeit als zentrale Plattform für den Betrieb und die Koordination des Smart-Home-Systems eingesetzt 

### Frameworks

#### FHEM
FHEM ist ein quelloffenes Smart-Home-Framework, das zur Steuerung, Überwachung und Automatisierung von Haus- und Gebäudetechnik eingesetzt wird. Die Software wird überwiegend auf Linux-basierten Systemen betrieben, wie beispielsweise einem Raspberry Pi, und fungiert als zentrale Steuereinheit innerhalb eines Smart-Home-Systems.

Das Framework ist modular aufgebaut und unterstützt eine Vielzahl von Geräten, Protokollen und Kommunikationsschnittstellen. Dadurch können sowohl Sensoren (z. B. Temperatur- oder Bewegungssensoren) als auch Aktoren (z. B. Relais, Heizungsventile oder Beleuchtungssysteme) in das System integriert werden. Die Verwaltung dieser Komponenten erfolgt zentral über FHEM.

Ein wesentliches Merkmal von FHEM ist die flexible Automatisierungslogik. Mithilfe von Regeln, Zeitplänen und Ereignissen können Abläufe definiert werden, die automatisch auf bestimmte Zustände oder Sensordaten reagieren. Zusätzlich bietet FHEM verschiedene Möglichkeiten zur Benutzerinteraktion, etwa über eine webbasierte Oberfläche oder externe Anwendungen.

Die Kommunikation zwischen FHEM und externen Geräten kann über unterschiedliche Protokolle erfolgen. In dieser Diplomarbeit wird hierfür das MQTT-Protokoll verwendet, da es eine effiziente und zuverlässige Datenübertragung zwischen Mikrocontrollern, Sensoren und der FHEM-Zentrale ermöglicht.

Aufgrund seiner Offenheit, Erweiterbarkeit und großen Community eignet sich FHEM besonders für individuelle und anpassbare Smart-Home-Lösungen. Aus diesen Gründen wurde FHEM als zentrale Automatisierungsplattform für diese Diplomarbeit ausgewählt.

#### Node-RED
Node-RED ist ein quelloffenes, ereignisgesteuertes Entwicklungsframework, das insbesondere im Bereich Smart Home und Internet of Things (IoT) eingesetzt wird. Es ermöglicht die grafische Erstellung von Steuerungs- und Automatisierungslogiken mithilfe eines webbasierten Editors. Die einzelnen Funktionsbausteine, sogenannte Nodes, werden per Drag-and-Drop miteinander verbunden und bilden gemeinsam sogenannte Flows, welche den Daten- und Kontrollfluss innerhalb des Systems abbilden.

Innerhalb eines Smart-Home-Systems übernimmt Node-RED die Verarbeitung von Sensordaten sowie die Umsetzung von logischen Abläufen. Eingehende Informationen, beispielsweise von Temperatur- oder Bewegungssensoren, können analysiert, gefiltert und anschließend zur Steuerung von Aktoren wie Beleuchtung, Heizung oder Rollläden verwendet werden. Dadurch lassen sich sowohl einfache Automatisierungen als auch komplexe Abhängigkeiten realisieren.

Ein wesentlicher Vorteil von Node-RED ist die Unterstützung zahlreicher Kommunikationsprotokolle und Schnittstellen. Dazu zählen unter anderem MQTT, HTTP sowie WebSockets, wodurch eine einfache Integration von Mikrocontrollern, Smart-Home-Zentralen und externen Diensten möglich ist. In dieser Diplomarbeit wird Node-RED insbesondere zur Verarbeitung von MQTT-Nachrichten und zur Umsetzung der Steuerlogik eingesetzt.

Zusätzlich besteht die Möglichkeit, eigene Funktionslogiken mithilfe von JavaScript zu implementieren, wodurch Node-RED flexibel erweitert werden kann. Über optionale Erweiterungen wie Dashboards können zudem grafische Benutzeroberflächen zur Visualisierung von Daten und zur manuellen Steuerung erstellt werden.

Aufgrund seiner übersichtlichen grafischen Programmierumgebung, der hohen Erweiterbarkeit und der aktiven Community eignet sich Node-RED besonders für die Entwicklung individueller Smart-Home-Lösungen. Daher wird das Framework in dieser Diplomarbeit als zentrales Werkzeug zur Umsetzung von Automatisierungs- und Steuerungsprozessen verwendet. 

#### MQTT
MQTT (Message Queuing Telemetry Transport) ist ein leichtgewichtiges, ereignisbasiertes Kommunikationsprotokoll, das speziell für den Einsatz in ressourcenbeschränkten Systemen entwickelt wurde. Aufgrund seines geringen Overheads und der hohen Zuverlässigkeit wird MQTT häufig in Smart-Home- und Internet-of-Things-Anwendungen eingesetzt.

Das Protokoll basiert auf dem sogenannten Publish-Subscribe-Prinzip. Dabei kommunizieren die einzelnen Geräte nicht direkt miteinander, sondern über eine zentrale Instanz, den sogenannten Broker. Sensoren oder andere Datenquellen senden ihre Informationen als Nachrichten (Publish) an den Broker, während andere Komponenten diese Nachrichten abonnieren (Subscribe). Die Zuordnung erfolgt über eindeutig benannte Themen (Topics).

In einem Smart-Home-System ermöglicht MQTT eine klare Trennung zwischen Datenerfassung und Steuerlogik. Sensoren, beispielsweise Mikrocontroller wie ein Arduino, senden Messwerte an den MQTT-Broker, während zentrale Systeme wie Node-RED oder FHEM diese Daten empfangen, verarbeiten und entsprechende Steuerbefehle an Aktoren weiterleiten. Dadurch entsteht eine flexible und skalierbare Kommunikationsstruktur.

Ein weiterer Vorteil von MQTT ist die Unterstützung verschiedener Qualitätsstufen (Quality of Service), die festlegen, wie zuverlässig Nachrichten übertragen werden. Zusätzlich bietet das Protokoll Mechanismen wie Retained Messages und Last Will, die insbesondere in Smart-Home-Systemen zur Erhöhung der Ausfallsicherheit beitragen.

Aufgrund seiner Effizienz, der einfachen Implementierung und der guten Integration in bestehende Smart-Home-Frameworks eignet sich MQTT besonders für die Kommunikation zwischen Sensoren, Aktoren und zentralen Steuerungssystemen. Aus diesen Gründen wird MQTT in dieser Diplomarbeit als zentrales Kommunikationsprotokoll für den Datenaustausch innerhalb des Smart-Home-Systems eingesetzt.


#### Portainer
Portainer ist eine webbasierte Management- und Verwaltungsplattform zur einfachen Administration von containerbasierten Anwendungen. Die Software wird hauptsächlich in Verbindung mit Docker eingesetzt und ermöglicht es, Container, Images, Netzwerke und Volumes über eine grafische Benutzeroberfläche zu verwalten. Dadurch wird die Nutzung von Container-Technologien auch ohne tiefgehende Kommandozeilenkenntnisse erleichtert.

Im Smart-Home-Umfeld eignet sich Portainer besonders für den Betrieb und die Organisation mehrerer Dienste auf einer zentralen Steuereinheit, wie beispielsweise einem Raspberry Pi oder einem Server. Anwendungen wie Node-RED, MQTT-Broker oder FHEM können in separaten Containern betrieben und über Portainer übersichtlich verwaltet werden. Dies erhöht die Wartbarkeit und Übersichtlichkeit des Gesamtsystems.

Ein wesentlicher Vorteil von Portainer ist die vereinfachte Bereitstellung und Aktualisierung von Containern. Neue Dienste können schnell gestartet, bestehende Container neu konfiguriert oder aktualisiert werden, ohne das gesamte System neu aufzusetzen. Zudem ermöglicht Portainer das Überwachen von Ressourcen wie CPU-Auslastung, Arbeitsspeicherverbrauch und Laufzeiten der einzelnen Container.

Durch die Trennung der einzelnen Anwendungen in eigenständige Container wird die Stabilität und Sicherheit des Systems erhöht. Fehler oder Abstürze eines Dienstes wirken sich nicht direkt auf andere Komponenten aus. Portainer unterstützt diesen modularen Ansatz, indem es eine zentrale Verwaltung aller Container bereitstellt.

Aufgrund der übersichtlichen Benutzeroberfläche, der einfachen Handhabung und der guten Integration in Docker-basierte Systeme wird Portainer in dieser Diplomarbeit zur Verwaltung und Überwachung der containerisierten Smart-Home-Komponenten eingesetzt.

### Einführung in die Programmiersprache Perl
Im Rahmen dieser Diplomarbeit wurde erstmals mit der Programmiersprache Perl gearbeitet. Perl ist eine interpretierte, plattformunabhängige Programmiersprache, die besonders für Textverarbeitung, Systemskripte sowie die Automatisierung von Abläufen eingesetzt wird. Aufgrund ihrer Flexibilität und der guten Integration in Linux-Systeme findet Perl auch im Bereich Server- und Smart-Home-Anwendungen Verwendung.

Perl-Programme bestehen aus einfachen, zeilenbasierten Anweisungen und werden in sogenannten Skripten gespeichert. Ein grundlegendes Perl-Programm beginnt üblicherweise mit einer sogenannten Shebang-Zeile, die angibt, mit welchem Interpreter das Skript ausgeführt werden soll.
`#!/usr/bin/perl`

##### Ausgabe von Text

Eine der grundlegendsten Funktionen in Perl ist die Ausgabe von Text auf der Konsole. Dies erfolgt mit dem Befehl print.
`print "Hello World\n";`
Der Ausdruck `\n` steht dabei für einen Zeilenumbruch.

##### Variablen

Perl verwendet unterschiedliche Variablentypen, die durch spezielle Zeichen gekennzeichnet sind. Skalare Variablen, die einzelne Werte wie Zahlen oder Zeichenketten speichern, beginnen mit dem Zeichen `$`.
`my $zahl = 10;`
`my $text = "Smart Home";`
Der Befehl my sorgt dafür, dass die Variable nur im aktuellen Gültigkeitsbereich verwendet werden kann.

##### Bedingungen

Mit bedingten Anweisungen lassen sich Entscheidungen im Programmablauf umsetzen. Eine einfache if-Anweisung sieht in Perl wie folgt aus:
`if ($zahl > 5) {`
`   print "Die Zahl ist größer als 5\n";`
`}`

##### Schleifen

Perl bietet verschiedene Möglichkeiten zur Wiederholung von Programmteilen. Eine häufig genutzte Variante ist die for-Schleife:
`for (my $i = 0; $i < 3; $i++) {`
`    print "Durchlauf $i\n";`
`}`

##### Bedeutung für diese Diplomarbeit

In dieser Diplomarbeit wird Perl verwendet, um Automatisierungsaufgaben und logische Abläufe innerhalb des Smart-Home-Systems umzusetzen. Die einfache Syntax und die gute Integration in Linux-basierte Systeme ermöglichen eine effiziente Implementierung von Steuerungs- und Verwaltungsfunktionen.

Durch das Erlernen der Programmiersprache Perl konnten grundlegende Programmierkonzepte wie Variablen, Bedingungen und Schleifen praktisch angewendet und in das Gesamtsystem integriert werden.

## Praktische Arbeit

In diesem Kapitel wird die praktische Umsetzung des Smart-Home-Systems beschrieben. Ziel war es, eine modulare und erweiterbare Architektur auf Basis von FHEM (Perl) zu realisieren. Als zentrale Steuereinheit wurde ein Raspberry Pi eingesetzt. Die Kommunikation zwischen Sensorik, Aktorik und der Steuerzentrale erfolgt über das MQTT-Protokoll. Zusätzlich wurde Node-RED zur Visualisierung und zur Erstellung von Logik-Workflows verwendet.

### MQTT im Kontext von FHEM und Perl

Rolle von MQTT in der FHEM-Architektur

In dieser Diplomarbeit übernimmt MQTT nicht nur die reine Nachrichtenübertragung, sondern fungiert als Entkopplungsschicht zwischen Hardware und Automatisierungslogik.

Während der Arduino Sensordaten erzeugt und Aktoren physisch schaltet, verarbeitet FHEM als zentrale Instanz diese Informationen und trifft Steuerentscheidungen.
MQTT stellt sicher, dass diese Kommunikation asynchron und zustandsunabhängig erfolgt.

Im Gegensatz zu direkten TCP- oder seriellen Verbindungen ermöglicht MQTT eine lose Kopplung der Systemkomponenten. Dadurch kann beispielsweise Node-RED oder ein zusätzliches Visualisierungssystem ergänzt werden, ohne die bestehende Struktur anzupassen.

#### MQTT-Integration in FHEM

In FHEM erfolgt die MQTT-Anbindung über das Modul MQTT2_CLIENT.
Dabei agiert FHEM selbst als MQTT-Client und verbindet sich mit einem lokal laufenden Broker wie Eclipse Mosquitto, der auf dem Raspberry Pi betrieben wird.

Die Konfiguration in FHEM erfolgt beispielsweise über:
`define myMQTT MQTT2_CLIENT 127.0.0.1:1883`
`attr myMQTT autocreate 1`

Dadurch kann FHEM:

- MQTT-Nachrichten abonnieren
- Statusänderungen empfangen
- eigene Nachrichten publizieren

Ein wesentlicher Vorteil dieser Methode ist die direkte Weiterverarbeitung der MQTT-Payloads innerhalb von FHEM-Perl-Funktionen.

#### Verarbeitung von MQTT-Daten in Perl

Ein besonderer Schwerpunkt dieser Arbeit liegt auf der Nutzung von Perl innerhalb von FHEM.
Eingehende MQTT-Nachrichten können in FHEM über sogenannte Notify- oder DOIF-Definitionen verarbeitet werden.

Beispielhaft kann ein Temperaturwert aus einem MQTT-Topic analysiert und weiterverarbeitet werden:
`define tempNotify notify MQTT2_DEVICE:temperature.* {`
`  my $wert = ReadingsVal("MQTT2_DEVICE","temperature",0);`
`  if($wert > 25){`
`    fhem("set Heizung off");`
`  }`
`}`

Hier wird deutlich:

- MQTT dient nur als Transportmechanismus
- Die Entscheidungslogik liegt vollständig in Perl
- FHEM fungiert als zentrale Steuerinstanz

Diese Trennung erhöht die Wartbarkeit des Systems erheblich.

#### Strukturierung der MQTT-Kommunikation

Im Gegensatz zur reinen hierarchischen Topic-Betrachtung wird in dieser Arbeit zusätzlich auf eine funktionsbasierte Gliederung der Topics geachtet.

Dabei werden Topics nicht nur nach Raum, sondern nach Systemfunktion strukturiert, z. B.:

- system/temperature/current
- system/heating/target
- system/light/state
- system/light/command

Diese Trennung ermöglicht:

- klare Unterscheidung zwischen Soll- und Ist-Werten
- einfache Erweiterbarkeit
- saubere Trennung von Status und Steuerbefehl

Gerade in FHEM erleichtert dies die Definition von Readings und Attributen.

#### Sicherheitsaspekte von MQTT im lokalen Netzwerk

Da das Smart-Home-System vollständig im lokalen Netzwerk betrieben wird, wurde bewusst auf externe Broker verzichtet.
Der MQTT-Broker läuft ausschließlich auf dem Raspberry Pi.

Zur Absicherung wurden folgende Maßnahmen berücksichtigt:

- Deaktivierung des anonymen Zugriffs
- Benutzername/Passwort
- Einschränkung auf das interne Netzwerk

Damit wird verhindert, dass unautorisierte Geräte Nachrichten publizieren oder manipulieren.

#### Abgrenzung zu anderen Protokollen

In der Planungsphase wurden auch alternative Kommunikationsmöglichkeiten betrachtet:

- direkte serielle Kommunikation
- HTTP-REST-Schnittstellen
- WebSockets

MQTT wurde gewählt, da es speziell für IoT-Anwendungen entwickelt wurde und:

- geringe Bandbreite benötigt
- zustandsorientiert arbeitet
- skalierbar ist

Im Gegensatz zur direkten seriellen Kommunikation ermöglicht MQTT zudem mehrere gleichzeitige Abonnenten.

### Umsetzung des Systems FHEM (Perl)

#### Installation von FHEM auf den Raspberry PI

##### Vorbereitung des Systems 

Als zentrale Steuereinheit des Smart-Home-Systems wurde ein Raspberry Pi 5 verwendet. Dieses basiert auf Debian Linux und bietet eine stabile Grundlage für serverbasierte Anwendungen wie FHEM. Zuserst wurde das System aktualiesiert, um sicher zustellen das alle Pakete up to date sind, mit den commands (`sudo apt update & sudo apt upgrade -y`). 

##### Installation von FHEM 

Bei FHEM handelt es sich um eine serverbasierte Smart-Home-Software, die in der Programmiersprache Perl entwickelt wurde. FHEM läuft als Hintergrunddienst und ist über ein Webinterface erreichbar.

Die Installation folgt mit folgende Commands.
`wget https://fhem.de/fhem-6.4.deb`
`sudo dpkg -i fhem-6.4.deb`

Falls Abhängigkeiten fehlten, wurden diese mit folgenden Befehk nach installiert:
`sudo apt --fix-broken install` 

Nach erfolgreciher Installation startet FHEM automatisch als Dienst.

##### Überprüfung der Installation 

Die Weboberfläche ist standartmäßig über Port 8083 erreichbar: 
 `http://<IP-Adresse-des-Raspberry-Pi>:8083`
  
Nach diesem Befehl erscheint die FHEM-WEB-Oberfläche, wodurch bestätigt wird, dass die Installation erfolgreich war.

Zusätzlich kann man den Status des Dienstes überprüfen, mit den Befehl:
`sudo systemctl status fhem`

Ein aktiver Status ("active(running)") zeigt an, das der Server korrekt ausgeführt wird.

#### Einbindung der LEDs in die FHEM-Weboberfläche

##### Grundprinzip der LED-Integration

Die LEDs stellen im Modellhaus die Lichtaktoren dar.
Physikalisch sind sie über Vorwiderstände mit digitalen Ausgängen des Arduino Uno verbunden.

Die Steuerung erfolgt in mehreren Schritten:

1. Weboberfläche (FHEM) sendet Schaltbefehl
2. FHEM publiziert MQTT-Nachricht
3. Arduino empfängt Befehl
4. Digitaler Ausgang wird gesetzt
5. LED leuchtet bzw. erlischt

FHEM übernimmt dabei die Rolle der zentralen Steuerinstanz.

#### Anlegen des MQTT-Devices in FHEM

Zunächst wurde in FHEM die MQTT-Verbindung definiert:
`define myMQTT MQTT2_CLIENT 127.0.0.1:1883`
`attr myMQTT autocreate 1`

Damit verbindet sich FHEM mit dem lokal laufenden Broker Eclipse Mosquitto.

#### Anlegen eines LED-Geräts in FHEM

Für jede LED wurde ein eigenes Device angelegt.

Beispiel: LED im Wohnzimmer

`define LED_Wohnzimmer MQTT2_DEVICE`
`attr LED_Wohnzimmer room Wohnzimmer`
`attr LED_Wohnzimmer setList on off`
`attr LED_Wohnzimmer readingList haus/licht/wohnzimmer/state`
`attr LED_Wohnzimmer setList on:haus/licht/wohnzimmer/set on off:haus/licht/wohnzimmer/set off`

Erklärung der Konfiguration

setList on off
 -> definiert die Schaltzustände

readingList
 -> empfängt Statusmeldungen vom Arduino

setList mit Topic
 -> sendet beim Klick auf „on“ oder „off“ eine MQTT-Nachricht

Dadurch erscheint in der Weboberfläche automatisch ein Schalter.

#### Darstellung in der Weboberfläche

In der FHEM-Weboberfläche wird jedes definierte Device automatisch angezeigt.
Zur besseren Übersicht wurden:
`attr LED_Wohnzimmer icon light_ceiling`
`attr LED_Wohnzimmer webCmd on:off`
gesetzt.

Das bewirkt:

- Anzeige eines Lichtsymbols
- Direkte Schaltbuttons im Webinterface
- Übersichtliche Raumstruktur

#### Zuordnung zu Räumen

Damit die LEDs logisch gruppiert werden, wurde das Attribut „room“ verwendet:
`attr LED_Wohnzimmer room Wohnzimmer`
`attr LED_Kueche room Kueche`
`attr LED_Schlafzimmer room Schlafzimmer`

Dadurch erscheinen die Geräte in der jeweiligen Raumansicht.

#### Rückmeldung des LED-Zustandes

Wichtig für die Weboberfläche ist die Statusrückmeldung.
Der Arduino sendet nach jeder Zustandsänderung:
`haus/licht/wohnzimmer/state ON`

FHEM aktualisiert dadurch automatisch das Reading des Devices.
Ohne Rückmeldung würde der Schalter zwar klicken, aber der Status wäre nicht synchron.

#### Verarbeitung mit Perl (optional erweitert) 

In deiner Diplomarbeit kannst du zusätzlich zeigen, dass FHEM die LED auch logisch verarbeiten kann:
`define autoLicht notify LED_Wohnzimmer:on {`
`  Log 1, "Wohnzimmer Licht wurde eingeschaltet";`
`}`

`Damit wird bei jeder Zustandsänderung ein Logeintrag erzeugt.`
`Hier zeigt sich der Vorteil von FHEM:`
`Die Logik kann direkt in Perl erweitert werden.`


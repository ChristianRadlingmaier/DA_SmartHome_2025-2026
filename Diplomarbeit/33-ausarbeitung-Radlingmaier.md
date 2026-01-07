# Teilaufgabe Schüler Radlingmaier
\textauthor{Radlingmaier Christian}

## Theorie

Dieses Kapitel wird oft auch als _Literaturrecherche_ bezeichnet. Da gehört alles rein was der __normale__ Leser braucht um den praktischen Ansatz zu verstehen. Das bedeutet Sie brauchen einen roten Faden !

Das sind z.B: allgemeine Definitionen, Beschreibung von fachspezifischen Vorgehensweisen, Frameworks, Theorie zu verwendeten Algorithmen, besondere Umstände, ... 

Hier werden die theorethischen sowie die Praktischen Grundlagen für die Umsetzung von Fhem in einem Modellhaus gezeigt und wie man es unteranderem in einem Haus anwenden kann. Das benötigte Wissen sowie die Frameworks die verwendet werden, sind hier dargestellt, damit der Leser alles nachvollziehen kann und es auch nachmachen kann.

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

## 1. Theoretische Grundlagen
    Unter einem Smart Home versteht man ein Haus, in dem verschiedene technische Komponenten miteinander vernetzt sind und zentral überwacht sowie gesteuert werden können. Diese Steuerung kann sowohl automatisch durch definierte Abläufe als auch manuell durch den Nutzer erfolgen. So ist es beispielsweise möglich, Beleuchtung oder Heizsysteme über ein mobiles Endgerät zu bedienen oder Rollläden zeitgesteuert automatisch zu bewegen.

    In dieser Diplomarbeit kommt ein Arduino als Mikrocontroller zum Einsatz, der für die Erfassung von Sensordaten sowie die Ansteuerung von Aktoren verantwortlich ist. Als zentrale Kontrolleinheit dient ein Raspberry Pi, auf dem die Smart-Home-Software FHEM betrieben wird. FHEM übernimmt die zentrale Verwaltung der angeschlossenen Geräte, verarbeitet eingehende Daten und setzt definierte Automatisierungsregeln um.

    Der Datenaustausch zwischen den einzelnen Systemkomponenten erfolgt über das MQTT-Protokoll. Dieses ermöglicht eine effiziente und zuverlässige Kommunikation zwischen Sensoren, Aktoren und der zentralen FHEM-Instanz.

### 1.1 Sensorik, Aktorik und Steuerung    

#### 1.1.1 Sensorik
Sensorik bildet eine zentrale Grundlage eines Smart-Home-Systems, da sie die Erfassung von physikalischen und umgebungsbezogenen Zuständen ermöglicht. Sensoren dienen dazu, Informationen aus der realen Umgebung aufzunehmen und diese in elektrische Signale umzuwandeln, die von Mikrocontrollern oder zentralen Steuereinheiten weiterverarbeitet werden können.

In Smart-Home-Anwendungen kommen unterschiedliche Sensortypen zum Einsatz. Dazu zählen unter anderem Temperatursensoren, Feuchtigkeits- und Helligkeitssensoren sowie Bewegungs- und Kontaktsensoren. Diese erfassen kontinuierlich relevante Umgebungsdaten, die als Grundlage für automatisierte Entscheidungen und Steuerungsprozesse dienen.

Die erfassten Sensordaten werden in der Regel von Mikrocontrollern, wie beispielsweise einem Arduino, ausgelesen und anschließend an eine zentrale Automatisierungsplattform übertragen. Dort können die Daten analysiert, visualisiert und für die Umsetzung von Automatisierungsregeln genutzt werden. Auf diese Weise ist es möglich, auf bestimmte Zustände gezielt zu reagieren, etwa durch das Einschalten der Beleuchtung bei Bewegung oder das Anpassen der Heizleistung in Abhängigkeit von der Raumtemperatur.

Ein wesentlicher Vorteil moderner Sensorik ist ihre hohe Genauigkeit sowie der geringe Energieverbrauch. In Kombination mit standardisierten Kommunikationsprotokollen lassen sich Sensoren flexibel in bestehende Smart-Home-Systeme integrieren und bei Bedarf erweitern.

In dieser Diplomarbeit wird Sensorik eingesetzt, um relevante Umgebungsparameter zu erfassen und als Grundlage für die Automatisierung und Steuerung innerhalb des Smart-Home-Systems zu dienen.

#### 1.1.2 Aktorik
Aktorik bezeichnet die Gesamtheit aller Komponenten in einem Smart-Home-System, die auf Basis von Steuerbefehlen physische Aktionen ausführen. Aktoren setzen digitale Signale aus der Steuerungslogik in konkrete mechanische, elektrische oder optische Vorgänge um und stellen damit das Gegenstück zur Sensorik dar.

In Smart-Home-Anwendungen werden unterschiedliche Aktortypen eingesetzt. Dazu zählen unter anderem Relaismodule zum Schalten von elektrischen Verbrauchern, Aktoren für Beleuchtungssysteme, Motoren zur Steuerung von Rolllaeden sowie Stellventile für Heizungs- oder Lueftungssysteme. Diese Aktoren reagieren auf Steuerbefehle, die entweder manuell durch den Benutzer oder automatisch durch definierte Regeln ausgelöst werden.

Die Ansteuerung der Aktoren erfolgt in der Regel über Mikrocontroller wie den Arduino, der die von der zentralen Steuereinheit empfangenen Befehle interpretiert und entsprechende Schaltsignale erzeugt. Die zentrale Steuerlogik wird dabei von einer Automatisierungsplattform wie Node-RED oder FHEM übernommen, während die Kommunikation häufig über das MQTT-Protokoll realisiert wird.

Ein wichtiger Aspekt der Aktorik ist die Zuverlässigkeit und Sicherheit der ausgefuehrten Aktionen. Insbesondere bei netzspannungsbetriebenen Geraeten muessen geeignete Schutzmaßnahmen, wie Relais mit ausreichender Belastbarkeit, beruecksichtigt werden. Dadurch wird ein sicherer Betrieb des Smart-Home-Systems gewaehrleistet.

In dieser Diplomarbeit wird Aktorik eingesetzt, um auf Basis von Sensordaten und definierten Automatisierungsregeln gezielt in die Umgebung einzugreifen und den gewuenschten Komfort-, Sicherheits- und Energieeffizienzgewinn zu realisieren.

#### 1.1.3 Steuerung(Arduino UNO)
Die Steuerung stellt eine zentrale Funktion innerhalb des Smart-Home-Systems dar und ist für die Verarbeitung von Sensordaten sowie die Ansteuerung der Aktoren verantwortlich. In dieser Diplomarbeit wird der Arduino Uno als Mikrocontroller eingesetzt, um diese Aufgaben zuverlässig und effizient zu übernehmen.

Der Arduino Uno fungiert als dezentrale Steuereinheit, an die verschiedene Sensoren und Aktoren angeschlossen sind. Die vom System erfassten Sensordaten werden vom Mikrocontroller eingelesen, vorverarbeitet und anschließend an die zentrale Automatisierungsplattform weitergeleitet. Gleichzeitig empfängt der Arduino Uno Steuerbefehle von der Zentrale und setzt diese in entsprechende Schalt- oder Regelvorgänge um.

Die Programmierung des Arduino Uno erfolgt über die Arduino-Entwicklungsumgebung und ermöglicht eine strukturierte Umsetzung der Steuerungslogik. Der Mikrocontroller arbeitet dabei ereignisgesteuert und reagiert auf definierte Zustände oder empfangene Nachrichten. Die Kommunikation mit der zentralen Steuerungseinheit erfolgt über standardisierte Schnittstellen und Protokolle, beispielsweise unter Verwendung von MQTT.

Durch den Einsatz des Arduino Uno wird eine klare Trennung zwischen der hardwarebezogenen Steuerungsebene und der zentralen Automatisierungs- und Logikebene erreicht. Dies erhöht die Modularität des Systems und erleichtert sowohl Erweiterungen als auch Wartungsarbeiten.

In dieser Diplomarbeit übernimmt der Arduino Uno somit die Aufgabe der direkten Steuerung von Sensoren und Aktoren und bildet die Verbindung zwischen der physischen Umgebung und der übergeordneten Smart-Home-Logik.

### 1.2 Frameworks

#### 1.2.1 FHEM
FHEM ist ein quelloffenes Smart-Home-Framework, das zur Steuerung, Überwachung und Automatisierung von Haus- und Gebäudetechnik eingesetzt wird. Die Software wird überwiegend auf Linux-basierten Systemen betrieben, wie beispielsweise einem Raspberry Pi, und fungiert als zentrale Steuereinheit innerhalb eines Smart-Home-Systems.

Das Framework ist modular aufgebaut und unterstützt eine Vielzahl von Geräten, Protokollen und Kommunikationsschnittstellen. Dadurch können sowohl Sensoren (z. B. Temperatur- oder Bewegungssensoren) als auch Aktoren (z. B. Relais, Heizungsventile oder Beleuchtungssysteme) in das System integriert werden. Die Verwaltung dieser Komponenten erfolgt zentral über FHEM.

Ein wesentliches Merkmal von FHEM ist die flexible Automatisierungslogik. Mithilfe von Regeln, Zeitplänen und Ereignissen können Abläufe definiert werden, die automatisch auf bestimmte Zustände oder Sensordaten reagieren. Zusätzlich bietet FHEM verschiedene Möglichkeiten zur Benutzerinteraktion, etwa über eine webbasierte Oberfläche oder externe Anwendungen.

Die Kommunikation zwischen FHEM und externen Geräten kann über unterschiedliche Protokolle erfolgen. In dieser Diplomarbeit wird hierfür das MQTT-Protokoll verwendet, da es eine effiziente und zuverlässige Datenübertragung zwischen Mikrocontrollern, Sensoren und der FHEM-Zentrale ermöglicht.

Aufgrund seiner Offenheit, Erweiterbarkeit und großen Community eignet sich FHEM besonders für individuelle und anpassbare Smart-Home-Lösungen. Aus diesen Gründen wurde FHEM als zentrale Automatisierungsplattform für diese Diplomarbeit ausgewählt.

#### 1.2.2 Node-RED
Node-RED ist ein quelloffenes, ereignisgesteuertes Entwicklungsframework, das insbesondere im Bereich Smart Home und Internet of Things (IoT) eingesetzt wird. Es ermöglicht die grafische Erstellung von Steuerungs- und Automatisierungslogiken mithilfe eines webbasierten Editors. Die einzelnen Funktionsbausteine, sogenannte Nodes, werden per Drag-and-Drop miteinander verbunden und bilden gemeinsam sogenannte Flows, welche den Daten- und Kontrollfluss innerhalb des Systems abbilden.

Innerhalb eines Smart-Home-Systems übernimmt Node-RED die Verarbeitung von Sensordaten sowie die Umsetzung von logischen Abläufen. Eingehende Informationen, beispielsweise von Temperatur- oder Bewegungssensoren, können analysiert, gefiltert und anschließend zur Steuerung von Aktoren wie Beleuchtung, Heizung oder Rollläden verwendet werden. Dadurch lassen sich sowohl einfache Automatisierungen als auch komplexe Abhängigkeiten realisieren.

Ein wesentlicher Vorteil von Node-RED ist die Unterstützung zahlreicher Kommunikationsprotokolle und Schnittstellen. Dazu zählen unter anderem MQTT, HTTP sowie WebSockets, wodurch eine einfache Integration von Mikrocontrollern, Smart-Home-Zentralen und externen Diensten möglich ist. In dieser Diplomarbeit wird Node-RED insbesondere zur Verarbeitung von MQTT-Nachrichten und zur Umsetzung der Steuerlogik eingesetzt.

Zusätzlich besteht die Möglichkeit, eigene Funktionslogiken mithilfe von JavaScript zu implementieren, wodurch Node-RED flexibel erweitert werden kann. Über optionale Erweiterungen wie Dashboards können zudem grafische Benutzeroberflächen zur Visualisierung von Daten und zur manuellen Steuerung erstellt werden.

Aufgrund seiner übersichtlichen grafischen Programmierumgebung, der hohen Erweiterbarkeit und der aktiven Community eignet sich Node-RED besonders für die Entwicklung individueller Smart-Home-Lösungen. Daher wird das Framework in dieser Diplomarbeit als zentrales Werkzeug zur Umsetzung von Automatisierungs- und Steuerungsprozessen verwendet. 

#### 1.2.3 MQTT
MQTT (Message Queuing Telemetry Transport) ist ein leichtgewichtiges, ereignisbasiertes Kommunikationsprotokoll, das speziell für den Einsatz in ressourcenbeschränkten Systemen entwickelt wurde. Aufgrund seines geringen Overheads und der hohen Zuverlässigkeit wird MQTT häufig in Smart-Home- und Internet-of-Things-Anwendungen eingesetzt.

Das Protokoll basiert auf dem sogenannten Publish-Subscribe-Prinzip. Dabei kommunizieren die einzelnen Geräte nicht direkt miteinander, sondern über eine zentrale Instanz, den sogenannten Broker. Sensoren oder andere Datenquellen senden ihre Informationen als Nachrichten (Publish) an den Broker, während andere Komponenten diese Nachrichten abonnieren (Subscribe). Die Zuordnung erfolgt über eindeutig benannte Themen (Topics).

In einem Smart-Home-System ermöglicht MQTT eine klare Trennung zwischen Datenerfassung und Steuerlogik. Sensoren, beispielsweise Mikrocontroller wie ein Arduino, senden Messwerte an den MQTT-Broker, während zentrale Systeme wie Node-RED oder FHEM diese Daten empfangen, verarbeiten und entsprechende Steuerbefehle an Aktoren weiterleiten. Dadurch entsteht eine flexible und skalierbare Kommunikationsstruktur.

Ein weiterer Vorteil von MQTT ist die Unterstützung verschiedener Qualitätsstufen (Quality of Service), die festlegen, wie zuverlässig Nachrichten übertragen werden. Zusätzlich bietet das Protokoll Mechanismen wie Retained Messages und Last Will, die insbesondere in Smart-Home-Systemen zur Erhöhung der Ausfallsicherheit beitragen.

Aufgrund seiner Effizienz, der einfachen Implementierung und der guten Integration in bestehende Smart-Home-Frameworks eignet sich MQTT besonders für die Kommunikation zwischen Sensoren, Aktoren und zentralen Steuerungssystemen. Aus diesen Gründen wird MQTT in dieser Diplomarbeit als zentrales Kommunikationsprotokoll für den Datenaustausch innerhalb des Smart-Home-Systems eingesetzt.


#### 1.2.4 Portainer
Portainer ist eine webbasierte Management- und Verwaltungsplattform zur einfachen Administration von containerbasierten Anwendungen. Die Software wird hauptsächlich in Verbindung mit Docker eingesetzt und ermöglicht es, Container, Images, Netzwerke und Volumes über eine grafische Benutzeroberfläche zu verwalten. Dadurch wird die Nutzung von Container-Technologien auch ohne tiefgehende Kommandozeilenkenntnisse erleichtert.

Im Smart-Home-Umfeld eignet sich Portainer besonders für den Betrieb und die Organisation mehrerer Dienste auf einer zentralen Steuereinheit, wie beispielsweise einem Raspberry Pi oder einem Server. Anwendungen wie Node-RED, MQTT-Broker oder FHEM können in separaten Containern betrieben und über Portainer übersichtlich verwaltet werden. Dies erhöht die Wartbarkeit und Übersichtlichkeit des Gesamtsystems.

Ein wesentlicher Vorteil von Portainer ist die vereinfachte Bereitstellung und Aktualisierung von Containern. Neue Dienste können schnell gestartet, bestehende Container neu konfiguriert oder aktualisiert werden, ohne das gesamte System neu aufzusetzen. Zudem ermöglicht Portainer das Überwachen von Ressourcen wie CPU-Auslastung, Arbeitsspeicherverbrauch und Laufzeiten der einzelnen Container.

Durch die Trennung der einzelnen Anwendungen in eigenständige Container wird die Stabilität und Sicherheit des Systems erhöht. Fehler oder Abstürze eines Dienstes wirken sich nicht direkt auf andere Komponenten aus. Portainer unterstützt diesen modularen Ansatz, indem es eine zentrale Verwaltung aller Container bereitstellt.

Aufgrund der übersichtlichen Benutzeroberfläche, der einfachen Handhabung und der guten Integration in Docker-basierte Systeme wird Portainer in dieser Diplomarbeit zur Verwaltung und Überwachung der containerisierten Smart-Home-Komponenten eingesetzt.

## Praktische Arbeit




### Auswertung der Ergebnisse

Anhand von XY kann man folgende Tabelle ableiten:

| Right | Left | Default | Center |
|------:|:-----|---------|:------:|
|   12  |  12  |    12   |    12  |
|  123  |  123 |   123   |   123  |
|    1  |    1 |     1   |     1  |

: Eine Tolle tabelle


# Teilaufgabe Schüler Pripfl

\textauthor{Chloe Pripfl}

Das IoT-Car hat noch keine Verwendung gefunden. Zum Start der Diplomarbeit kann das Auto mithilfe einer Carson ModelSport Vernbedienung gesteuert werden.
Außerdem sind die Jumper Kabel welche die Sensoren mit der verbauten Raspberry Pi verbinden ausgesteckt.
In diesem teil der Arbeit werden:
- Jumperkabel wieder verbunden,
- ROS2 auf der Raspberry Pi augfesetzt,
- die Kamerasicht des Autos 
- sowie die Steuerung über ein Smartphone implementiert.

## Theorieteil

### ROS2

#### Was ist ROS?

ROS (Robot Operating System) ist ein Open-Source-Framework, welches Bibliotheken, Werkzeuge und Kommunikationsmechanismen zur Entwicklung
von Roboteranwendungen bereitstellt und die Programmierung stark vereinfacht. Ziel von ROS ist es, komplexe Robotersysteme modular,
wiederverwendbar und skalierbar zu machen.
[@ROS2]

##### Grundidee und Architektur (ROS vs ROS 2)

ROS basiert auf einem verteilten System welche **Nodes** genannt werden. Ein Node ist ein einzelnes Programm welches eine Teilaufgabe
übernimmt (z.B. Sensor Auswertung oder Motorsteuerung). In ROS 2 wurden die Nodes erweitert. Innerhalb eines Prozesses können nun mehrere Nodes betrieben werden. Zusätzlich wurden **Lifecycle-Nodes** eingeführt, die definierte Zustände wie unconfigured, inactive und active besitzen.

Ein **Master** bieten die Namensregestrierung und -auflösung für den Computation Graph. Ohne den Master, würden Nodes sich nicht finden, nicht komunizieren und keine Services aufrufen können. In ROS 2 existiert kein zentraler Master mehr; die Kommunikation und Discovery erfolgt dezentral. 

Der **Parameter Server** ermöglicht es, Daten in Form von Schlüssel-Wert-Paaren zu speichern. Aktuell ist der Parameter Server Teil des ROS Masters. In ROS 2 gibt es keinen zentralen Parameter Server mehr. Stattdessen sind Parameter node-lokal organisiert.

Node kommunizieren durch **Messages**, welche eine Datenstruktur mit typisierten Feldern ist. Unterstützt werden: Standard-Datentypen,
Arrays von primitiven Datentypen und beliebig verschachtelte Strukturen und Arrays.

Diese Messages werden über ein Transportsystem weitergekeitet, welches mit der Publish-/Subscripe-Semantik funktioniert. D.h. ein Node sendet
eine Nchricht indem er auf einem **Topic** veröffentlicht (publish). Ein Topic ist ein Name, der den Inhalt der Nachricht identifiziert.
Nodes, die an bestimmten Daten interessiert sind, abonieren (subscribe) das entprechende Topic. In ROS 2 wurden zusätzlich Quality-of-Service-Mechanismen (QoS) eingeführt, die eine bessere Kontrolle über Zuverlässigkeit, Latenz und Echtzeitfähigkeit ermöglichen und ROS 2 für Embedded- und Echtzeitsysteme geeignet machen.

Dieses Publish-/Subscribe-Modell ist sehr flexibel, eignet sich aber nicht fr Request-Reply-Interaktionen (Anfrage/Antwort), die in verteilten Systemen häufig benötigt werden. Sie werden über **Services** realisiert. Ein Service besteht aus zwei Message-Strukturen, eine für die Anfrage (Request) und eine für die Antwort (Reply).
Ein anbietender Node stellt den Service unter einem Namen bereit, ein Client kann dann diesen Service aufrufen, indem er eine Anfrage sendet und auf die Antwort wartet. ROS-Client-Bibliotheken stellen diese Kommunikation dem Programmierrer meist so dar, als hadle es sich um einen RPC (Remote Procedure Call). In ROS 2 stehen zusätzlich Actions als Standardmechanismus zur Verfügung, die speziell für langlaufende Aufgaben mit Feedback konzipiert sind.

**Bags** ist ein Dateiformat zum Speichern und Wiedergeben von ROS-Messagedaten. Sie sind besonders wichtig für das Aufzeichnen von Sensordaten, die Entwicklung und testen von Algorithmen und für die Analyse von Systemverhalten. In ROS 2 wurde hierfür ein neues Backend implementiert, das verschiedene Speicherformate (z. B. SQLite) unterstützt.
[@ROS-Architektur] & [@ROSvsROS2-Architektur]

#### Warum ROS2
(Warum ROS2, was kann es besser etc.)

#### Vorbereitungen für ROS2
(also was braucht man um ROS2 zum laufen zu bringen)

### Verbindung zum Smartphone
(vermutlich über mqtt)

## Praxisteil

### Sensorenverbindung Jumperkabel

Durch Herrn Hutter Anleitungen fürs Auto bekommen, worin alles beschrieben wird. Welche Sensoren auf welche Pins der Raspberry Pi verbunden werden müssen. 

### Raspberry Pi Betriebssystem

Um ein passendes Betriebssystem zu finden muss man sich zuerst die Raspberry Pi selbst anschauen. In dem Fall wurde eine Raspberry Pi 3 mit 64 bit verbaut. 
Am besten für ROS2 ist Ubuntu. Da die Raspberry Pi 3 leider nicht für die LTS Version von Ubuntu geeignet ist, wurde nach einer anderen Option gesucht.

Repositroy bla bla [@raspberry-pi-image]

## Fehler

### Kaputtes Ground Jumper Kabel

Dieses Problem wurde einfach gelöst. Hierzu wurde ein Leitendes Pin-ähnelndes metallstück an das Kabel angelötet. 

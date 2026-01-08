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

##### Grundidee und Architektur

ROS basiert auf einem verteilten System welche **Nodes** genannt werden. Ein Node ist ein einzelnes Programm welches eine Teilaufgabe
übernimmt (z.B. Sensor Auswertung, Motorsteuerung, etc.). 

**Masters** bieten die Namensregestrierung und -auflösung für den  Computation Graph bereit. Ohne den Master, würden Nodes sich nicht finden,
nicht komunizieren und keine Services aufrufen können.

Der **Parameter Server** ermöglicht es, Daten in Form von Schlüssel-Wert-Paaren zu speichern. Aktuell ist der Parameter Server Teil des ROS Masters.

Node kommunizieren durch **Messages**, welche eine Datenstruktur mit typisierten Feldern ist. Unterstützt werden: Standard-Datentypen,
Arrays von primitiven Datentypen und beliebig verschachtelte Strukturen und Arrays.

Diese Messages werden über ein Transportsystem weitergekeitet, welches mit der Publish-/Subscripe-Semantik funktioniert. D.h. ein Node sendet
eine Nchricht indem er auf einem **Topic** veröffentlicht (publish). Ein Topic ist ein Name, der den Inhalt der Nachricht identifiziert.
Nodes, die an bestimmten Daten interessiert sind, abonieren (subscribe) das entprechende Topic. Z.B. ein Node welches die Aufgabe hat, die
Geschwindigkeit in einen Graphen darzustellen, subscribed das Node mit dem Topic in dem die Daten der Geschwindigkeiten published werden.

Dieses Publish-/Subscribe-Modell ist sehr flexibel, eignet sich aber nicht fpr Request-Reply-Interaktionen (Anfrage/Antwort), die in verteilten Systemen häufig benötigt werden. Sie werden über **Services** realisiert. 

#### Warum ROS2
(Warum ROS2, was kann es besser etc.)

#### Vorbereitungen für ROS2
(also was braucht man um ROS2 zum laufen zu bringen)


### Verbindung zum Smartphone


## Praxisteil

### Sensorenverbindung Jumperkabel

Durch Herrn Hutter Anleitungen fürs Auto bekommen, worin alles beschrieben wird. Welche Sensoren auf welche Pins der Raspberry Pi verbunden werden müssen. 


### Raspberry Pi Betriebssystem

Um ein passendes Betriebssystem zu finden muss man sich zuerst die Raspberry Pi selbst anschauen. In dem Fall wurde eine Raspberry Pi 3 mit 64 bit verbaut. 
Am besten für ROS2 ist Ubuntu. Da die Raspberry Pi 3 leider nicht für die LTS Version von Ubuntu geeignet ist, wurde nach einer anderen Option gesucht.

Repositroy bla bla [@ros-realtime-rpi4-image]

### ROS2 installieren

## Fehler

### Kaputtes Ground Jumper Kabel

Dieses Problem wurde einfach gelöst. Hierzu wurde ein Leitendes Pin-ähnelndes metallstück an das Kabel angelötet. 

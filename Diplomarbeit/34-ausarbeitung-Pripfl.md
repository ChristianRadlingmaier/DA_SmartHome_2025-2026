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

ROS ist ein open Source System, welches wie ein Betriebssystem für Roboter agiert. Es stellt Dienste wie Hardwareabstraktion, Gerätetreiber, Utilityfunktionen, 
Interprozesskommunikation und Paketmanagment zur verfügung. Außerdem finden sich nützliche Werkzeuge um Roboter zu programmieren, zu steuern und mit Hardware zu verbinden. 

#### Warum ROS2
(Warum ROS2, was kann es besser etc.)

#### Vorbereitungen für ROS2
(also was braucht man um ROS2 zum laufen zu bringen)


### Verbindung zum Smartphone


## Praxisteil

### Sensorenverbindung Jumperkabel

Durch Herrn Hutter Anleitungen fürs Auto bekommen, worin alles beschrieben wird. Welche Sensoren auf welche Pins der Raspberry Pi verbunden werden müssen. 

### Kaputtes Ground Jumper Kabel

Dieses Problem wurde einfach gelöst. Hierzu wurde ein Leitendes Pin-ähnelndes metallstück an das Kabel angelötet. 

### Raspberry Pi Betriebssystem

Um ein passendes Betriebssystem zu finden muss man sich zuerst die Raspberry Pi selbst anschauen. In dem Fall wurde eine Raspberry Pi 3 mit 64 bit verbaut. 
Am besten für ROS2 ist Ubuntu. Da die Raspberry Pi 3 leider nicht für die LTS Version von Ubuntu geeignet ist, ist Raspberry OS die einfachste Option.

Das Image kann man ganz einfach über den RaspberryPi Imager über einen anderen PC oder Laptop auf die SD Karte laden. Dort kann man direkt einen Namen (iotcar) und ein Passowrt auswählen
und eine Internetverbindng vorbereiten.

### ROS2 installieren



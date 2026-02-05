# Teilaufgabe Schüler Gierer

\textauthor{Janik Gierer}

Dieses Kapitel wird oft auch als *Literaturrecherche* bezeichnet. Hier wird alles behandelt, was ein **fachlich interessierter Leser** benötigt, um den praktischen Ansatz nachvollziehen zu können.  
Ziel ist ein klarer roter Faden.

Dazu zählen unter anderem:

- allgemeine Definitionen  
- Beschreibung fachspezifischer Vorgehensweisen  
- verwendete Frameworks  
- theoretische Grundlagen zu eingesetzten Algorithmen  
- besondere technische Rahmenbedingungen  

In diesem Kapitel werden die theoretischen und praktischen Grundlagen zur Umsetzung von Home Assistant für ein Modellhaus beschrieben. Zusätzlich wird erläutert, wie diese Konzepte auf ein reales Wohnhaus übertragen werden können.  
Der Fokus liegt auf der Einrichtung von Docker auf dem Raspberry Pi sowie auf der Kommunikation zwischen Raspberry Pi, Arduino Uno und den angeschlossenen Aktoren und Sensoren. [@ha_installation; @docker_what_is_container; @docker_compose_overview]

## Verwendete Aktoren

- 100 Stück Widerstände (1/4 W, 5 % Toleranz, 150 Ohm)  
- 3 mm Leuchtdioden (LEDs)

## Zusätzlich benötigtes Material

- IWILCS Dupont Crimp Set (790-teilig inkl. Crimpzange)  
- Kabel mit 0,5 mm² Querschnitt  
- 4× PLA Basic Hellgrau (10104)  
- 2× PLA Basic Dunkelgrau (10105)

## Verwendete Frameworks

- **Home Assistant**  
  Dient als zentrales Steuerelement des Modellhauses. Es wird praxisnah simuliert, wie von einem zentralen Standort aus sämtliche Geräte gesteuert und überwacht werden können. [@ha_installation; @aavild_distributed_homeassistant_2024]

- **Node-RED**  
  Ermöglicht die einfache Erstellung und Automatisierung von Logiken. Sensordaten wie Temperatur oder Helligkeit können verarbeitet und entsprechende Aktoren angesteuert werden. [@nodered_homepage]

- **MQTT**  
  Wird als Kommunikationsprotokoll zwischen Mikrocontroller (Arduino Uno), Raspberry Pi und Home Assistant verwendet. Es ermöglicht eine zuverlässige und schnelle Datenübertragung. [@oasis_mqtt_v5_2019; @agyemang_mqtt_2022; @ha_mqtt_integration]

- **Portainer**  
  Dient zur übersichtlichen Verwaltung aller laufenden Docker-Container über ein Webinterface. [@portainer_docs]

- **Firmata**  
  Firmata ist ein Kommunikationsprotokoll, mit dem ein Computer (in diesem Fall der Raspberry Pi) einen Mikrocontroller (Arduino Uno) direkt steuern kann. Auf dem Mikrocontroller läuft dabei das *StandardFirmata*-Sketch, welches das Setzen von Pins sowie das Lesen von Eingängen ermöglicht. [@arduino_firmata_docs; @firmata_arduino_github]

# Teilaufgabe – Smart-Home-Umsetzung mit Home Assistant und Node-RED

**Schüler:** Janik Gierer

## Theoretische Grundlagen

Ein Smart Home beschreibt ein vernetztes Haus, bei dem Geräte und Komponenten zentral gesteuert und Zustände ausgelesen werden können. Die Steuerung erfolgt entweder automatisch oder durch Benutzereingaben. [@abutair_secure_privacy_smart_home_2020]  
Beispiele hierfür sind das Ein- und Ausschalten von Licht oder Heizung über ein Smartphone oder das automatische Herunterfahren von Rollläden zu bestimmten Uhrzeiten. [@abutair_secure_privacy_smart_home_2020]

Im Rahmen dieser Diplomarbeit kommen ein Arduino Uno als Mikrocontroller, ein Raspberry Pi als Steuerzentrale sowie Home Assistant als Automatisierungsplattform zum Einsatz. [@ha_installation]  
Die Kommunikation zwischen Sensoren und Aktoren erfolgt über MQTT. [@oasis_mqtt_v5_2019; @ha_mqtt_integration]

### Sensorik, Aktorik und Steuerung im Modellhaus

Sensorik, Aktorik und Steuerung bilden die grundlegenden Bestandteile eines Smart Homes. Erst durch ihr Zusammenspiel wird ein automatisiertes System möglich. [@abutair_secure_privacy_smart_home_2020]

**Sensorik**  
Sensoren erfassen Zustände und Umweltparameter wie Temperatur, Helligkeit, Bewegung oder Luftfeuchtigkeit. Diese Messwerte werden an den Mikrocontroller weitergeleitet. [@abutair_secure_privacy_smart_home_2020]

**Aktorik**  
Aktoren reagieren auf Steuerbefehle oder geänderte Messwerte. Digitale Signale werden in physische Aktionen umgesetzt, beispielsweise durch LEDs, Relais oder Motoren. [@abutair_secure_privacy_smart_home_2020]

**Steuerung**  
Die Steuerung verarbeitet Sensordaten und entscheidet, welche Aktoren angesteuert werden. Die Logik befindet sich in einer übergeordneten Software, während der Mikrocontroller die Befehle ausführt. [@abutair_secure_privacy_smart_home_2020]

#### Sensoren zur Messung von Umweltparametern

Kurzbeschreibung der verwendeten Sensoren (z. B. Temperatur-, Helligkeitssensoren) sowie deren Aufgabe im Smart-Home-System. [@abutair_secure_privacy_smart_home_2020]

#### Aktoren zur Steuerung von Licht und Geräten

Relais, LEDs und Mini-Lampen – Einsatzmöglichkeiten und Grenzen. [@abutair_secure_privacy_smart_home_2020]

#### Mikrocontroller (Arduino) als Basis für smarte Funktionen

Auf dem Arduino wird das Beispiel *StandardFirmata* installiert. Dieses Sketch stellt die Firmata-Funktionen bereit und ermöglicht die Steuerung des Arduino über die serielle Schnittstelle durch einen Host (Raspberry Pi). [@arduino_firmata_docs; @firmata_arduino_github]

*(Hinweis: In der Arduino IDE findet man es typischerweise unter **File → Examples → Firmata → StandardFirmata**.)* [@arduino_firmata_docs]

##### Einbindung der Firmata-Bibliothek

`#include <Firmata.h>`  
Ermöglicht, dass der Arduino vom Host aus gesteuert werden kann (Pins setzen, lesen). [@arduino_firmata_docs]

##### Start der seriellen Kommunikation

`Firmata.begin(57600);`  
Öffnet die serielle Schnittstelle mit 57600 Baud – notwendig, damit der Host über USB mit dem Arduino kommunizieren kann. [@firmata_arduino_github]

##### Registrierung der Callbacks

`Firmata.attach(ANALOG_MESSAGE, analogWriteCallback);`  
`Firmata.attach(DIGITAL_MESSAGE, digitalWriteCallback);`  
`Firmata.attach(SET_PIN_MODE, setPinModeCallback);`  
`Firmata.attach(START_SYSEX, sysexCallback);`  
`Firmata.attach(SYSTEM_RESET, systemResetCallback);`

Diese Callbacks sorgen dafür, dass eingehende Nachrichten korrekt verarbeitet werden. [@firmata_arduino_github]

##### Setzen des Pin-Modus

Ein *Pin-Conflict* entsteht typischerweise, wenn mehrere Nodes denselben Pin parallel ansprechen. Daher sollte pro Pin genau eine Schaltstelle existieren. [@firmata_arduino_github]

##### Digitales Schreiben

Wird ausgelöst, wenn der Host einen digitalen Befehl sendet (z. B. ON / OFF). [@firmata_arduino_github]

##### Haupt-Loop

Verarbeitet dauerhaft Eingangszustände und Befehle vom Host. [@firmata_arduino_github]

### Datenübertragung und Kommunikation im Smart Home

#### MQTT als zentrales Protokoll

Topic-Struktur, Payload-Formate und Zuverlässigkeit. [@oasis_mqtt_v5_2019; @ha_mqtt_integration]

#### Node-RED zur Verarbeitung von Nachrichten

Visuelle Programmierung zur Automatisierung von Abläufen. [@nodered_homepage]

#### Serieller Zugriff auf den Arduino

Verbindung über `/dev/ttyUSB0` zur Übertragung von Steuerkommandos.

### Home Assistant als zentrale Steuereinheit

#### Integration von MQTT-Geräten

Manuelle Konfiguration im Vergleich zur MQTT-Integration. [@ha_mqtt_integration; @ha_mqtt_sensor]

#### Automationen in Home Assistant

Beispielsweise Lichtsteuerung bei Bewegung oder Temperaturregelung. [@ha_automation]

### Visualisierung und Benutzeroberfläche

#### Lovelace UI

Dashboards für Licht, Heizung und Sensorwerte. [@ha_dashboards_intro; @ha_cards]

#### Visualisierung von Zustandsänderungen

Darstellung von Lampenstatus, Temperaturverläufen und Türkontakten. [@ha_cards]

## Praktische Umsetzung

### Aufbau des Modellhauses

#### Stromversorgung und Verkabelung

Mini-USB, Breadboards und Steckverbindungen.

#### Einbau von LEDs, Relais und Sensoren

Platzierung und Verkabelung im Modellhaus.

### Arduino-Programmierung

#### Einlesen und Senden von Sensorwerten

Übertragung über Serial oder MQTT. [@oasis_mqtt_v5_2019]

#### Empfang und Ausführung von Steuerkommandos

Lichtsteuerung über serielle Befehle. [@arduino_firmata_docs; @firmata_arduino_github]

### Node-RED Workflows zur Kommunikation

#### MQTT-IN Nodes

Beispiel: `haus/licht/wohnzimmer → Serial`. [@nodered_homepage; @oasis_mqtt_v5_2019]

#### Serial-Out an den Arduino

Steuerung der LEDs über den USB-Port. [@nodered_homepage]

### Docker-basierter Betrieb

#### Container für Home Assistant, Node-RED, MQTT und Portainer

Verwaltung über `docker-compose` am Raspberry Pi. [@docker_compose_overview; @docker_compose_file_reference; @portainer_docs]

### Bedienung und Steuerung

#### Steuerung über Endgeräte

Zugriff auf die Home-Assistant-Oberfläche im Browser. [@ha_dashboards_intro]

#### Test der Licht- und Heizungssteuerung

### Fehleranalyse und Optimierungen

#### Serielle Fehler

Behandlung von Berechtigungsproblemen und Portkonflikten.

#### MQTT-Verbindungsabbrüche

Vermeidung durch QoS und Last Will and Testament (LWT). [@oasis_mqtt_v5_2019]

## Ausblick

### Erweiterung mit Sprachsteuerung

Integration von Sprachassistenten wie Alexa. [@ha_voice_control; @ha_alexa_smart_home]

### Erweiterung auf mehrere Räume

Modularer Ausbau ohne Änderungen an der Grundarchitektur.

### Einbindung weiterer Sensoren

CO₂-, Luftqualitäts- und Helligkeitssensoren. [@ha_dev_sensor_entity]

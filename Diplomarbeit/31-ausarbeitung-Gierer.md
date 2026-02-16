# Teilaufgabe Schüler Gierer

\textauthor{Janik Gierer}

Dieses Kapitel entspricht der *Literaturrecherche*. Es enthält alles, was ein **fachlich interessierter Leser** braucht, um den praktischen Ansatz nachvollziehen zu können.  
Ziel ist ein klarer roter Faden.

Dazu zählen unter anderem:

- allgemeine Definitionen  
- Beschreibung fachspezifischer Vorgehensweisen  
- verwendete Frameworks  
- theoretische Grundlagen zu eingesetzten Algorithmen  
- besondere technische Rahmenbedingungen  

Dieses Kapitel beschreibt die theoretischen und praktischen Grundlagen zur Umsetzung von Home Assistant im Modellhaus. Zusätzlich wird gezeigt, wie sich diese Konzepte auf ein reales Wohnhaus übertragen lassen.  
Der Fokus liegt auf der Einrichtung von Docker am Raspberry Pi sowie auf der Kommunikation zwischen Raspberry Pi, Arduino Uno und den angeschlossenen Aktoren und Sensoren. [@ha_installation] [@docker_compose_overview] [@docker_what_is_container]

## Verwendete Aktoren
<!-- TODO: Abschnittstitel prüfen: Widerstände sind keine Aktoren. -->

- 100 Stück Widerstände (1/4 W, 5 % Toleranz, 150 Ohm)  
- 3 mm Leuchtdioden (LEDs)

## Zusätzlich benötigtes Material

- IWILCS Dupont Crimp Set (790-teilig inkl. Crimpzange)  
- Kabel mit 0,5 mm² Querschnitt  
- 4× PLA Basic Hellgrau (10104)  
- 2× PLA Basic Dunkelgrau (10105)

## Verwendete Frameworks

- **Home Assistant**  
  Dient als zentrales Steuerelement des Modellhauses. Es wird praxisnah gezeigt, wie Geräte zentral gesteuert und überwacht werden können. [@ha_installation] [@aavild_distributed_homeassistant_2024]

- **Node-RED**  
  Ermöglicht die einfache Erstellung und Automatisierung von Abläufen. Sensordaten wie Temperatur oder Helligkeit können verarbeitet und entsprechende Aktoren angesteuert werden. [@nodered_homepage]

- **MQTT**  
  Wird als Kommunikationsprotokoll zwischen Mikrocontroller (Arduino Uno), Raspberry Pi und Home Assistant verwendet. Es ermöglicht eine zuverlässige und schnelle Datenübertragung. [@oasis_mqtt_v5_2019] [@agyemang_mqtt_2022] [@ha_mqtt_integration]

- **Portainer**  
  Dient zur übersichtlichen Verwaltung laufender Docker-Container über ein Webinterface. [@portainer_docs]

- **Firmata**  
  Firmata ist ein Kommunikationsprotokoll, mit dem ein Computer (in diesem Fall der Raspberry Pi) einen Mikrocontroller (Arduino Uno) direkt steuern kann. Auf dem Mikrocontroller läuft dabei das *StandardFirmata*-Sketch, das das Setzen von Pins sowie das Lesen von Eingängen ermöglicht. [@arduino_firmata_doc] [@firmata_arduino_github]

# Teilaufgabe – Smart-Home-Umsetzung mit Home Assistant und Node-RED

**Schüler:** Janik Gierer

## Theoretische Grundlagen

Ein Smart Home ist ein vernetztes Haus, in dem Geräte und Komponenten zentral gesteuert und Zustände ausgelesen werden. Die Steuerung erfolgt automatisch oder durch Benutzereingaben. [@abutair_secure_privacy_smart_home_2020]  
Beispiele hierfür sind das Ein- und Ausschalten von Licht oder Heizung über ein Smartphone oder das automatische Herunterfahren von Rollläden zu bestimmten Uhrzeiten. [@abutair_secure_privacy_smart_home_2020]

Im Rahmen dieser Diplomarbeit kommen ein Arduino Uno als Mikrocontroller, ein Raspberry Pi als Steuerzentrale sowie Home Assistant als Automatisierungsplattform zum Einsatz. [@ha_installation]  
Die Kommunikation zwischen Arduino Uno, Raspberry Pi und Home Assistant erfolgt über MQTT. [@oasis_mqtt_v5_2019] [@ha_mqtt_integration]

### Sensorik, Aktorik und Steuerung im Modellhaus

Sensorik, Aktorik und Steuerung bilden die grundlegenden Bestandteile eines Smart Homes. Erst durch ihr Zusammenspiel wird ein automatisiertes System möglich. [@abutair_secure_privacy_smart_home_2020]

**Sensorik**  
Sensoren erfassen Zustände und Umweltparameter wie Temperatur, Helligkeit, Bewegung oder Luftfeuchtigkeit. Diese Messwerte werden an den Mikrocontroller weitergeleitet. [@abutair_secure_privacy_smart_home_2020]

**Aktorik**  
Aktoren reagieren auf Steuerbefehle oder geänderte Messwerte. Digitale Signale werden in physische Aktionen umgesetzt, beispielsweise durch LEDs, Relais oder Motoren. [@abutair_secure_privacy_smart_home_2020]

**Steuerung**  
Die Steuerung verarbeitet Sensordaten und entscheidet, welche Aktoren angesteuert werden. Die Logik befindet sich in einer übergeordneten Software, während der Mikrocontroller die Befehle ausführt. [@abutair_secure_privacy_smart_home_2020]

#### Sensoren zur Messung von Umweltparametern

Kurzbeschreibung der verwendeten Sensoren (z. B. Temperatur- und Helligkeitssensoren) sowie deren Aufgabe im Smart-Home-System. [@abutair_secure_privacy_smart_home_2020] <!-- TODO: Verwendete Sensoren konkret nennen und kurz beschreiben. -->

#### Aktoren zur Steuerung von Licht und Geräten

Relais, LEDs und Mini-Lampen: Einsatzmöglichkeiten und Grenzen. [@abutair_secure_privacy_smart_home_2020] <!-- TODO: Aktoren konkret beschreiben und Grenzen kurz erläutern. -->

#### Mikrocontroller (Arduino) als Basis für smarte Funktionen

Auf dem Arduino wird das Beispiel *StandardFirmata* installiert. Dieser Sketch stellt die Firmata-Funktionen bereit und ermöglicht die Steuerung des Arduino über die serielle Schnittstelle durch einen Host (Raspberry Pi). [@arduino_firmata_docs] [@firmata_arduino_github]

*(Hinweis: In der Arduino IDE findet man es typischerweise unter **File -> Examples -> Firmata -> StandardFirmata**.)* [@arduino_firmata_docs]

##### Einbindung der Firmata-Bibliothek

`#include <Firmata.h>`  
Ermöglicht die Steuerung des Arduino durch den Host (Pins setzen und lesen). [@arduino_firmata_docs]

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

Ein *Pin-Konflikt* entsteht typischerweise, wenn mehrere Nodes denselben Pin parallel ansprechen. Daher sollte pro Pin genau eine Steuerstelle existieren. [@firmata_arduino_github]

##### Digitales Schreiben

Wird ausgelöst, wenn der Host einen digitalen Befehl sendet (z. B. ON/OFF). [@firmata_arduino_github]

##### Haupt-Loop

Verarbeitet dauerhaft Eingangszustände und Befehle des Hosts. [@firmata_arduino_github]

### Datenübertragung und Kommunikation im Smart Home

#### MQTT als zentrales Protokoll

Themen: Topic-Struktur, Payload-Formate und Zuverlässigkeit. [@oasis_mqtt_v5_2019; @ha_mqtt_integration] <!-- TODO: Inhalte kurz ausführen. -->

#### Node-RED zur Verarbeitung von Nachrichten

Visuelle Programmierung zur Automatisierung von Abläufen. [@nodered_homepage]

#### Serieller Zugriff auf den Arduino

Verbindung über `/dev/ttyUSB0` zur Übertragung von Steuerkommandos.

### Home Assistant als zentrale Steuereinheit
Home Assistant ist ein weit verbreitetes Automatisierungstool für Wohnhäuser. Gründe sind unter anderem die große Nutzerbasis, die einfache Einrichtung und die vergleichsweise geringen Kosten. <!-- TODO: Aussage belegen oder präzisieren. -->

#### Integration von MQTT-Geräten

Manuelle Konfiguration im Vergleich zur MQTT-Integration. [@ha_mqtt_integration] [@ha_mqtt_sensor]

#### Automationen in Home Assistant

Beispielsweise Lichtsteuerung bei Bewegung oder Temperaturregelung. [@ha_automation]

### Visualisierung und Benutzeroberfläche

#### Lovelace UI

Dashboards für Licht, Heizung und Sensorwerte. [@ha_dashboards_intro] [@ha_cards]

#### Visualisierung von Zustandsänderungen

Darstellung von Lampenstatus, Temperaturverläufen und Türkontakten. [@ha_cards]

## Praktische Umsetzung

### Aufbau des Modellhauses

#### Stromversorgung und Verkabelung

Stromversorgung über Mini-USB sowie Breadboards und Steckverbindungen für die Verdrahtung.

#### Einbau von LEDs, Relais und Sensoren

Platzierung und Verkabelung der LEDs, Relais und Sensoren im Modellhaus.

### Arduino-Programmierung

#### Einlesen und Senden von Sensorwerten

Übertragung über serielle Verbindung oder MQTT. [@oasis_mqtt_v5_2019]

#### Empfang und Ausführung von Steuerkommandos

Lichtsteuerung über serielle Befehle. [@arduino_firmata_docs] [@firmata_arduino_github]

### Node-RED Workflows zur Kommunikation

#### MQTT-IN Nodes

Beispiel: `haus/licht/wohnzimmer -> Serial`. [@nodered_homepage] [@oasis_mqtt_v5_2019]

#### Serial-Out an den Arduino

Steuerung der LEDs über den USB-Port. [@nodered_homepage]



### Docker-basierter Betrieb
```yaml
version: "3.9"

services:

  homeassistant:

    container_name: homeassistant

    image: ghcr.io/home-assistant/home-assistant:stable

    restart: always

    ports:

      - "8123:8123"

    volumes:

      - ./homeassistant:/config

    environment:

      - TZ=Europe/Vienna

  mqtt:

    container_name: mqtt

    image: eclipse-mosquitto:2

    restart: always

    ports:

      - "1883:1883"

      - "9001:9001"

    volumes:

      - ./mosquitto/config:/mosquitto/config:ro

      - ./mosquitto/data:/mosquitto/data

      - ./mosquitto/log:/mosquitto/log

  portainer:

    container_name: portainer

    image: portainer/portainer-ce:latest

    restart: always

    ports:

      - "9000:9000"

    volumes:

      - /var/run/docker.sock:/var/run/docker.sock

      - ./portainer:/data
```

#### Bei Neustart des Raspberry Pi

##### Docker starten und testen
Alle Schritte zum Aufsetzen von Docker erfolgen erst nach der Installation von Raspberry Pi OS.  
Im Ordner, in dem die `docker-compose.yaml`-Datei liegt, wird `docker-compose up -d` ausgeführt; alternativ `docker compose up -d`. Das hängt von der Docker-Version ab.  
Zum Testen `docker ps` ausführen. Steht im Status `Up` mit einer Zeitangabe, läuft alles.

##### Alles zum Laufen bringen 
Die Ausgabe von `hostname -I` sieht etwa so aus: `10.0.0.140 172.17.0.1 172.19.0.1 2001:871:264:3198:14ae:a095:e626:6d2e`. Relevant ist nur die erste Adresse, hier `10.0.0.140`. Bei Verwendung derselben `docker-compose.yaml` kann auf Home Assistant mit `http://10.0.0.140:8123` und auf Portainer mit `http://10.0.0.140:9000` zugegriffen werden.

###### Node-RED-Installation 

Wenn Node-RED im Container läuft, ist die Installation zusätzlicher Nodes nur eingeschränkt möglich. Deshalb wird Node-RED lokal am Raspberry Pi installiert:  
`bash <(curl -sL https://raw.githubusercontent.com/node-red/linux-installers/master/deb/update-nodejs-and-nodered)`  
Mit `sudo systemctl enable nodered` wird der Dienst für den Autostart aktiviert.  
Mit `sudo systemctl start nodered` wird der Dienst gestartet.  
Mit `sudo systemctl status nodered --no-pager` wird geprüft, ob es keine Fehler gibt.
 

#### Container für Home Assistant, MQTT, Portainer

Verwaltung über `docker-compose` am Raspberry Pi. [@docker_compose_overview] [@docker_compose_file_reference] [@portainer_docs]



### Bedienung und Steuerung

#### Steuerung über Endgeräte

Zugriff auf die Home-Assistant-Oberfläche im Browser. [@ha_dashboards_intro]

#### Test der Licht- und Heizungssteuerung
<!-- TODO: Testablauf und Ergebnisse kurz beschreiben. -->

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

CO2-, Luftqualitäts- und Helligkeitssensoren. [@ha_dev_sensor_entity]

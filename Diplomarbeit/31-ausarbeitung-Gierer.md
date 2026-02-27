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

## Verwendete Komponenten

### Aktoren und passive Bauteile

- 3 mm Leuchtdioden (LEDs) als Lichtaktoren  
- 100 Stück Widerstände (1/4 W, 5 % Toleranz, 150 Ohm) zur Strombegrenzung der LEDs

### Zusätzlich benötigtes Material

- IWILCS Dupont Crimp Set (790-teilig inkl. Crimpzange)  
- Kabel mit 0,5 mm² Querschnitt  
- 4× PLA Basic Hellgrau (10104)  
- 2× PLA Basic Dunkelgrau (10105)

## Verwendete Frameworks

- **Home Assistant**  
  Dient als zentrale Automatisierungsplattform, über die Geräte integriert, Zustände visualisiert und Regeln ausgeführt werden. [@ha_installation] [@ha_automation]

- **Node-RED**  
  Wird als visuelle Low-Code-Umgebung eingesetzt, um Datenflüsse zwischen MQTT, serieller Schnittstelle und Home Assistant abzubilden. [@nodered_homepage]

- **MQTT**  
  Wird als Publish/Subscribe-Protokoll zwischen Mikrocontroller, Raspberry Pi und Smart-Home-Plattform verwendet. [@oasis_mqtt_v5_2019] [@agyemang_mqtt_2022] [@ha_mqtt_integration]

- **Portainer**  
  Dient zur Verwaltung laufender Docker-Container über ein Webinterface. [@portainer_docs]

- **Firmata**  
  Firmata ist ein Protokoll, mit dem ein Host-System (Raspberry Pi) einen Mikrocontroller (Arduino Uno) über die serielle Schnittstelle steuern kann. [@arduino_firmata_docs] [@firmata_arduino_github]

# Teilaufgabe – Smart-Home-Umsetzung mit Home Assistant und Node-RED

**Schüler:** Janik Gierer

## Theoretische Grundlagen

Ein Smart Home ist ein vernetztes Haus, in dem Geräte und Komponenten zentral gesteuert und Zustände ausgelesen werden. Die Steuerung erfolgt automatisch oder durch Benutzereingaben. [@abutair_secure_privacy_smart_home_2020]  
Beispiele sind das automatische Schalten von Beleuchtung in Abhängigkeit von Sensorwerten oder die manuelle Steuerung über eine Benutzeroberfläche. [@abutair_secure_privacy_smart_home_2020]

Im Rahmen dieser Diplomarbeit kommen ein Arduino Uno als Mikrocontroller, ein Raspberry Pi als Steuerzentrale sowie Home Assistant als Automatisierungsplattform zum Einsatz. [@ha_installation]  
Die Kommunikation zwischen Arduino Uno, Raspberry Pi und Home Assistant erfolgt über MQTT. [@oasis_mqtt_v5_2019] [@ha_mqtt_integration]

### Sensorik, Aktorik und Steuerung im Modellhaus

Sensorik, Aktorik und Steuerung bilden die grundlegenden Bestandteile eines Smart Homes. Erst durch ihr Zusammenspiel wird ein automatisiertes System möglich. [@abutair_secure_privacy_smart_home_2020]

**Sensorik**  
Sensoren erfassen Zustände und Umweltparameter. Die Messwerte werden an den Mikrocontroller übertragen und dort für die Weiterverarbeitung vorbereitet. [@abutair_secure_privacy_smart_home_2020]

**Aktorik**  
Aktoren setzen digitale Steuerbefehle in physische Aktionen um, z. B. durch das Ein- und Ausschalten von Beleuchtung. [@abutair_secure_privacy_smart_home_2020]

**Steuerung**  
Die Steuerlogik verarbeitet Sensordaten, entscheidet auf Basis von Regeln und steuert anschließend die Aktoren an. [@abutair_secure_privacy_smart_home_2020]

#### Sensoren zur Messung von Umweltparametern

Im Projekt werden insbesondere folgende Sensordaten verarbeitet:

- **Helligkeitssensor** zur Erfassung von Lichtwerten (z. B. Schwellwert für automatische Beleuchtung)  
- **Bewegungssensor (PIR)** als Trigger für Anwesenheit  
- **Temperatursensor** als Grundlage für temperaturabhängige Steuerungen  
- **Türkontakt** zur Zustandsmeldung (offen/geschlossen)

Damit werden sowohl kontinuierliche Messwerte (z. B. Temperatur, Helligkeit) als auch diskrete Zustände (Bewegung, Türkontakt) verarbeitet. [@abutair_secure_privacy_smart_home_2020]

#### Aktoren zur Steuerung von Licht und Geräten

Im Modellhaus werden hauptsächlich LEDs bzw. Mini-Lampen als Lichtaktoren verwendet. Die Ansteuerung erfolgt digital (ON/OFF), optional über Relaiskanäle bei getrennten Lastkreisen.  
Grenzen ergeben sich durch die elektrische Belastbarkeit der Ausgänge und die verfügbaren GPIO-/I/O-Ressourcen des Systems. Für größere Lasten ist eine getrennte Treiberstufe (z. B. Relaismodul) erforderlich. [@abutair_secure_privacy_smart_home_2020]

#### Mikrocontroller (Arduino) als Basis für smarte Funktionen

Auf dem Arduino wird das Beispiel *StandardFirmata* installiert. Dieser Sketch stellt die Firmata-Funktionen bereit und ermöglicht die Steuerung des Arduino über die serielle Schnittstelle durch einen Host (Raspberry Pi). [@arduino_firmata_docs] [@firmata_arduino_github]

*(Hinweis: In der Arduino IDE findet man es typischerweise unter **File -> Examples -> Firmata -> StandardFirmata**.)* [@firmata_arduino_github]

##### Einbindung der Firmata-Bibliothek

`#include <Firmata.h>`  
Bindet die Firmata-API ein, damit Nachrichten vom Host empfangen und Pins über standardisierte Befehle angesteuert werden können. [@firmata_arduino_github]

##### Start der seriellen Kommunikation

`Firmata.begin(57600);`  
Initialisiert die serielle Schnittstelle für die Host-Kommunikation. [@firmata_arduino_github]

##### Registrierung der Callbacks

`Firmata.attach(ANALOG_MESSAGE, analogWriteCallback);`  
`Firmata.attach(DIGITAL_MESSAGE, digitalWriteCallback);`  
`Firmata.attach(SET_PIN_MODE, setPinModeCallback);`  
`Firmata.attach(START_SYSEX, sysexCallback);`  
`Firmata.attach(SYSTEM_RESET, systemResetCallback);`

Diese Callback-Funktionen ordnen eingehende Protokollnachrichten konkreten Verarbeitungsfunktionen zu. [@firmata_arduino_github]

##### Setzen des Pin-Modus

Über `setPinModeCallback` wird pro Pin festgelegt, ob er als Eingang, Ausgang oder Spezialfunktion (z. B. PWM) betrieben wird. Eine eindeutige Pin-Zuordnung ist wichtig, damit keine widersprüchlichen Steuerbefehle entstehen. [@firmata_arduino_github]

##### Digitales Schreiben

`digitalWriteCallback` setzt digitale Ausgänge auf HIGH oder LOW. In dieser Arbeit wird das für Schaltvorgänge wie Licht ein/aus verwendet. [@firmata_arduino_github]

##### Haupt-Loop

In der `loop()`-Funktion werden eingehende serielle Daten dauerhaft verarbeitet (`Firmata.available()` / `Firmata.processInput()`). Dadurch reagiert der Arduino laufend auf Befehle des Hosts. [@firmata_arduino_github]

### Datenübertragung und Kommunikation im Smart Home

Die Kommunikationskette ist in dieser Arbeit klar getrennt:  
Sensorik/Aktorik am Arduino -> serielle Verbindung bzw. MQTT -> Node-RED/ Home Assistant als Verarbeitungs- und Bedienebene.  
Diese Trennung erleichtert Wartung und Erweiterung, weil Datenerfassung, Transport und Automatisierungslogik entkoppelt sind. [@oasis_mqtt_v5_2019] [@ha_mqtt_integration] [@nodered_homepage]

#### MQTT als zentrales Protokoll

MQTT basiert auf dem Publish/Subscribe-Prinzip mit Broker, Topics und Clients. Geräte publizieren Zustände, andere Komponenten abonnieren diese Topics. [@oasis_mqtt_v5_2019]

Für das Modellhaus wird eine hierarchische Topic-Struktur verwendet, z. B.:

- `haus/sensor/temperatur`  
- `haus/sensor/helligkeit`  
- `haus/licht/wohnzimmer/set`  
- `haus/licht/wohnzimmer/state`

Payloads werden als einfache Werte oder JSON-Objekte übertragen. Für schaltkritische Nachrichten kann QoS 1 verwendet werden; QoS 0 eignet sich für unkritische, häufige Statusupdates. Retained Messages und Last Will and Testament erhöhen die Nachvollziehbarkeit von Zuständen nach Reconnects. [@oasis_mqtt_v5_2019] [@ha_mqtt_integration]

#### Node-RED zur Verarbeitung von Nachrichten

Node-RED ermöglicht die visuelle Modellierung von Datenflüssen mit Nodes. In dieser Arbeit werden MQTT-In/-Out, Function- und Serial-Nodes kombiniert, um Sensordaten aufzubereiten und Steuerbefehle weiterzugeben. [@nodered_homepage]

Ein typischer Ablauf ist:

1. MQTT-In empfängt Sensordaten oder Schaltbefehle.  
2. Function-Node validiert bzw. transformiert Payloads.  
3. Serial-Out oder MQTT-Out sendet den Befehl an Arduino bzw. Home Assistant.

Dadurch bleibt die Steuerlogik nachvollziehbar und schnell anpassbar. [@nodered_homepage]

#### Serieller Zugriff auf den Arduino

Der Arduino wird unter Linux typischerweise als `/dev/ttyUSB0` oder `/dev/ttyACM0` eingebunden. Für stabile Kommunikation ist wichtig, dass der Port nur von einem Prozess gleichzeitig geöffnet wird und die laufende Node-RED-/Systeminstanz ausreichende Geräteberechtigungen besitzt. [@nodered_raspberrypi]

### Home Assistant als zentrale Steuereinheit

Home Assistant wird als zentrale Integrations- und Bedienplattform genutzt. In der Arbeit wird Home Assistant lokal auf dem Raspberry Pi betrieben und mit MQTT-Entitäten, Automationen und Dashboards verknüpft. [@ha_installation] [@ha_mqtt_integration] [@ha_automation]

#### Integration von MQTT-Geräten

Die MQTT-Einbindung kann entweder manuell über Konfigurationen oder über MQTT Discovery erfolgen. Discovery reduziert den manuellen Aufwand, da Geräte und Entitäten automatisch angelegt werden, sobald gültige Discovery-Nachrichten gesendet werden. [@ha_mqtt_integration] [@ha_mqtt_sensor]

#### Automationen in Home Assistant

Automationen bestehen aus Trigger, optionalen Bedingungen und Aktionen. [@ha_automation]  
Beispiel in dieser Arbeit:

- Trigger: Bewegung erkannt und Helligkeit unter Schwellwert  
- Bedingung: Automatikmodus aktiv  
- Aktion: Licht einschalten, nach definierter Zeit wieder ausschalten

Dieses Muster trennt Erkennung (Sensorik) und Reaktion (Aktorik) klar und bleibt im Dashboard transparent nachvollziehbar.

### Visualisierung und Benutzeroberfläche


#### Visualisierung von Zustandsänderungen

Zustandsänderungen werden über passende Karten (z. B. Entities-, Button- und Verlaufskarten) sichtbar gemacht. So sind aktuelle Schaltzustände und Messwertverläufe auf einen Blick erkennbar. [@ha_cards]

## Praktische Umsetzung

### Hardwareaufbau

#### Stromversorgung und Verkabelung

Die Stromversorgung erfolgt über den Raspberry Pi (5 V) und den Arduino über USB. Die LED-Kreise sind über Vorwiderstände ausgelegt, um die Bauteile elektrisch zu schützen. Für die Verdrahtung wurden Breadboard-Verbindungen und gecrimpte Leitungen genutzt, damit Anpassungen im Aufbau ohne Löten möglich bleiben.

#### Einbau von LEDs, Relais und Sensoren

Die LEDs wurden den Räumen des Modellhauses zugeordnet. Sensoren wurden so positioniert, dass die relevanten Zustände (Helligkeit, Bewegung, Temperatur, Türkontakt) möglichst repräsentativ erfasst werden. Relaiskanäle wurden dort eingesetzt, wo getrennte Schaltkreise erforderlich sind.

### Arduino-Programmierung

#### Einlesen und Senden von Sensorwerten

Der Arduino liest Sensorzustände ein und stellt sie dem übergeordneten System über die Kommunikationsschnittstelle bereit. Für MQTT-basierte Flows werden die Werte in definierte Topics übertragen. [@oasis_mqtt_v5_2019]

#### Empfang und Ausführung von Steuerkommandos

Steuerbefehle (z. B. Licht ein/aus) werden vom Host empfangen und als digitale Ausgänge umgesetzt. Die Umsetzung erfolgt über Firmata-Callbacks und damit deterministisch pro eingehender Nachricht. [@arduino_firmata_docs] [@firmata_arduino_github]

### Node-RED Workflows zur Kommunikation

#### MQTT-IN Nodes

MQTT-In-Nodes abonnieren Topics wie `haus/licht/wohnzimmer/set` und übergeben die Nutzdaten an die weitere Logik im Flow. [@nodered_homepage] [@oasis_mqtt_v5_2019]

#### Serial-Out an den Arduino

Nach Validierung wird der Befehl über den Serial-Out-Node an den Arduino übertragen. Dadurch lassen sich MQTT-basierte Steuerbefehle direkt in Hardwareaktionen überführen. [@nodered_homepage]

#### Nach erstem Aufsetzen des Raspberry Pi

Beim ersten Aufbau werden Betriebssystem, Containerdienste und Weboberflächen einmalig eingerichtet. Ein bewährter Ablauf ist:

1. Raspberry Pi starten, SSH-Zugriff prüfen und System aktualisieren (`sudo apt update && sudo apt upgrade -y`).
2. Docker und Compose gemäß offizieller Docker-Dokumentation installieren und den Benutzer der Docker-Gruppe hinzufügen. [@docker_compose_overview]
3. Projektordner mit `compose.yaml` anlegen (inkl. Verzeichnisse für `homeassistant`, `mosquitto` und `portainer`) und die Konfigurationsdateien einspielen. [@docker_compose_file_reference]
4. Container erstmals starten: `docker compose up -d`.
5. Laufende Dienste kontrollieren: `docker ps` und bei Bedarf Logs prüfen (`docker logs <container>`). [@docker_compose_overview]
6. IP-Adresse des Raspberry Pi mit `hostname -I` ermitteln und im Browser öffnen:
   - Home Assistant: `http://<raspberry-ip>:8123`
   - Portainer: `http://<raspberry-ip>:9000`
7. In Home Assistant den Onboarding-Prozess (Benutzer, Standort, Zeitzone) abschließen und danach die MQTT-Integration verbinden. [@ha_installation] [@ha_mqtt_integration]
8. In Portainer den Admin-Benutzer anlegen und den lokalen Docker-Endpoint auswählen. [@portainer_docs]

Nach diesem Erstsetup sind Home Assistant, MQTT-Broker und Portainer betriebsbereit. Die wiederkehrenden Startschritte nach einem Neustart sind im nächsten Abschnitt beschrieben.

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

#### Projektstruktur
`mkdir smarthome`-> erstellt einen Ordner mit dem Namen smarthome der Name des Ordners kann freigewählt werden es muss aber im nachstehenden Teil immer dieser Ordner Name sein.
`cd smarthome` -> man geht in den ordner den man gerade erstellt hat. Danach gleich die Ordnerstruktur für die Volumes erstellen  `mkdir -p homeassistant` Ordner für homeassistant erstellen `mkdir -p mosquitto/config mosquitto/data mosquitto/log` erstellen des Ordners für die Ordner mosquitto und den dazugehörigen config,data und log. Als leztes noch den Ordner für Portainer erstellen mit `mkdir -p portainer`    

#### Docker & Compose auf Raspberry Pi OS installieren
Als erstes muss man das System updaten mit `sudo apt update && sudo apt upgrade -y` danach den Docker installieren mit `curl -fsSL https://get.docker.com | sudo sh`. Der User muss in der docker-Gruppe hinzugefügt werden um Berechtigungsprobleme zu vermeiden dies macht man mit `sudo usermod -aG docker $USER` und `newgrp docker` danach kann man den ersten Docker test machen mit `docker run --rm hello-world`. Wenn das Docker Compose Plugin nicht installiert ist `sudo apt install -y docker-compose-plugin` und danach `docker compose version`

#### YAML-Datei erstellen 
`sudo nano docker-compose.yml` oder `sudo nano docker-compose.yaml` beide Varianten sind möglich. Die [Docker-basierter Betrieb](31-ausarbeitung-Gierer.md) Datei dort einfügen man muss in der Kommandozeile (Bash) immer rechtsklick einfügen/paste verwenden ctrl+v funktioniert nicht. 


#### Bei Neustart des Raspberry Pi

##### Docker starten und testen

Im Verzeichnis mit der `compose.yaml` bzw. `docker-compose.yaml` wird `docker compose up -d` gestartet (bei älteren Installationen `docker-compose up -d`).  
Der aktuelle Containerstatus wird mit `docker ps` geprüft. [@docker_compose_overview] [@docker_compose_file_reference]

##### Zugriff auf die Weboberflächen

Mit `hostname -I` wird die IP-Adresse des Raspberry Pi ermittelt. Über diese IP sind die Dienste erreichbar, z. B.:

- Home Assistant: `http://<raspberry-ip>:8123`  
- Portainer: `http://<raspberry-ip>:9000`

###### Node-RED-Installation

Für den lokalen Betrieb auf dem Raspberry Pi wird das offizielle Installationsskript verwendet:

`bash <(curl -sL https://github.com/node-red/linux-installers/releases/latest/download/update-nodejs-and-nodered-deb)`

Danach:

- `sudo systemctl enable nodered.service` (Autostart)  
- `sudo systemctl start nodered.service` (Start)  
- `sudo systemctl status nodered.service --no-pager` (Statusprüfung)

Der Editor wird anschließend im Browser geöffnet:

- lokal am Pi: `http://localhost:1880`  
- im Netzwerk: `http://<raspberry-ip>:1880` [@nodered_raspberrypi]

#### Container für Home Assistant, MQTT und Portainer

Die Dienste laufen getrennt in Containern und können unabhängig voneinander neu gestartet, aktualisiert und überwacht werden. Dadurch bleiben Änderungen an einem Dienst auf diesen begrenzt. [@docker_compose_overview] [@docker_compose_file_reference] [@portainer_docs]

### Bedienung und Steuerung

Die tägliche Bedienung erfolgt über Home-Assistant-Dashboards. Node-RED arbeitet im Hintergrund als Verarbeitungs- und Brückenschicht für eingehende Messwerte und ausgehende Steuerbefehle. [@ha_dashboards_intro] [@nodered_homepage]

#### Steuerung über Endgeräte

Die Oberfläche ist über Browser auf PC, Tablet oder Smartphone erreichbar. Schaltvorgänge werden über Buttons ausgelöst; Statuswerte werden in Echtzeit visualisiert. [@ha_dashboards_intro] [@ha_cards]

#### Test der Licht- und Heizungssteuerung

Der Testablauf orientiert sich an den definierten Use-Cases:

1. Sensorwerte werden erzeugt (Dunkelheit/Bewegung bzw. Temperaturänderung).  
2. Die Automationslogik wird ausgelöst.  
3. Der Aktorzustand wird im Dashboard kontrolliert.

Ergebnis im Projektbetrieb: Lichtsteuerung und zustandsabhängige Schaltvorgänge wurden stabil ausgelöst; Statusänderungen waren im Dashboard nachvollziehbar. Einzelne Fehlerfälle (z. B. Verbindungsunterbrechung) konnten reproduziert und behandelt werden.

### Fehleranalyse und Optimierungen

Fehleranalyse wurde auf Kommunikationspfade (seriell, MQTT) und Zustandslogik fokussiert. Ziel war, reproduzierbare Fehlerbilder zu erzeugen und die Auswirkungen im Dashboard sichtbar zu machen.

#### Serielle Fehler

Typische Probleme sind Portkonflikte (Port bereits belegt), wechselnde Device-Namen (`/dev/ttyUSB0` vs. `/dev/ttyACM0`) und Berechtigungsprobleme. Behebung:

- korrekten Port in Node-RED fixieren  
- exklusiven Zugriff sicherstellen  
- Dienst nach Änderungen neu starten

Dadurch wurde die Stabilität der Host-zu-Arduino-Kommunikation verbessert.

#### MQTT-Verbindungsabbrüche

Zur Erhöhung der Robustheit wurden QoS und Last Will and Testament (LWT) gezielt verwendet. Zusätzlich werden Reconnects über die beteiligten Clients automatisch durchgeführt. Damit bleiben Ausfälle im Dashboard sichtbar und Zustände nach Wiederverbindung konsistent. [@oasis_mqtt_v5_2019] [@ha_mqtt_integration]

## Ausblick

Die umgesetzte Architektur ist modular und kann ohne grundlegenden Umbau erweitert werden.

### Erweiterung mit Sprachsteuerung

Als nächster Schritt ist die Einbindung von Sprachsteuerung möglich, z. B. über die Home-Assistant-Voice-Funktionen oder Alexa-Integration. [@ha_voice_control] [@ha_alexa_smart_home]

### Erweiterung auf mehrere Räume

Die vorhandene Topic-Struktur und Entitätenlogik lässt sich pro Raum vervielfachen (z. B. `haus/licht/kueche`, `haus/licht/schlafzimmer`). Damit kann das Modell schrittweise auf ein vollständiges Mehrraumsystem skaliert werden.

### Einbindung weiterer Sensoren

Zusätzliche Sensoren wie CO2-, Luftqualitäts- und erweiterte Helligkeitssensoren können als weitere Entitäten integriert und in bestehende Automationen eingebunden werden. [@ha_dev_sensor_entity]

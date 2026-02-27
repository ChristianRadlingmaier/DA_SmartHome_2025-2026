# Teilaufgabe Schueler Gierer

\textauthor{Janik Gierer}

Dieses Kapitel dokumentiert die theoretischen Grundlagen und die praktische Umsetzung meines Teilprojekts im Rahmen der Diplomarbeit. Der Schwerpunkt liegt auf dem Betrieb eines Smart-Home-Modellhauses mit Home Assistant, Node-RED, MQTT, Docker und einem Arduino Uno als I/O-Ebene.

Ziel ist ein nachvollziehbarer, technisch korrekter Aufbau, der sich im schulischen Umfeld reproduzieren laesst und als Grundlage fuer spaetere Erweiterungen dient. Neben der Implementierung werden auch Architekturentscheidungen, typische Fehlerquellen und Optimierungsmoeglichkeiten beschrieben. [@ha_installation] [@docker_compose_overview] [@docker_what_is_container]

## Verwendete Komponenten

### Aktoren und passive Bauteile

- 3-mm-LEDs als Lichtaktoren
- Widerstaende (1/4 W, 5 % Toleranz, 150 Ohm) zur Strombegrenzung

Hinweis zur elektrischen Auslegung: Bei 5 V Betriebsspannung und einer roten LED mit ca. 2 V Vorwaertsspannung ergibt sich bei 150 Ohm ein Strom von rund 20 mA. Das liegt am oberen Bereich dessen, was ein Arduino-Pin dauerhaft liefern sollte. In der Praxis ist daher auf Strombudget pro Pin und pro Port zu achten, bei Bedarf sind hoehere Widerstandswerte sinnvoll.

### Zusaetzliches Material

- Dupont-Crimp-Set inklusive Crimpzange
- Leitungen mit 0,5 mm2 Querschnitt
- PLA-Filament fuer das Modellhaus (hellgrau und dunkelgrau)

## Verwendete Frameworks und Protokolle

- **Home Assistant**
  Zentrale Smart-Home-Plattform fuer Geraeteintegration, Automationen und Dashboards. [@ha_installation] [@ha_automation]
- **Node-RED**
  Visuelle Entwicklungsumgebung fuer Datenfluesse und Logik zwischen MQTT, serieller Schnittstelle und Home Assistant. [@nodered_homepage]
- **MQTT**
  Leichtgewichtiges Publish/Subscribe-Protokoll fuer den Nachrichtenaustausch zwischen Diensten. [@oasis_mqtt_v5_2019] [@agyemang_mqtt_2022] [@ha_mqtt_integration]
- **Portainer**
  Weboberflaeche zur Verwaltung von Docker-Containern. [@portainer_docs]
- **Firmata**
  Standardisiertes Protokoll zur Steuerung eines Mikrocontrollers ueber eine serielle Host-Verbindung. [@arduino_firmata_docs] [@firmata_arduino_github]

## Smart-Home-Umsetzung mit Home Assistant und Node-RED

**Schueler:** Janik Gierer

## Theoretische Grundlagen

Ein Smart Home beschreibt ein vernetztes System aus Sensoren, Aktoren und Steuerlogik. Messwerte werden erfasst, interpretiert und ueber definierte Regeln in Aktionen umgesetzt. Die Bedienung erfolgt lokal oder remote ueber eine Benutzeroberflaeche. [@abutair_secure_privacy_smart_home_2020]

Im vorliegenden Projekt kommen drei Ebenen zusammen:

1. **Feldebene (Arduino):** direkte Anbindung von Sensoren und Aktoren.
2. **Verarbeitungsebene (Node-RED + MQTT):** Transport, Aufbereitung und Weiterleitung von Daten.
3. **Managementebene (Home Assistant):** Automationen, Visualisierung und Bedienung.

Technisch wichtig: Die Verbindung zwischen Arduino und Raspberry Pi erfolgt in diesem Aufbau primaer **seriell ueber Firmata**. MQTT wird zwischen Broker, Node-RED und Home Assistant eingesetzt, nicht als direkter Transportkanal zwischen Arduino Uno und Home Assistant. [@oasis_mqtt_v5_2019] [@ha_mqtt_integration] [@firmata_arduino_github]

### Sensorik, Aktorik und Steuerung im Modellhaus

Sensorik, Aktorik und Steuerung bilden das Grundprinzip des Systems:

- **Sensorik:** erfasst Zustaende wie Helligkeit, Bewegung, Temperatur oder Tuerkontakt.
- **Aktorik:** fuehrt Schaltvorgaenge aus, z. B. Licht ein/aus.
- **Steuerung:** setzt Regeln um und verbindet Ereignisse mit Aktionen.

Damit lassen sich kontinuierliche Werte (z. B. Temperatur) und diskrete Ereignisse (z. B. Bewegung erkannt) einheitlich verarbeiten. [@abutair_secure_privacy_smart_home_2020]

#### Sensoren im Projekt

- Helligkeitssensor fuer lichtabhaengige Schwellwerte
- PIR-Bewegungssensor als Anwesenheitstrigger
- Temperatursensor fuer klimaabhaengige Logik
- Tuerkontakt fuer offen/geschlossen-Zustaende

#### Aktoren im Projekt

Als Aktoren werden vor allem LEDs bzw. kleine Lichtkreise verwendet. Die Ansteuerung erfolgt digital (HIGH/LOW), bei hoeheren Lasten oder galvanischer Trennung ueber Relais bzw. Treiberstufen. Die maximalen Stroeme der Mikrocontroller-Ausgaenge duerfen dabei nicht ueberschritten werden.

### Arduino Uno mit StandardFirmata

Der Arduino Uno arbeitet mit dem Sketch **StandardFirmata**. Dadurch werden Pins vom Host-System (Raspberry Pi) ueber ein standardisiertes Protokoll gesetzt oder ausgelesen. [@arduino_firmata_docs] [@firmata_arduino_github]

StandardFirmata ist in der Arduino IDE verfuegbar unter:
`File -> Examples -> Firmata -> StandardFirmata`

Wichtige Bestandteile:

- `#include <Firmata.h>` bindet die Protokollbibliothek ein.
- `Firmata.begin(57600);` initialisiert die serielle Kommunikation.
- `Firmata.attach(...)` verknuepft eingehende Nachrichten mit Callback-Funktionen.
- In `loop()` werden Nachrichten mit `Firmata.available()` und `Firmata.processInput()` verarbeitet.

Diese Struktur erlaubt eine robuste, dauerhafte Host-Steuerung ohne eigenes komplexes Anwendungsprotokoll auf dem Mikrocontroller.

### Datenuebertragung und Kommunikation

Die Kommunikationskette ist klar getrennt:
Sensor/Aktor <-> Arduino (I/O) <-> serielle Verbindung <-> Node-RED <-> MQTT-Broker <-> Home Assistant.

Die Trennung reduziert Kopplung, erleichtert Fehlersuche und erlaubt spaetere Erweiterungen (weitere Sensoren, weitere Raeume, weitere Aktortypen). [@nodered_homepage] [@oasis_mqtt_v5_2019] [@ha_mqtt_integration]

#### MQTT als zentrales Nachrichtenprotokoll

MQTT arbeitet mit Clients, Topics und einem Broker. Komponenten publizieren Nachrichten oder abonnieren relevante Topics.

Beispielhafte Topic-Struktur:

- `haus/sensor/temperatur`
- `haus/sensor/helligkeit`
- `haus/licht/wohnzimmer/set`
- `haus/licht/wohnzimmer/state`

Empfohlene Praxis:

- QoS 0 fuer haeufige, unkritische Telemetrie
- QoS 1 fuer wichtigere Schaltmeldungen
- Retained Messages fuer letzten bekannten Zustand
- Last Will and Testament (LWT) fuer Offline-Erkennung

[@oasis_mqtt_v5_2019] [@ha_mqtt_integration]

#### Node-RED als Logik- und Schnittstellenebene

Node-RED verbindet serielle Daten und MQTT-Topics mit leicht wartbaren Flows. Typischer Ablauf:

1. MQTT-In oder Serial-In empfaengt Daten.
2. Function-Node prueft und transformiert Payloads.
3. MQTT-Out oder Serial-Out sendet Ergebnisse an Zielsysteme.

Dadurch bleibt die Steuerlogik transparent und ohne Quellcode-Neubau anpassbar. [@nodered_homepage]

#### Serieller Zugriff unter Linux

Arduino-Geraete erscheinen meist als `/dev/ttyACM0` oder `/dev/ttyUSB0`. Fuer stabilen Betrieb gilt:

- nur ein Prozess darf den Port gleichzeitig nutzen
- korrekte Benutzerrechte auf das Device muessen gesetzt sein
- bei Neustarts kann sich der Device-Name aendern

[@nodered_raspberrypi]

### Home Assistant als zentrale Steuereinheit

Home Assistant uebernimmt Integration, Automationsausfuehrung und Visualisierung. In diesem Projekt wird Home Assistant lokal am Raspberry Pi betrieben und mit MQTT-Entitaeten verbunden. [@ha_installation] [@ha_mqtt_integration] [@ha_automation]

#### MQTT-Integration

Die Anbindung erfolgt manuell oder ueber MQTT Discovery. Discovery reduziert Konfigurationsaufwand, weil Entitaeten automatisch erstellt werden, sobald gueltige Discovery-Nachrichten publiziert werden. [@ha_mqtt_sensor]

#### Automationen

Automationen bestehen aus Trigger, optionalen Bedingungen und Aktionen. Beispiel:

- Trigger: Bewegung erkannt und Helligkeit unter Schwellwert
- Bedingung: Automatikmodus aktiv
- Aktion: Licht einschalten, nach Timeout ausschalten

Damit ist das Verhalten reproduzierbar und im Dashboard nachvollziehbar. [@ha_automation]

### Visualisierung und Benutzeroberflaeche

Die Bedienung erfolgt ueber Home-Assistant-Dashboards. Verwendet werden u. a. Entities-, Button- und Verlaufskarten fuer Schaltzustaende und Messwertverlaeufe. [@ha_dashboards_intro] [@ha_cards]

## Praktische Umsetzung

### Hardwareaufbau

#### Stromversorgung und Verkabelung

Der Raspberry Pi wird mit 5 V versorgt, der Arduino ueber USB angebunden. LED-Kreise werden mit Vorwiderstaenden betrieben, um Bauteile und I/O-Pins zu schuetzen. Fuer flexible Anpassungen im Modellhaus wurden gecrimpte Leitungen und steckbare Verbindungen verwendet.

#### Einbau von LEDs, Relais und Sensoren

Die Aktoren wurden raumbezogen im Modellhaus positioniert. Sensoren wurden so platziert, dass sie reale Nutzungsszenarien gut abbilden (z. B. Bewegung im Eingangsbereich, Helligkeit an typischer Fensterposition). Relais bzw. Treiber kommen dort zum Einsatz, wo Lasten nicht direkt ueber den Mikrocontroller geschaltet werden sollen.

### Arduino-Integration

Durch StandardFirmata liest der Host (Node-RED) Eingangs- und Sensordaten zyklisch aus und setzt Ausgaenge fuer Aktoren. Schaltbefehle werden deterministisch pro Nachricht ausgefuehrt, was die Fehlersuche vereinfacht. [@arduino_firmata_docs] [@firmata_arduino_github]

### Node-RED-Workflows

- MQTT-In-Nodes abonnieren Sollwerte und Steuerbefehle.
- Function-Nodes validieren Wertebereiche und Zustandslogik.
- Serial-Out-Nodes senden Befehle an den Arduino.
- MQTT-Out-Nodes publizieren Ist-Zustaende fuer Home Assistant.

Dieses Muster bildet eine klare Bruecke zwischen Hardwareebene und Visualisierungsebene. [@nodered_homepage] [@oasis_mqtt_v5_2019]

### Erstinbetriebnahme am Raspberry Pi

Ein strukturierter Erstaufbau reduziert spaetere Fehler:

1. System aktualisieren: `sudo apt update && sudo apt upgrade -y`
2. Docker installieren und Benutzer zur Docker-Gruppe hinzufuegen. [@docker_compose_overview]
3. Projektordner und Volume-Struktur anlegen.
4. `compose.yaml` mit Home Assistant, MQTT und Portainer erstellen. [@docker_compose_file_reference]
5. Container starten: `docker compose up -d`
6. Status pruefen: `docker ps`, Logs bei Bedarf mit `docker logs <container>`
7. Home Assistant Onboarding abschliessen und MQTT anbinden. [@ha_installation] [@ha_mqtt_integration]
8. Portainer initial konfigurieren. [@portainer_docs]

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

```bash
mkdir smarthome
cd smarthome
mkdir -p homeassistant
mkdir -p mosquitto/config mosquitto/data mosquitto/log
mkdir -p portainer
```

#### Docker und Compose auf Raspberry Pi OS

```bash
sudo apt update && sudo apt upgrade -y
curl -fsSL https://get.docker.com | sudo sh
sudo usermod -aG docker $USER
newgrp docker
docker run --rm hello-world
sudo apt install -y docker-compose-plugin
docker compose version
```

#### YAML-Datei erstellen

```bash
nano compose.yaml
```

Danach den Compose-Inhalt einfuegen und speichern.

#### Betrieb nach Neustart

- Im Projektordner starten: `docker compose up -d`
- Containerstatus pruefen: `docker ps`
- IP-Adresse ermitteln: `hostname -I`
- Zugriffe:
  - Home Assistant: `http://<raspberry-ip>:8123`
  - Portainer: `http://<raspberry-ip>:9000`

### Node-RED-Installation auf Raspberry Pi

```bash
bash <(curl -sL https://github.com/node-red/linux-installers/releases/latest/download/update-nodejs-and-nodered-deb)
sudo systemctl enable nodered.service
sudo systemctl start nodered.service
sudo systemctl status nodered.service --no-pager
```

Editor-Zugriff:

- lokal: `http://localhost:1880`
- im Netzwerk: `http://<raspberry-ip>:1880`

[@nodered_raspberrypi]

### Bedienung und Tests

Die taegliche Bedienung erfolgt ueber Home-Assistant-Dashboards; Node-RED arbeitet als Hintergrundlogik und Datendrehscheibe. [@ha_dashboards_intro] [@nodered_homepage]

#### Endgeraete

Steuerung ist ueber Browser am PC, Tablet und Smartphone moeglich. Schaltbefehle werden per Button gesendet, Zustandsaenderungen werden direkt visualisiert. [@ha_cards]

#### Test der Licht- und Heizungslogik

Testablauf:

1. Ereignis simulieren (z. B. Dunkelheit oder Bewegung).
2. Trigger und Bedingungen pruefen.
3. Aktorzustand im Dashboard verifizieren.
4. Rueckmeldung ueber MQTT-State-Topic kontrollieren.

Ergebnis: Die Lichtsteuerung und zustandsabhaengigen Schaltungen liefen im Testbetrieb stabil. Kommunikationsunterbrechungen konnten reproduziert und ueber Reconnect-Strategien abgefangen werden.

### Fehleranalyse und Optimierungen

#### Serielle Kommunikation

Typische Fehler:

- Portkonflikte durch parallelen Zugriff
- Device-Wechsel (`/dev/ttyUSB0` zu `/dev/ttyACM0`)
- unzureichende Rechte auf dem seriellen Device

Massnahmen:

- festen Port in Node-RED konfigurieren
- konkurrierende Prozesse beenden
- Dienste nach Konfigurationsaenderungen sauber neu starten

#### MQTT-Stabilitaet

Zur Absicherung wurden QoS, Retained Messages und LWT gezielt eingesetzt. Dadurch bleiben Offline-Zustaende sichtbar und nach Reconnect ist der letzte gueltige Zustand schneller wiederhergestellt. [@oasis_mqtt_v5_2019] [@ha_mqtt_integration]

## Ausblick

Die Architektur ist modular und fuer Erweiterungen vorbereitet.

### Sprachsteuerung

Eine Erweiterung mit Home-Assistant-Voice oder Alexa-Anbindung ist moeglich. [@ha_voice_control] [@ha_alexa_smart_home]

### Skalierung auf mehrere Raeume

Die Topic- und Entitaetsstruktur kann raumweise erweitert werden, z. B.:

- `haus/licht/kueche/set`
- `haus/licht/schlafzimmer/set`
- `haus/sensor/flur/bewegung`

### Weitere Sensorik

Zusaetzliche Sensoren wie CO2-, Luftqualitaets- oder Feuchtigkeitssensoren koennen direkt in bestehende Flows und Automationen integriert werden. [@ha_dev_sensor_entity]


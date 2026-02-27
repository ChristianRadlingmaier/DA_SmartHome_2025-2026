# Teilaufgabe Schüler Gierer

\textauthor{Janik Gierer}

Dieses Kapitel beschreibt die theoretischen Grundlagen sowie die bisher umgesetzten technischen Bausteine meines Teilprojekts innerhalb der Diplomarbeit. Der Schwerpunkt liegt auf dem Zusammenspiel von Home Assistant, Node-RED, MQTT, Docker und einem Arduino Uno in einem Smart-Home-Modellhaus. Es wird bewusst darauf geachtet, den Inhalt fachlich korrekt, nachvollziehbar und reproduzierbar darzustellen.

Ziel dieses Kapitels ist es, nicht nur einzelne Werkzeuge aufzulisten, sondern den Gesamtzusammenhang zu erklären: Welche Rolle übernimmt welche Komponente, wie werden Daten transportiert, wie werden Zustandsänderungen verarbeitet und wie wird daraus ein bedienbares, erweiterbares Smart-Home-System. [@ha_installation] [@nodered_homepage] [@oasis_mqtt_v5_2019]

## Einordnung und Ziel dieses Abschnitts

Der vorliegende Abschnitt ist eine Verbindung aus Literaturrecherche und technischer Dokumentation. Er soll einem fachlich interessierten Leser ermöglichen, den praktischen Teil logisch nachzuvollziehen, ohne vorauszusetzen, dass die konkrete Projektumgebung bereits bekannt ist.

Die Ausführungen decken drei Ebenen ab:

1. **Grundlagenebene:** Definitionen zu Smart Home, Sensorik, Aktorik und Steuerung.
2. **Architekturebene:** Aufbau des Gesamtsystems mit Raspberry Pi, Arduino, Node-RED, MQTT und Home Assistant.
3. **Umsetzungsebene:** Betriebs- und Konfigurationsschritte, die im Projekt bereits beschrieben wurden.

Die Inhalte sind so formuliert, dass keine zusätzlichen praktischen Ergebnisse behauptet werden, die nicht bereits Teil der bisherigen Projektarbeit sind.

## Zielsetzung und fachliche Abgrenzung

Die zentrale Zielsetzung besteht darin, ein modulares und verständliches Smart-Home-System im Modellmaßstab zu realisieren, das typische Funktionen realer Hausautomation technisch korrekt abbildet. Dazu gehören die Erfassung von Umgebungsdaten, die Ausführung von Schaltaktionen sowie die sichtbare Darstellung der Systemzustände in einer Benutzeroberfläche.

Die Arbeit verfolgt nicht das Ziel, ein marktreifes Produkt zu entwickeln. Der Fokus liegt stattdessen auf:

- nachvollziehbarer Architektur,
- klar getrennten Verantwortlichkeiten der Systemkomponenten,
- robuster Kommunikation zwischen den beteiligten Diensten,
- guter Erweiterbarkeit für spätere Projektphasen.

Diese Abgrenzung ist wesentlich, damit Bewertung und Dokumentation auf denselben technischen Rahmenbedingungen basieren.

## Verwendete Komponenten

### Aktoren und passive Bauteile

- 3-mm-LEDs als Lichtaktoren
- Widerstände (1/4 W, 5 % Toleranz, 150 Ohm) zur Strombegrenzung

Die LED-Kreise bilden die zentrale, sichtbare Aktorik im Modellhaus. Ihr Vorteil ist die klare Rückmeldung bei Schaltvorgängen: Jede Zustandsänderung ist direkt erkennbar und kann zusätzlich im Dashboard kontrolliert werden.

**Hinweis zur Auslegung:** Bei 5 V Betriebsspannung, einer typischen LED-Vorwärtsspannung von ca. 2 V und 150 Ohm Vorwiderstand liegt der Strom rechnerisch im Bereich von etwa 20 mA. Das ist für viele Mikrocontroller-Pins bereits nahe am sinnvollen Grenzbereich. Für einen stabilen Dauerbetrieb ist daher eine sorgfältige Stromverteilung wichtig, insbesondere wenn mehrere Kanäle gleichzeitig geschaltet werden.

### Sensorik

Im Projektkontext werden folgende Sensorklassen betrachtet:

- Helligkeitssensoren,
- PIR-Bewegungssensoren,
- Temperatursensoren,
- Türkontakte.

Die Sensorik stellt die Datengrundlage für Automationen dar. Ohne konsistente, wiederholbar erfasste Eingangswerte ist eine reproduzierbare Steuerlogik nicht möglich.

### Zusätzliches Material und Modellhausbezug

- Dupont-Crimp-Set inklusive Crimpzange
- Leitungen mit 0,5 mm2 Querschnitt
- PLA-Filament für den Modellhausaufbau (hellgrau und dunkelgrau)

Der Aufbau im Modellhaus hat einen didaktischen Vorteil: Leitungsführung, Kanalzuordnung und Schaltverhalten werden sichtbar. Dadurch kann die technische Funktion nicht nur softwareseitig, sondern auch mechanisch und elektrisch nachvollzogen werden.

## Verwendete Frameworks und Protokolle

### Home Assistant

Home Assistant dient als zentrale Integrations- und Bedienplattform. Hier laufen Entitäten, Automationen und Dashboards zusammen. Damit entsteht ein einheitlicher Blick auf den Systemzustand. [@ha_installation] [@ha_automation]

Im Projekt ist Home Assistant besonders wichtig für:

- die Darstellung von Ist-Zuständen,
- die Auslösung manueller Schaltvorgänge,
- die Definition regelbasierter Automationen.

### Node-RED

Node-RED wird als visuelle Verarbeitungsschicht eingesetzt. Datenflüsse können über Nodes modelliert, angepasst und nachvollzogen werden. Das erleichtert Iterationen während der Entwicklung deutlich, da Logikbausteine ohne kompletten Neuaufbau des Systems angepasst werden können. [@nodered_homepage]

Wesentliche Rolle von Node-RED im Projekt:

- Brücke zwischen serieller Kommunikation und MQTT,
- Validierung und Transformation von Payloads,
- geordnete Weitergabe von Befehlen und Statusmeldungen.

### MQTT

MQTT wird als leichtgewichtiges Publish/Subscribe-Protokoll für den Nachrichtenaustausch zwischen Diensten eingesetzt. Der Einsatz ist vor allem bei verteilten Komponenten sinnvoll, weil Sender und Empfänger nicht direkt gekoppelt sein müssen. [@oasis_mqtt_v5_2019] [@agyemang_mqtt_2022] [@ha_mqtt_integration]

Typische Vorteile im vorliegenden Kontext:

- geringe Protokolloverheads,
- einfache Skalierung auf weitere Topics und Entitäten,
- klare Trennung von Kommando- und Statuskanälen.

### Portainer

Portainer dient als Weboberfläche zur Verwaltung der Docker-Container. Das ist besonders hilfreich, wenn mehrere Dienste parallel betrieben und bei Bedarf einzeln neu gestartet, aktualisiert oder überwacht werden müssen. [@portainer_docs]

### Firmata

Firmata ist ein standardisiertes Protokoll, mit dem ein Host-System (hier Raspberry Pi bzw. Node-RED) einen Mikrocontroller (Arduino Uno) über die serielle Schnittstelle ansteuern kann. [@arduino_firmata_docs] [@firmata_arduino_github]

Der praktische Nutzen liegt darin, dass keine vollständig eigene serielle Protokolldefinition implementiert werden muss. Stattdessen wird ein etablierter Standard genutzt.

## Systemarchitektur

## Smart-Home-Umsetzung mit Home Assistant und Node-RED

**Schüler:** Janik Gierer

### Architektur in drei Ebenen

Das System kann in drei logisch getrennte Ebenen aufgeteilt werden:

1. **Feldebene (Arduino):** Direkte Anbindung von Sensorik und Aktorik.
2. **Verarbeitungsebene (Node-RED + MQTT):** Datenfluss, Protokollbrücke und Logikaufbereitung.
3. **Managementebene (Home Assistant):** Visualisierung, Automationen und Bedienung.

Diese Trennung erhöht die Wartbarkeit, weil Änderungen auf einer Ebene nicht automatisch alle anderen Ebenen brechen.

### Kommunikationspfad

Im aktuellen Aufbau läuft die Kommunikation entlang eines klaren Pfades:

Sensor/Aktor <-> Arduino (I/O) <-> serielle Verbindung (Firmata) <-> Node-RED <-> MQTT-Broker <-> Home Assistant.

Damit ist fachlich sauber getrennt:

- **I/O-nahe Steuerung** auf Mikrocontroller-Ebene,
- **Nachrichtentransport und Aufbereitung** auf Middleware-Ebene,
- **Benutzerinteraktion und Regelwerk** auf Plattform-Ebene.

Technisch wichtig: In dieser Architektur ist MQTT nicht der direkte Transportweg vom Arduino Uno zu Home Assistant. Der Arduino ist primär seriell via Firmata angebunden; MQTT wird zwischen den Diensten auf dem Raspberry Pi genutzt. [@firmata_arduino_github] [@ha_mqtt_integration]

## Theoretische Grundlagen

### Begriff Smart Home

Ein Smart Home ist ein vernetztes System, in dem Sensorik, Aktorik und Steuerlogik zusammenwirken. Eingehende Daten werden ausgewertet und führen je nach Regelwerk zu Aktionen. Die Interaktion kann automatisch oder manuell über eine Benutzeroberfläche erfolgen. [@abutair_secure_privacy_smart_home_2020]

Für diese Arbeit bedeutet das konkret:

- Sensoren liefern Ereignisse bzw. Messwerte,
- die Logik entscheidet über Aktionen,
- Aktoren setzen diese Aktionen sichtbar um,
- die Plattform stellt alles nachvollziehbar dar.

### Sensorik

Sensorik umfasst die strukturierte Erfassung physischer Zustände. Im Modellhaus sind das insbesondere Helligkeit, Bewegung, Temperatur und Türstatus. Jeder Sensortyp liefert dabei eine andere Datencharakteristik:

- diskrete Ereignisse (z. B. Bewegung erkannt),
- quasi-binäre Zustände (z. B. Tür offen/geschlossen),
- kontinuierliche Werte (z. B. Temperatur).

Diese Unterschiede sind für die Auswertung relevant, da Triggerlogik und Entprellung je nach Signaltyp unterschiedlich gestaltet werden müssen.

### Aktorik

Aktorik setzt digitale Steuerentscheidungen in physische Wirkung um. Im Projekt sind dies primär Lichtkanäle (LEDs). Auch wenn die Lasten im Modell klein sind, gelten dieselben Grundprinzipien wie in größeren Anlagen:

- sichere elektrische Auslegung,
- klare Kanalzuordnung,
- reproduzierbares Schaltverhalten.

Für höhere Lasten wären Treiberstufen oder Relais zwingend erforderlich, um Mikrocontroller-Ausgänge zu entlasten.

### Steuerung

Steuerung verbindet Sensorik und Aktorik über ein Regelwerk. Ein typisches Muster ist:

1. Eingangssignal trifft ein.
2. Bedingungen werden geprüft.
3. Aktion wird ausgeführt.
4. Zustand wird rückgemeldet.

Je klarer dieses Muster in Topics, Flows und Automationen abgebildet ist, desto besser sind Fehlersuche und Erweiterung möglich.

## Arduino Uno mit StandardFirmata

### Rolle des Arduino im Gesamtsystem

Der Arduino Uno dient als direkte I/O-Schnittstelle zur physikalischen Ebene. Er ist dort sinnvoll, wo Signale in Echtzeit eingelesen oder Ausgänge unmittelbar gesetzt werden müssen.

### Einsatz von StandardFirmata

Im Projekt wird StandardFirmata verwendet. Dadurch kann der Arduino vom Host aus gesteuert werden, ohne dass für jede Änderung ein separates, proprietäres Applikationsprotokoll aufgesetzt werden muss. [@arduino_firmata_docs] [@firmata_arduino_github]

In der Arduino IDE ist der Sketch verfügbar unter:
`File -> Examples -> Firmata -> StandardFirmata`

Wesentliche Bestandteile:

- `#include <Firmata.h>` für die Protokollfunktionen,
- `Firmata.begin(57600);` für die serielle Initialisierung,
- `Firmata.attach(...)` für die Zuordnung eingehender Nachrichten zu Callbacks,
- zyklische Verarbeitung in `loop()` mit `Firmata.available()` und `Firmata.processInput()`.

Dieses Vorgehen ist für ein Lern- und Demonstrationsprojekt sinnvoll, weil es robuste Grundfunktionalität bereitstellt und den Fokus auf Systemintegration statt auf Low-Level-Protokolldesign legt.

## Datenübertragung und Kommunikationsdesign

### MQTT als Nachrichtenrückgrat

MQTT arbeitet mit einem Broker als zentralem Verteiler. Clients publizieren Nachrichten auf Topics oder abonnieren Topics. Der Broker entkoppelt damit Sender und Empfänger. [@oasis_mqtt_v5_2019]

Typischer Nutzen in dieser Arbeit:

- Sensorwerte können mehreren Verbrauchern bereitgestellt werden.
- Schaltbefehle und Rückmeldungen bleiben sauber getrennt.
- Der Datenfluss ist durch Topic-Namen transparent.

### Topic-Struktur

Eine hierarchische Benennung erleichtert Wartung und Skalierung. Beispielhafte Struktur:

- `haus/sensor/temperatur`
- `haus/sensor/helligkeit`
- `haus/licht/wohnzimmer/set`
- `haus/licht/wohnzimmer/state`

Damit ist aus dem Topic bereits erkennbar, ob es sich um Messdaten, Schaltkommandos oder Statusmeldungen handelt.

### Command- und State-Trennung

Die Trennung von Soll- und Ist-Kanälen verhindert Mehrdeutigkeiten:

- `.../set` repräsentiert den angeforderten Zielzustand.
- `.../state` repräsentiert den tatsächlichen Rückmeldezustand.

Diese Trennung ist vor allem bei Dashboards und Automationen wichtig, um keine falschen Annahmen über den realen Aktorzustand zu treffen.

### QoS, Retain und LWT

Die Auswahl passender MQTT-Mechanismen verbessert Robustheit:

- **QoS 0:** geeignet für häufige, unkritische Telemetrie.
- **QoS 1:** geeignet für wichtigere Schaltmeldungen.
- **Retained Messages:** stellen den letzten bekannten Zustand für neue Subscriber bereit.
- **Last Will and Testament (LWT):** signalisiert, wenn ein Client unerwartet offline geht.

Im Zusammenspiel mit Home Assistant erhöht das die Nachvollziehbarkeit bei Verbindungsunterbrechungen und Neustarts. [@ha_mqtt_integration]

## Node-RED als Logik- und Integrationsschicht

Node-RED ist in dieser Arbeit mehr als ein Visualisierungstool für Datenflüsse. Es übernimmt die technische Mittlerrolle zwischen serieller Hardwareanbindung und MQTT-basierter Plattformintegration. [@nodered_homepage]

Ein typischer Flow besteht aus:

1. Eingang über MQTT-In oder Serial-In.
2. Validierung und Transformation in Function-Nodes.
3. Weitergabe über MQTT-Out oder Serial-Out.

Dieses Muster ist wiederverwendbar und bildet eine gute Grundlage für zusätzliche Kanäle oder Räume.

### Vorteile für die Projektarbeit

- Schnelle Anpassung ohne komplettes Re-Deployment.
- Transparente Darstellung der Datenpfade.
- Leichte Erweiterung um Filter- und Plausibilitätslogik.

### Serieller Zugriff unter Linux

Arduino-Geräte erscheinen typischerweise als `/dev/ttyACM0` oder `/dev/ttyUSB0`. Für stabilen Betrieb müssen drei Punkte sichergestellt sein:

- exklusiver Portzugriff,
- korrekte Device-Rechte,
- konsistente Portzuordnung nach Neustarts.

Diese Punkte sind häufige Fehlerquellen in gemischten Hardware-/Software-Setups. [@nodered_raspberrypi]

## Home Assistant als zentrale Steuereinheit

Home Assistant bildet die Bedien- und Automationsoberfläche des Systems. Entitäten, Trigger und Dashboards werden dort zusammengeführt. [@ha_installation] [@ha_automation]

### MQTT-Integration

Die Einbindung kann manuell oder über MQTT Discovery erfolgen. Discovery reduziert Konfigurationsaufwand, da Entitäten aus gültigen Discovery-Nachrichten erzeugt werden können. [@ha_mqtt_sensor]

### Automationen

Automationen folgen dem Schema Trigger -> Bedingungen -> Aktionen. Ein für das Modellhaus typisches Muster ist:

- Trigger: Bewegung erkannt und Helligkeit unter Schwellwert,
- Bedingung: Automatikmodus aktiv,
- Aktion: Licht einschalten und nach definierter Zeit ausschalten.

Das Muster ist bewusst einfach, aber präzise genug, um die Trennung zwischen Sensordatenerfassung und Aktorreaktion klar zu halten.

### Dashboards und Visualisierung

Die Visualisierung erfolgt über Dashboard-Karten wie Entities-, Button- und Verlaufskarten. Damit sind Schaltzustände, Messwerttrends und manuelle Eingriffe auf einer Oberfläche verfügbar. [@ha_dashboards_intro] [@ha_cards]

## Praktische Umsetzung

### Hardwareaufbau

#### Stromversorgung und Verkabelung

Der Raspberry Pi wird mit 5 V betrieben, der Arduino ist über USB angebunden. LED-Kreise sind über Vorwiderstände abgesichert. Für den Aufbau wurden gecrimpte und steckbare Verbindungen genutzt, um Anpassungen ohne Lötarbeiten zu ermöglichen.

#### Einbau von LEDs, Relais und Sensoren

Die Aktoren wurden den Räumen des Modellhauses zugeordnet. Sensoren wurden so positioniert, dass typische Nutzungssituationen abgebildet werden können (z. B. Bewegung im Eingangsbereich, Helligkeitsmessung in raumtypischer Lage). Relais bzw. Treiberstufen werden dort vorgesehen, wo Lasttrennung erforderlich ist.

### Arduino-Integration

Durch StandardFirmata liest der Host Eingangs- und Sensordaten aus und setzt Ausgänge für Aktoren. Schaltbefehle werden deterministisch pro eingehender Nachricht verarbeitet. [@arduino_firmata_docs] [@firmata_arduino_github]

### Node-RED-Workflows

Die im Projekt verwendete Logik kann wie folgt zusammengefasst werden:

- MQTT-In-Nodes abonnieren Sollwerte und Triggerinformationen,
- Function-Nodes validieren Daten und bereiten Kommandos auf,
- Serial-Out-Nodes übertragen Befehle an den Arduino,
- MQTT-Out-Nodes melden Ist-Zustände zurück.

Durch diese Kette bleibt die Steuerlogik nachvollziehbar und modular.

### Erstinbetriebnahme am Raspberry Pi

Für einen reproduzierbaren Erstaufbau hat sich ein klarer Ablauf bewährt:

1. System aktualisieren: `sudo apt update && sudo apt upgrade -y`
2. Docker installieren und Benutzer zur Docker-Gruppe hinzufügen. [@docker_compose_overview]
3. Projektverzeichnis samt Volume-Struktur anlegen.
4. `compose.yaml` für Home Assistant, MQTT und Portainer erstellen. [@docker_compose_file_reference]
5. Dienste starten: `docker compose up -d`
6. Laufzeitstatus prüfen: `docker ps`, Logs mit `docker logs <container>`
7. Home Assistant Onboarding abschließen und MQTT integrieren. [@ha_mqtt_integration]
8. Portainer initial konfigurieren. [@portainer_docs]

Der Vorteil dieser festen Reihenfolge ist, dass Fehlerquellen früh sichtbar werden und nicht erst später bei der Automationslogik auftreten.

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

Danach den Compose-Inhalt einfügen und speichern.

#### Betrieb nach Neustart

- Im Projektordner starten: `docker compose up -d`
- Containerstatus prüfen: `docker ps`
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

## Bedienung und Steuerung

Die tägliche Bedienung erfolgt über Home-Assistant-Dashboards. Node-RED arbeitet parallel als Logik- und Integrationsschicht. Dadurch wird die Benutzeroberfläche von der eigentlichen Nachrichtenverarbeitung entkoppelt. [@ha_dashboards_intro] [@nodered_homepage]

### Steuerung über Endgeräte

Der Zugriff ist über Browser auf PC, Tablet und Smartphone möglich. Schaltbefehle werden in der Regel per Button ausgelöst, Zustandsänderungen erscheinen als direkte Rückmeldung in den Karten.

### Bedeutung der Rückmeldelogik

Besonders wichtig für die Alltagstauglichkeit ist die Rückmeldelogik:

- Schaltkommandos allein reichen nicht aus,
- erst die Rückmeldung über State-Topics macht den realen Zustand transparent,
- Automationen können so auf echte Zustandsänderungen reagieren.

Diese Trennung reduziert Fehlinterpretationen in der Bedienoberfläche.

## Test und Validierung im bisherigen Projektstand

Die bisherige Validierung orientiert sich an den definierten Use-Cases und den vorhandenen Komponenten. Dabei wurde der Fokus auf funktionale Korrektheit und Kommunikationsstabilität gelegt.

Typischer Ablauf:

1. Ereignis erzeugen (z. B. Dunkelheit, Bewegung oder Temperaturänderung).
2. Trigger- und Bedingungslogik beobachten.
3. Aktorreaktion am Modellhaus und im Dashboard vergleichen.
4. Rückmeldung über Topics und Statuskarten kontrollieren.

Der bisher dokumentierte Projektbetrieb zeigt, dass Lichtsteuerung und zustandsabhängige Schaltabläufe reproduzierbar ausgelöst werden können. Verbindungsunterbrechungen wurden als Fehlerfall betrachtet und in der Logik berücksichtigt.

## Fehleranalyse und Optimierungen

### Serielle Kommunikation

Typische Problemquellen:

- Port ist bereits durch einen anderen Prozess belegt,
- Device-Bezeichnung ändert sich nach Neustart,
- fehlende Rechte auf `/dev/tty...`.

Bewährte Maßnahmen:

- festen Port in Node-RED konfigurieren,
- konkurrierende Prozesse beenden,
- Dienst nach Änderungen sauber neu starten.

Diese Maßnahmen verbessern die Stabilität der Host-zu-Arduino-Kommunikation deutlich.

### MQTT-Stabilität

Bei MQTT-Verbindungen sind vor allem Reconnect-Verhalten und Zustandskonsistenz entscheidend. Durch geeignete Kombination aus QoS, Retained Messages und LWT kann das System robuster auf Netzunterbrechungen reagieren. [@oasis_mqtt_v5_2019] [@ha_mqtt_integration]

Wichtige Beobachtung für den Betrieb:

- Offline-Zustände sollen sichtbar werden,
- nach Wiederverbindung soll ein konsistenter Ausgangszustand hergestellt werden,
- Dashboards dürfen dabei keine veralteten Zustandsbilder dauerhaft anzeigen.

## bertragbarkeit auf reale Wohnhaus-Szenarien

Die im Modellhaus umgesetzte Architektur ist grundsätzlich auf reale Umgebungen übertragbar, wenn elektrische Auslegung, Sicherheitsanforderungen und Lasttrennung entsprechend angepasst werden. Der wesentliche Mehrwert des Modellansatzes liegt darin, dass die Struktur bereits jetzt klar definiert ist:

- getrennte Ebenen für I/O, Verarbeitung und Bedienung,
- standardisierte Schnittstellen zwischen den Ebenen,
- zentrale Sicht auf den Gesamtzustand.

Damit ist eine gute Grundlage für spätere Skalierung geschaffen, ohne die Grundarchitektur neu entwerfen zu müssen.

## Zusammenfassende Bewertung des Teilprojekts

Aus technischer Sicht zeigt der bisherige Stand, dass der gewählte Stack für ein modulares Smart-Home-Modell geeignet ist:

- Home Assistant als zentrale Plattform,
- Node-RED als flexible Integrationslogik,
- MQTT als entkoppeltes Transportprotokoll,
- Docker für reproduzierbaren Dienstbetrieb,
- Arduino/Firmata für den direkten Hardwarezugriff.

Der zentrale Vorteil dieser Kombination liegt in der klaren Rollenverteilung. Jede Komponente hat eine nachvollziehbare Aufgabe, wodurch Entwicklung, Fehlersuche und Erweiterung strukturiert möglich sind.

## Ausblick

Die bestehende Architektur ist für Erweiterungen vorbereitet.

### Sprachsteuerung

Eine mögliche Erweiterung ist die Einbindung von Sprachsteuerung, z. B. über Home-Assistant-Voice oder Alexa-Integration. [@ha_voice_control] [@ha_alexa_smart_home]

### Skalierung auf mehrere Räume

Die bestehende Topic- und Entitätsstruktur kann auf weitere Räume erweitert werden, etwa:

- `haus/licht/kche/set`
- `haus/licht/schlafzimmer/set`
- `haus/sensor/flur/bewegung`

Wichtig ist dabei, die bisherige Namenskonvention konsistent beizubehalten.

### Einbindung weiterer Sensorik

Zusätzliche Sensoren (z. B. CO2, Luftqualität, Feuchtigkeit) können als weitere Entitäten in Home Assistant und als weitere Datenkanäle in Node-RED integriert werden. [@ha_dev_sensor_entity]

### Methodischer Ausblick

Für die weitere Arbeit ist es sinnvoll, bei jeder Erweiterung denselben Ablauf beizubehalten:

1. fachliche Anforderung beschreiben,
2. Datenfluss definieren,
3. Topic- und Entitätsmodell festlegen,
4. Visualisierung und Testfall dokumentieren.

So bleibt das System auch bei wachsendem Umfang technisch konsistent und dokumentierbar.




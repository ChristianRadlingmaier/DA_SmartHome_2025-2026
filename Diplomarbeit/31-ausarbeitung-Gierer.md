# Teilaufgabe Schueler Gierer

\textauthor{Janik Gierer}

Dieses Kapitel beschreibt die theoretischen Grundlagen sowie die bisher umgesetzten technischen Bausteine meines Teilprojekts innerhalb der Diplomarbeit. Der Schwerpunkt liegt auf dem Zusammenspiel von Home Assistant, Node-RED, MQTT, Docker und einem Arduino Uno in einem Smart-Home-Modellhaus. Es wird bewusst darauf geachtet, den Inhalt fachlich korrekt, nachvollziehbar und reproduzierbar darzustellen.

Ziel dieses Kapitels ist es, nicht nur einzelne Werkzeuge aufzulisten, sondern den Gesamtzusammenhang zu erklaeren: Welche Rolle uebernimmt welche Komponente, wie werden Daten transportiert, wie werden Zustandsaenderungen verarbeitet und wie wird daraus ein bedienbares, erweiterbares Smart-Home-System. [@ha_installation] [@nodered_homepage] [@oasis_mqtt_v5_2019]

## Einordnung und Ziel dieses Abschnitts

Der vorliegende Abschnitt ist eine Verbindung aus Literaturrecherche und technischer Dokumentation. Er soll einem fachlich interessierten Leser ermoeglichen, den praktischen Teil logisch nachzuvollziehen, ohne vorauszusetzen, dass die konkrete Projektumgebung bereits bekannt ist.

Die Ausfuehrungen decken drei Ebenen ab:

1. **Grundlagenebene:** Definitionen zu Smart Home, Sensorik, Aktorik und Steuerung.
2. **Architekturebene:** Aufbau des Gesamtsystems mit Raspberry Pi, Arduino, Node-RED, MQTT und Home Assistant.
3. **Umsetzungsebene:** Betriebs- und Konfigurationsschritte, die im Projekt bereits beschrieben wurden.

Die Inhalte sind so formuliert, dass keine zusaetzlichen praktischen Ergebnisse behauptet werden, die nicht bereits Teil der bisherigen Projektarbeit sind.

## Zielsetzung und fachliche Abgrenzung

Die zentrale Zielsetzung besteht darin, ein modulares und verstaendliches Smart-Home-System im Modellmassstab zu realisieren, das typische Funktionen realer Hausautomation technisch korrekt abbildet. Dazu gehoeren die Erfassung von Umgebungsdaten, die Ausfuehrung von Schaltaktionen sowie die sichtbare Darstellung der Systemzustaende in einer Benutzeroberflaeche.

Die Arbeit verfolgt nicht das Ziel, ein marktreifes Produkt zu entwickeln. Der Fokus liegt stattdessen auf:

- nachvollziehbarer Architektur,
- klar getrennten Verantwortlichkeiten der Systemkomponenten,
- robuster Kommunikation zwischen den beteiligten Diensten,
- guter Erweiterbarkeit fuer spaetere Projektphasen.

Diese Abgrenzung ist wesentlich, damit Bewertung und Dokumentation auf denselben technischen Rahmenbedingungen basieren.

## Verwendete Komponenten

### Aktoren und passive Bauteile

- 3-mm-LEDs als Lichtaktoren
- Widerstaende (1/4 W, 5 % Toleranz, 150 Ohm) zur Strombegrenzung

Die LED-Kreise bilden die zentrale, sichtbare Aktorik im Modellhaus. Ihr Vorteil ist die klare Rueckmeldung bei Schaltvorgaengen: Jede Zustandsaenderung ist direkt erkennbar und kann zusaetzlich im Dashboard kontrolliert werden.

**Hinweis zur Auslegung:** Bei 5 V Betriebsspannung, einer typischen LED-Vorwaertsspannung von ca. 2 V und 150 Ohm Vorwiderstand liegt der Strom rechnerisch im Bereich von etwa 20 mA. Das ist fuer viele Mikrocontroller-Pins bereits nahe am sinnvollen Grenzbereich. Fuer einen stabilen Dauerbetrieb ist daher eine sorgfaeltige Stromverteilung wichtig, insbesondere wenn mehrere Kanaele gleichzeitig geschaltet werden.

### Sensorik

Im Projektkontext werden folgende Sensorklassen betrachtet:

- Helligkeitssensoren,
- PIR-Bewegungssensoren,
- Temperatursensoren,
- Tuerkontakte.

Die Sensorik stellt die Datengrundlage fuer Automationen dar. Ohne konsistente, wiederholbar erfasste Eingangswerte ist eine reproduzierbare Steuerlogik nicht moeglich.

### Zusaetzliches Material und Modellhausbezug

- Dupont-Crimp-Set inklusive Crimpzange
- Leitungen mit 0,5 mm2 Querschnitt
- PLA-Filament fuer den Modellhausaufbau (hellgrau und dunkelgrau)

Der Aufbau im Modellhaus hat einen didaktischen Vorteil: Leitungsfuehrung, Kanalzuordnung und Schaltverhalten werden sichtbar. Dadurch kann die technische Funktion nicht nur softwareseitig, sondern auch mechanisch und elektrisch nachvollzogen werden.

## Verwendete Frameworks und Protokolle

### Home Assistant

Home Assistant dient als zentrale Integrations- und Bedienplattform. Hier laufen Entitaeten, Automationen und Dashboards zusammen. Damit entsteht ein einheitlicher Blick auf den Systemzustand. [@ha_installation] [@ha_automation]

Im Projekt ist Home Assistant besonders wichtig fuer:

- die Darstellung von Ist-Zustaenden,
- die Ausloesung manueller Schaltvorgaenge,
- die Definition regelbasierter Automationen.

### Node-RED

Node-RED wird als visuelle Verarbeitungsschicht eingesetzt. Datenfluesse koennen ueber Nodes modelliert, angepasst und nachvollzogen werden. Das erleichtert Iterationen waehrend der Entwicklung deutlich, da Logikbausteine ohne kompletten Neuaufbau des Systems angepasst werden koennen. [@nodered_homepage]

Wesentliche Rolle von Node-RED im Projekt:

- Bruecke zwischen serieller Kommunikation und MQTT,
- Validierung und Transformation von Payloads,
- geordnete Weitergabe von Befehlen und Statusmeldungen.

### MQTT

MQTT wird als leichtgewichtiges Publish/Subscribe-Protokoll fuer den Nachrichtenaustausch zwischen Diensten eingesetzt. Der Einsatz ist vor allem bei verteilten Komponenten sinnvoll, weil Sender und Empfaenger nicht direkt gekoppelt sein muessen. [@oasis_mqtt_v5_2019] [@agyemang_mqtt_2022] [@ha_mqtt_integration]

Typische Vorteile im vorliegenden Kontext:

- geringe Protokolloverheads,
- einfache Skalierung auf weitere Topics und Entitaeten,
- klare Trennung von Kommando- und Statuskanaelen.

### Portainer

Portainer dient als Weboberflaeche zur Verwaltung der Docker-Container. Das ist besonders hilfreich, wenn mehrere Dienste parallel betrieben und bei Bedarf einzeln neu gestartet, aktualisiert oder ueberwacht werden muessen. [@portainer_docs]

### Firmata

Firmata ist ein standardisiertes Protokoll, mit dem ein Host-System (hier Raspberry Pi bzw. Node-RED) einen Mikrocontroller (Arduino Uno) ueber die serielle Schnittstelle ansteuern kann. [@arduino_firmata_docs] [@firmata_arduino_github]

Der praktische Nutzen liegt darin, dass keine vollstaendig eigene serielle Protokolldefinition implementiert werden muss. Stattdessen wird ein etablierter Standard genutzt.

## Systemarchitektur

## Smart-Home-Umsetzung mit Home Assistant und Node-RED

**Schueler:** Janik Gierer

### Architektur in drei Ebenen

Das System kann in drei logisch getrennte Ebenen aufgeteilt werden:

1. **Feldebene (Arduino):** Direkte Anbindung von Sensorik und Aktorik.
2. **Verarbeitungsebene (Node-RED + MQTT):** Datenfluss, Protokollbruecke und Logikaufbereitung.
3. **Managementebene (Home Assistant):** Visualisierung, Automationen und Bedienung.

Diese Trennung erhoeht die Wartbarkeit, weil Aenderungen auf einer Ebene nicht automatisch alle anderen Ebenen brechen.

### Kommunikationspfad

Im aktuellen Aufbau laeuft die Kommunikation entlang eines klaren Pfades:

Sensor/Aktor <-> Arduino (I/O) <-> serielle Verbindung (Firmata) <-> Node-RED <-> MQTT-Broker <-> Home Assistant.

Damit ist fachlich sauber getrennt:

- **I/O-nahe Steuerung** auf Mikrocontroller-Ebene,
- **Nachrichtentransport und Aufbereitung** auf Middleware-Ebene,
- **Benutzerinteraktion und Regelwerk** auf Plattform-Ebene.

Technisch wichtig: In dieser Architektur ist MQTT nicht der direkte Transportweg vom Arduino Uno zu Home Assistant. Der Arduino ist primaer seriell via Firmata angebunden; MQTT wird zwischen den Diensten auf dem Raspberry Pi genutzt. [@firmata_arduino_github] [@ha_mqtt_integration]

## Theoretische Grundlagen

### Begriff Smart Home

Ein Smart Home ist ein vernetztes System, in dem Sensorik, Aktorik und Steuerlogik zusammenwirken. Eingehende Daten werden ausgewertet und fuehren je nach Regelwerk zu Aktionen. Die Interaktion kann automatisch oder manuell ueber eine Benutzeroberflaeche erfolgen. [@abutair_secure_privacy_smart_home_2020]

Fuer diese Arbeit bedeutet das konkret:

- Sensoren liefern Ereignisse bzw. Messwerte,
- die Logik entscheidet ueber Aktionen,
- Aktoren setzen diese Aktionen sichtbar um,
- die Plattform stellt alles nachvollziehbar dar.

### Sensorik

Sensorik umfasst die strukturierte Erfassung physischer Zustaende. Im Modellhaus sind das insbesondere Helligkeit, Bewegung, Temperatur und Tuerstatus. Jeder Sensortyp liefert dabei eine andere Datencharakteristik:

- diskrete Ereignisse (z. B. Bewegung erkannt),
- quasi-binaere Zustaende (z. B. Tuer offen/geschlossen),
- kontinuierliche Werte (z. B. Temperatur).

Diese Unterschiede sind fuer die Auswertung relevant, da Triggerlogik und Entprellung je nach Signaltyp unterschiedlich gestaltet werden muessen.

### Aktorik

Aktorik setzt digitale Steuerentscheidungen in physische Wirkung um. Im Projekt sind dies primaer Lichtkanaele (LEDs). Auch wenn die Lasten im Modell klein sind, gelten dieselben Grundprinzipien wie in groesseren Anlagen:

- sichere elektrische Auslegung,
- klare Kanalzuordnung,
- reproduzierbares Schaltverhalten.

Fuer hoehere Lasten waeren Treiberstufen oder Relais zwingend erforderlich, um Mikrocontroller-Ausgaenge zu entlasten.

### Steuerung

Steuerung verbindet Sensorik und Aktorik ueber ein Regelwerk. Ein typisches Muster ist:

1. Eingangssignal trifft ein.
2. Bedingungen werden geprueft.
3. Aktion wird ausgefuehrt.
4. Zustand wird rueckgemeldet.

Je klarer dieses Muster in Topics, Flows und Automationen abgebildet ist, desto besser sind Fehlersuche und Erweiterung moeglich.

## Arduino Uno mit StandardFirmata

### Rolle des Arduino im Gesamtsystem

Der Arduino Uno dient als direkte I/O-Schnittstelle zur physikalischen Ebene. Er ist dort sinnvoll, wo Signale in Echtzeit eingelesen oder Ausgaenge unmittelbar gesetzt werden muessen.

### Einsatz von StandardFirmata

Im Projekt wird StandardFirmata verwendet. Dadurch kann der Arduino vom Host aus gesteuert werden, ohne dass fuer jede Aenderung ein separates, proprietaeres Applikationsprotokoll aufgesetzt werden muss. [@arduino_firmata_docs] [@firmata_arduino_github]

In der Arduino IDE ist der Sketch verfuegbar unter:
`File -> Examples -> Firmata -> StandardFirmata`

Wesentliche Bestandteile:

- `#include <Firmata.h>` fuer die Protokollfunktionen,
- `Firmata.begin(57600);` fuer die serielle Initialisierung,
- `Firmata.attach(...)` fuer die Zuordnung eingehender Nachrichten zu Callbacks,
- zyklische Verarbeitung in `loop()` mit `Firmata.available()` und `Firmata.processInput()`.

Dieses Vorgehen ist fuer ein Lern- und Demonstrationsprojekt sinnvoll, weil es robuste Grundfunktionalitaet bereitstellt und den Fokus auf Systemintegration statt auf Low-Level-Protokolldesign legt.

## Datenuebertragung und Kommunikationsdesign

### MQTT als Nachrichtenrueckgrat

MQTT arbeitet mit einem Broker als zentralem Verteiler. Clients publizieren Nachrichten auf Topics oder abonnieren Topics. Der Broker entkoppelt damit Sender und Empfaenger. [@oasis_mqtt_v5_2019]

Typischer Nutzen in dieser Arbeit:

- Sensorwerte koennen mehreren Verbrauchern bereitgestellt werden.
- Schaltbefehle und Rueckmeldungen bleiben sauber getrennt.
- Der Datenfluss ist durch Topic-Namen transparent.

### Topic-Struktur

Eine hierarchische Benennung erleichtert Wartung und Skalierung. Beispielhafte Struktur:

- `haus/sensor/temperatur`
- `haus/sensor/helligkeit`
- `haus/licht/wohnzimmer/set`
- `haus/licht/wohnzimmer/state`

Damit ist aus dem Topic bereits erkennbar, ob es sich um Messdaten, Schaltkommandos oder Statusmeldungen handelt.

### Command- und State-Trennung

Die Trennung von Soll- und Ist-Kanaelen verhindert Mehrdeutigkeiten:

- `.../set` repraesentiert den angeforderten Zielzustand.
- `.../state` repraesentiert den tatsaechlichen Rueckmeldezustand.

Diese Trennung ist vor allem bei Dashboards und Automationen wichtig, um keine falschen Annahmen ueber den realen Aktorzustand zu treffen.

### QoS, Retain und LWT

Die Auswahl passender MQTT-Mechanismen verbessert Robustheit:

- **QoS 0:** geeignet fuer haeufige, unkritische Telemetrie.
- **QoS 1:** geeignet fuer wichtigere Schaltmeldungen.
- **Retained Messages:** stellen den letzten bekannten Zustand fuer neue Subscriber bereit.
- **Last Will and Testament (LWT):** signalisiert, wenn ein Client unerwartet offline geht.

Im Zusammenspiel mit Home Assistant erhoeht das die Nachvollziehbarkeit bei Verbindungsunterbrechungen und Neustarts. [@ha_mqtt_integration]

## Node-RED als Logik- und Integrationsschicht

Node-RED ist in dieser Arbeit mehr als ein Visualisierungstool fuer Datenfluesse. Es uebernimmt die technische Mittlerrolle zwischen serieller Hardwareanbindung und MQTT-basierter Plattformintegration. [@nodered_homepage]

Ein typischer Flow besteht aus:

1. Eingang ueber MQTT-In oder Serial-In.
2. Validierung und Transformation in Function-Nodes.
3. Weitergabe ueber MQTT-Out oder Serial-Out.

Dieses Muster ist wiederverwendbar und bildet eine gute Grundlage fuer zusaetzliche Kanale oder Raeume.

### Vorteile fuer die Projektarbeit

- Schnelle Anpassung ohne komplettes Re-Deployment.
- Transparente Darstellung der Datenpfade.
- Leichte Erweiterung um Filter- und Plausibilitaetslogik.

### Serieller Zugriff unter Linux

Arduino-Geraete erscheinen typischerweise als `/dev/ttyACM0` oder `/dev/ttyUSB0`. Fuer stabilen Betrieb muessen drei Punkte sichergestellt sein:

- exklusiver Portzugriff,
- korrekte Device-Rechte,
- konsistente Portzuordnung nach Neustarts.

Diese Punkte sind haeufige Fehlerquellen in gemischten Hardware-/Software-Setups. [@nodered_raspberrypi]

## Home Assistant als zentrale Steuereinheit

Home Assistant bildet die Bedien- und Automationsoberflaeche des Systems. Entitaeten, Trigger und Dashboards werden dort zusammengefuehrt. [@ha_installation] [@ha_automation]

### MQTT-Integration

Die Einbindung kann manuell oder ueber MQTT Discovery erfolgen. Discovery reduziert Konfigurationsaufwand, da Entitaeten aus gueltigen Discovery-Nachrichten erzeugt werden koennen. [@ha_mqtt_sensor]

### Automationen

Automationen folgen dem Schema Trigger -> Bedingungen -> Aktionen. Ein fuer das Modellhaus typisches Muster ist:

- Trigger: Bewegung erkannt und Helligkeit unter Schwellwert,
- Bedingung: Automatikmodus aktiv,
- Aktion: Licht einschalten und nach definierter Zeit ausschalten.

Das Muster ist bewusst einfach, aber praezise genug, um die Trennung zwischen Sensordatenerfassung und Aktorreaktion klar zu halten.

### Dashboards und Visualisierung

Die Visualisierung erfolgt ueber Dashboard-Karten wie Entities-, Button- und Verlaufskarten. Damit sind Schaltzustaende, Messwerttrends und manuelle Eingriffe auf einer Oberflaeche verfuegbar. [@ha_dashboards_intro] [@ha_cards]

## Praktische Umsetzung

### Hardwareaufbau

#### Stromversorgung und Verkabelung

Der Raspberry Pi wird mit 5 V betrieben, der Arduino ist ueber USB angebunden. LED-Kreise sind ueber Vorwiderstaende abgesichert. Fuer den Aufbau wurden gecrimpte und steckbare Verbindungen genutzt, um Anpassungen ohne Loetarbeiten zu ermoeglichen.

#### Einbau von LEDs, Relais und Sensoren

Die Aktoren wurden den Raeumen des Modellhauses zugeordnet. Sensoren wurden so positioniert, dass typische Nutzsituationen abgebildet werden koennen (z. B. Bewegung im Eingangsbereich, Helligkeitsmessung in raumtypischer Lage). Relais bzw. Treiberstufen werden dort vorgesehen, wo Lasttrennung erforderlich ist.

### Arduino-Integration

Durch StandardFirmata liest der Host Eingangs- und Sensordaten aus und setzt Ausgaenge fuer Aktoren. Schaltbefehle werden deterministisch pro eingehender Nachricht verarbeitet. [@arduino_firmata_docs] [@firmata_arduino_github]

### Node-RED-Workflows

Die im Projekt verwendete Logik kann wie folgt zusammengefasst werden:

- MQTT-In-Nodes abonnieren Sollwerte und Triggerinformationen,
- Function-Nodes validieren Daten und bereiten Kommandos auf,
- Serial-Out-Nodes uebertragen Befehle an den Arduino,
- MQTT-Out-Nodes melden Ist-Zustaende zurueck.

Durch diese Kette bleibt die Steuerlogik nachvollziehbar und modular.

### Erstinbetriebnahme am Raspberry Pi

Fuer einen reproduzierbaren Erstaufbau hat sich ein klarer Ablauf bewahrt:

1. System aktualisieren: `sudo apt update && sudo apt upgrade -y`
2. Docker installieren und Benutzer zur Docker-Gruppe hinzufuegen. [@docker_compose_overview]
3. Projektverzeichnis samt Volume-Struktur anlegen.
4. `compose.yaml` fuer Home Assistant, MQTT und Portainer erstellen. [@docker_compose_file_reference]
5. Dienste starten: `docker compose up -d`
6. Laufzeitstatus pruÌˆfen: `docker ps`, Logs mit `docker logs <container>`
7. Home Assistant Onboarding abschliessen und MQTT integrieren. [@ha_mqtt_integration]
8. Portainer initial konfigurieren. [@portainer_docs]

Der Vorteil dieser festen Reihenfolge ist, dass Fehlerquellen frueh sichtbar werden und nicht erst spaeter bei der Automationslogik auftreten.

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

## Bedienung und Steuerung

Die taegliche Bedienung erfolgt ueber Home-Assistant-Dashboards. Node-RED arbeitet parallel als Logik- und Integrationsschicht. Dadurch wird die Benutzeroberflaeche von der eigentlichen Nachrichtenverarbeitung entkoppelt. [@ha_dashboards_intro] [@nodered_homepage]

### Steuerung ueber Endgeraete

Der Zugriff ist ueber Browser auf PC, Tablet und Smartphone moeglich. Schaltbefehle werden in der Regel per Button ausgeloest, Zustandsaenderungen erscheinen als direkte Rueckmeldung in den Karten.

### Bedeutung der Rueckmeldelogik

Besonders wichtig fuer die Alltagstauglichkeit ist die Rueckmeldelogik:

- Schaltkommandos allein reichen nicht aus,
- erst die Rueckmeldung ueber State-Topics macht den realen Zustand transparent,
- Automationen koennen so auf echte Zustandsaenderungen reagieren.

Diese Trennung reduziert Fehlinterpretationen in der Bedienoberflaeche.

## Test und Validierung im bisherigen Projektstand

Die bisherige Validierung orientiert sich an den definierten Use-Cases und den vorhandenen Komponenten. Dabei wurde der Fokus auf funktionale Korrektheit und Kommunikationsstabilitaet gelegt.

Typischer Ablauf:

1. Ereignis erzeugen (z. B. Dunkelheit, Bewegung oder Temperaturaenderung).
2. Trigger- und Bedingungslogik beobachten.
3. Aktorreaktion am Modellhaus und im Dashboard vergleichen.
4. Rueckmeldung ueber Topics und Statuskarten kontrollieren.

Der bisher dokumentierte Projektbetrieb zeigt, dass Lichtsteuerung und zustandsabhaengige Schaltablaeufe reproduzierbar ausgeloest werden koennen. Verbindungsunterbrechungen wurden als Fehlerfall betrachtet und in der Logik beruecksichtigt.

## Fehleranalyse und Optimierungen

### Serielle Kommunikation

Typische Problemquellen:

- Port ist bereits durch einen anderen Prozess belegt,
- Device-Bezeichnung aendert sich nach Neustart,
- fehlende Rechte auf `/dev/tty...`.

Bewaehrte Massnahmen:

- festen Port in Node-RED konfigurieren,
- konkurrierende Prozesse beenden,
- Dienst nach Aenderungen sauber neu starten.

Diese Massnahmen verbessern die Stabilitaet der Host-zu-Arduino-Kommunikation deutlich.

### MQTT-Stabilitaet

Bei MQTT-Verbindungen sind vor allem Reconnect-Verhalten und Zustandskonsistenz entscheidend. Durch geeignete Kombination aus QoS, Retained Messages und LWT kann das System robuster auf Netzunterbrechungen reagieren. [@oasis_mqtt_v5_2019] [@ha_mqtt_integration]

Wichtige Beobachtung fuer den Betrieb:

- Offline-Zustaende sollen sichtbar werden,
- nach Wiederverbindung soll ein konsistenter Ausgangszustand hergestellt werden,
- Dashboards duerfen dabei keine veralteten Zustandsbilder dauerhaft anzeigen.

## Uebertragbarkeit auf reale Wohnhaus-Szenarien

Die im Modellhaus umgesetzte Architektur ist grundsaetzlich auf reale Umgebungen uebertragbar, wenn elektrische Auslegung, Sicherheitsanforderungen und Lasttrennung entsprechend angepasst werden. Der wesentliche Mehrwert des Modellansatzes liegt darin, dass die Struktur bereits jetzt klar definiert ist:

- getrennte Ebenen fuer I/O, Verarbeitung und Bedienung,
- standardisierte Schnittstellen zwischen den Ebenen,
- zentrale Sicht auf den Gesamtzustand.

Damit ist eine gute Grundlage fuer spaetere Skalierung geschaffen, ohne die Grundarchitektur neu entwerfen zu muessen.

## Zusammenfassende Bewertung des Teilprojekts

Aus technischer Sicht zeigt der bisherige Stand, dass der gewaehlte Stack fuer ein modulares Smart-Home-Modell geeignet ist:

- Home Assistant als zentrale Plattform,
- Node-RED als flexible Integrationslogik,
- MQTT als entkoppeltes Transportprotokoll,
- Docker fuer reproduzierbaren Dienstbetrieb,
- Arduino/Firmata fuer den direkten Hardwarezugriff.

Der zentrale Vorteil dieser Kombination liegt in der klaren Rollenverteilung. Jede Komponente hat eine nachvollziehbare Aufgabe, wodurch Entwicklung, Fehlersuche und Erweiterung strukturiert moeglich sind.

## Ausblick

Die bestehende Architektur ist fuer Erweiterungen vorbereitet.

### Sprachsteuerung

Eine moegliche Erweiterung ist die Einbindung von Sprachsteuerung, z. B. ueber Home-Assistant-Voice oder Alexa-Integration. [@ha_voice_control] [@ha_alexa_smart_home]

### Skalierung auf mehrere Raeume

Die bestehende Topic- und Entitaetsstruktur kann auf weitere Raeume erweitert werden, etwa:

- `haus/licht/kueche/set`
- `haus/licht/schlafzimmer/set`
- `haus/sensor/flur/bewegung`

Wichtig ist dabei, die bisherige Namenskonvention konsistent beizubehalten.

### Einbindung weiterer Sensorik

Zusaetzliche Sensoren (z. B. CO2, Luftqualitaet, Feuchtigkeit) koennen als weitere Entitaeten in Home Assistant und als weitere Datenkanaele in Node-RED integriert werden. [@ha_dev_sensor_entity]

### Methodischer Ausblick

Fuer die weitere Arbeit ist es sinnvoll, bei jeder Erweiterung denselben Ablauf beizubehalten:

1. fachliche Anforderung beschreiben,
2. Datenfluss definieren,
3. Topic- und Entitaetsmodell festlegen,
4. Visualisierung und Testfall dokumentieren.

So bleibt das System auch bei wachsendem Umfang technisch konsistent und dokumentierbar.


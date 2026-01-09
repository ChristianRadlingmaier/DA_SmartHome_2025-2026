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

---

## Verwendete Aktoren

- 100 Stück Widerstände (1/4 W, 5 % Toleranz, 150 Ohm)
- 3 mm Leuchtdioden (LEDs)

---

## Zusätzlich benötigtes Material

- IWILCS Dupont Crimp Set (790-teilig inkl. Crimpzange)
- Kabel mit 0,5 mm² Querschnitt
- 4× PLA Basic Hellgrau (10104)
- 2× PLA Basic Dunkelgrau (10105)

---

## Verwendete Frameworks

- **Home Assistant**Dient als zentrales Steuerelement des Modellhauses. Es wird praxisnah simuliert, wie von einem zentralen Standort aus sämtliche Geräte gesteuert und überwacht werden können. [@ha_installation; @aavild_distributed_homeassistant_2024]
- **Node-RED**Ermöglicht die einfache Erstellung und Automatisierung von Logiken. Sensordaten wie Temperatur oder Helligkeit können verarbeitet und entsprechende Aktoren angesteuert werden. [@nodered_homepage]
- **MQTT**Wird als Kommunikationsprotokoll zwischen Mikrocontroller (Arduino Uno), Raspberry Pi und Home Assistant verwendet. Es ermöglicht eine zuverlässige und schnelle Datenübertragung. [@oasis_mqtt_v5_2019; @agyemang_mqtt_2022; @ha_mqtt_integration]
- **Portainer**Dient zur übersichtlichen Verwaltung aller laufenden Docker-Container über ein Webinterface. [@portainer_docs]
- **Firmata**
  Firmata ist ein Kommunikationsprotokoll, mit dem ein Computer (in diesem Fall der Raspberry Pi) einen Mikrocontroller (Arduino Uno) direkt steuern kann. Auf dem Mikrocontroller läuft dabei das *StandardFirmata*-Sketch, welches das Setzen von Pins sowie das Lesen von Eingängen ermöglicht. [@arduino_firmata_docs; @firmata_arduino_github]

---

# Teilaufgabe – Smart-Home-Umsetzung mit Home Assistant und Node-RED

**Schüler:** Janik Gierer

---

## 1. Theoretische Grundlagen

Ein Smart Home beschreibt ein vernetztes Haus, bei dem Geräte und Komponenten zentral gesteuert und Zustände ausgelesen werden können. Die Steuerung erfolgt entweder automatisch oder durch Benutzereingaben. [@abutair_secure_privacy_smart_home_2020]
Beispiele hierfür sind das Ein- und Ausschalten von Licht oder Heizung über ein Smartphone oder das automatische Herunterfahren von Rollläden zu bestimmten Uhrzeiten. [@abutair_secure_privacy_smart_home_2020]

Im Rahmen dieser Diplomarbeit kommen ein Arduino Uno als Mikrocontroller, ein Raspberry Pi als Steuerzentrale sowie Home Assistant als Automatisierungsplattform zum Einsatz. [@ha_installation]
Die Kommunikation zwischen Sensoren und Aktoren erfolgt über MQTT. [@oasis_mqtt_v5_2019; @ha_mqtt_integration]

---

### 1.1 Sensorik, Aktorik und Steuerung im Modellhaus

Sensorik, Aktorik und Steuerung bilden die grundlegenden Bestandteile eines Smart Homes. Erst durch ihr Zusammenspiel wird ein automatisiertes System möglich. [@abutair_secure_privacy_smart_home_2020]

**Sensorik**
Sensoren erfassen Zustände und Umweltparameter wie Temperatur, Helligkeit, Bewegung oder Luftfeuchtigkeit. Diese Messwerte werden an den Mikrocontroller weitergeleitet. [@abutair_secure_privacy_smart_home_2020]

**Aktorik**
Aktoren reagieren auf Steuerbefehle oder geänderte Messwerte. Digitale Signale werden in physische Aktionen umgesetzt, beispielsweise durch LEDs, Relais oder Motoren. [@abutair_secure_privacy_smart_home_2020]

**Steuerung**
Die Steuerung verarbeitet Sensordaten und entscheidet, welche Aktoren angesteuert werden. Die Logik befindet sich in einer übergeordneten Software, während der Mikrocontroller die Befehle ausführt. [@abutair_secure_privacy_smart_home_2020]

---

#### 1.1.1 Sensoren zur Messung von Umweltparametern

Kurzbeschreibung der verwendeten Sensoren (z. B. Temperatur-, Helligkeitssensoren) sowie deren Aufgabe im Smart-Home-System. [@abutair_secure_privacy_smart_home_2020]

#### 1.1.2 Aktoren zur Steuerung von Licht und Geräten

Relais, LEDs und Mini-Lampen – Einsatzmöglichkeiten und Grenzen. [@abutair_secure_privacy_smart_home_2020]

#### 1.1.3 Mikrocontroller (Arduino) als Basis für smarte Funktionen

Auf dem Arduino wird das Beispiel *StandardFirmata* installiert. Dieses Sketch stellt die Firmata-Funktionen bereit und ermöglicht die Steuerung des Arduino über die serielle Schnittstelle durch einen Host (Raspberry Pi). [@arduino_firmata_docs; @firmata_arduino_github]

*(Hinweis: In der Arduino IDE findet man es typischerweise unter **File → Examples → Firmata → StandardFirmata**.)* [@arduino_firmata_docs]

##### Einbindung der Firmata-Bibliothek

`#include <Firmata.h>`
Ermöglicht, dass der Arduino vom Host aus gesteuert werden kann (Pins setzen, lesen). [@arduino_firmata_docs]

##### Start der seriellen Kommunikation

`Firmata.begin(57600);`
Öffnet die serielle Schnittstelle mit 57600 Baud – notwendig, damit der Host über USB mit dem Arduino kommunizieren kann. [@firmata_arduino_github]

##### Registrierung der Callbacks (Herzstück der Steuerung)

`Firmata.attach(ANALOG_MESSAGE, analogWriteCallback);`
`Firmata.attach(DIGITAL_MESSAGE, digitalWriteCallback);`
`Firmata.attach(SET_PIN_MODE, setPinModeCallback);`
`Firmata.attach(START_SYSEX, sysexCallback);`
`Firmata.attach(SYSTEM_RESET, systemResetCallback);`

Diese Callbacks sorgen dafür, dass eingehende Nachrichten (z. B. „digital write“, „set pin mode“, Sysex) korrekt verarbeitet werden. [@firmata_arduino_github]

##### Setzen des Pin-Modus

`void setPinModeCallback(byte pin, int mode)`
Ein *Pin-Conflict* entsteht typischerweise, wenn in der Steuerlogik (z. B. Node-RED) mehrere Nodes denselben Pin parallel konfigurieren oder schalten. Daher sollte pro Pin genau **eine** „Schaltstelle“ (ein Flow/Node) zuständig sein. [@firmata_arduino_github]

##### Digitales Schreiben (LED ein / aus)

`void digitalWriteCallback(byte port, int value)`
Wird ausgelöst, wenn der Host einen digitalen Befehl sendet (z. B. ON / OFF). [@firmata_arduino_github]

##### Haupt-Loop (Dauerbetrieb)

`void loop()`
`{`
`  checkDigitalInputs();`
`  while (Firmata.available())`
`    Firmata.processInput();`
`}`

Dauerhafte Aufgaben: prüft Eingangszustände und verarbeitet sofort eingehende Befehle vom Host. Eine eigene Logik am Arduino ist dabei nicht zwingend nötig, da die „Intelligenz“ am Host liegt. [@firmata_arduino_github]

---

### 1.2 Datenübertragung und Kommunikation im Smart Home

#### 1.2.1 MQTT als zentrales Protokoll zwischen Arduino und Home Assistant

Topic-Struktur, Payload-Formate und Zuverlässigkeit. [@oasis_mqtt_v5_2019; @ha_mqtt_integration]

#### 1.2.2 Node-RED zur Verarbeitung und Weiterleitung von Nachrichten

Visuelle Programmierung zur Automatisierung von Abläufen. [@nodered_homepage]

#### 1.2.3 Serieller Zugriff auf den Arduino vom Raspberry Pi

Verbindung über `/dev/ttyUSB0` zur Übertragung von Steuerkommandos.

---

### 1.3 Home Assistant als zentrale Steuereinheit

#### 1.3.1 Integration von MQTT-Geräten in Home Assistant

Manuelle Konfiguration im Vergleich zur MQTT-Integration. [@ha_mqtt_integration; @ha_mqtt_sensor]

#### 1.3.2 Automationen in Home Assistant

Beispielsweise Lichtsteuerung bei Bewegung oder Temperaturregelung. [@ha_automation]

---

### 1.4 Visualisierung und Benutzeroberfläche

#### 1.4.1 Lovelace UI zur Darstellung von Geräten und Zuständen

Dashboards für Licht, Heizung und Sensorwerte. [@ha_dashboards_intro; @ha_cards]

#### 1.4.2 Visualisierung von Zustandsänderungen

Darstellung von Lampenstatus, Temperaturverläufen und Türkontakten. [@ha_cards]

---

## 2. Praktische Umsetzung

### 2.1 Aufbau des Modellhauses

#### 2.1.1 Stromversorgung und Verkabelung

Mini-USB, Breadboards und Steckverbindungen.

#### 2.1.2 Einbau von LEDs, Relais und Temperatursensoren

Platzierung und Verkabelung im Modellhaus.

---

### 2.2 Arduino-Programmierung

#### 2.2.1 Einlesen und Senden von Sensorwerten

Übertragung von Messwerten über Serial oder MQTT. [@oasis_mqtt_v5_2019]

#### 2.2.2 Empfang und Ausführung von Steuerkommandos

Lichtsteuerung über serielle Befehle. [@arduino_firmata_docs; @firmata_arduino_github]

---

### 2.3 Node-RED Workflows zur Kommunikation

#### 2.3.1 MQTT-IN zur Verarbeitung von Home-Assistant-Kommandos

Beispiel: `haus/licht/wohnzimmer -> Serial`. [@nodered_homepage; @oasis_mqtt_v5_2019]

#### 2.3.2 Serial-Out an den Arduino

Steuerung der LEDs über den USB-Port. [@nodered_homepage]

---

### 2.4 Docker-basierter Betrieb

#### 2.4.1 Container für Home Assistant, Node-RED, MQTT und Portainer

Verwaltung über `docker-compose` am Raspberry Pi. [@docker_compose_overview; @docker_compose_file_reference; @portainer_docs]

Es wird eine `docker-compose.yaml` Datei erstellt, die sich in einem eigenen Unterverzeichnis befindet, um Übersicht und Kapselung zu gewährleisten. [@docker_compose_overview]

**Vorgehensweise:**

1. Wechsel in das gewünschte Unterverzeichnis
2. Erstellen der Datei `docker-compose.yaml`
3. Einfügen des Codes
4. Speichern der Datei
5. Setzen der erforderlichen Berechtigungen

---

### 2.5 Bedienung und Steuerung

#### 2.5.1 Steuerung über Smartphone, Tablet und PC

Zugriff auf die Home-Assistant-Oberfläche im Browser. [@ha_dashboards_intro]

#### 2.5.2 Test der Licht- und Heizungssteuerung

---

### 2.6 Fehleranalyse und Optimierungen

#### 2.6.1 Serielle Fehler und Verbindungsprobleme

Behandlung von *Permission denied* und Portkonflikten.

#### 2.6.2 MQTT-Verbindungsabbrüche und Topics

Vermeidung durch QoS und Last Will and Testament (LWT). [@oasis_mqtt_v5_2019]

---

## 2.7 Ausblick

### 2.7.1 Erweiterung mit Sprachsteuerung (z. B. Alexa)

Home Assistant bietet eine Möglichkeit zur Integration von Sprachsteuerung (z. B. über Alexa/Voice Assistants). Dadurch können bestehende Geräte per Sprachbefehl gesteuert werden. [@ha_voice_control; @ha_alexa_smart_home]

### 2.7.2 Erweiterung auf mehrere Räume oder Wohnungen

Falls zusätzliche Räume gebaut werden oder weitere Bereiche automatisiert werden sollen, kann die bestehende Implementierung der bereits vorhandenen Geräte übernommen und erweitert werden. Durch den modularen Aufbau des Systems lassen sich neue Räume einfach in die bestehende Struktur integrieren, ohne grundlegende Änderungen an der Architektur vornehmen zu müssen.
Sensoren und Aktoren können nach dem gleichen Prinzip wie in den bereits umgesetzten Räumen angebunden werden. Die Steuerungslogik sowie die Kommunikationsstruktur bleiben dabei unverändert und werden lediglich um zusätzliche Geräte und Topics ergänzt. Dadurch ist es möglich, sowohl einzelne zusätzliche Räume als auch komplette Wohnungen in das Smart-Home-System einzubinden.

### 2.7.3 Einbindung weiterer Sensoren (CO$_2$, Luftqualität, Helligkeit)

Das bestehende System kann durch zusätzliche Sensoren wie CO$_2$-, Luftqualitäts- oder Helligkeitssensoren erweitert werden. Diese lassen sich nach dem gleichen Prinzip wie bereits vorhandene Sensoren integrieren und in die bestehende Automatisierungslogik einbinden. [@ha_dev_sensor_entity]

---

## Praktische Arbeit

Zu Beginn der Arbeit wurde untersucht, wie ein Arduino Uno ohne eigene Internetverbindung mit Home Assistant verbunden werden kann.
Dies wurde mithilfe des Programms *StandardFirmata* umgesetzt, welches auf den Arduino geladen wird. Anschließend kann der Mikrocontroller direkt vom Raspberry Pi aus gesteuert werden. [@arduino_firmata_docs; @firmata_arduino_github]

Die praxisnaheste Verwendung von Home Assistant erfolgt auf einem Raspberry Pi, auf dem Home Assistant in einem Docker-Container betrieben wird. [@ha_installation; @docker_what_is_container]

---

### Messergebnisse

*(noch ausständig)*

---

### Fehler

#### Berechtigungsprobleme

Diese treten sowohl bei der Erstellung der Docker-Container als auch während des laufenden Betriebs auf. [@docker_what_is_container]

#### Node-RED Fehler

- **Board-Fehler:** nicht reproduzierbar, behoben durch Neustart von Node-RED
- **Pin-Conflict-Error:** tritt auf, wenn mehrere Arduino-Out-Nodes denselben Pin ansprechen [@firmata_arduino_github]

---

### Fließtext

*(optional für Ergänzungen)*

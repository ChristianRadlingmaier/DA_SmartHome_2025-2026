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
Der Fokus liegt auf der Einrichtung von Docker auf dem Raspberry Pi sowie auf der Kommunikation zwischen Raspberry Pi, Arduino Uno und den angeschlossenen Aktoren und Sensoren.

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

- **Home Assistant**  
  Dient als zentrales Steuerelement des Modellhauses. Es wird praxisnah simuliert, wie von einem zentralen Standort aus sämtliche Geräte gesteuert und überwacht werden können.

- **Node-RED**  
  Ermöglicht die einfache Erstellung und Automatisierung von Logiken. Sensordaten wie Temperatur oder Helligkeit können verarbeitet und entsprechende Aktoren angesteuert werden.

- **MQTT**  
  Wird als Kommunikationsprotokoll zwischen Mikrocontroller (Arduino Uno), Raspberry Pi und Home Assistant verwendet. Es ermöglicht eine zuverlässige und schnelle Datenübertragung.

- **Portainer**  
  Dient zur übersichtlichen Verwaltung aller laufenden Docker-Container über ein Webinterface.

- **Firmata**  
  Firmata ist ein Kommunikationsprotokoll, mit dem ein Computer (in diesem Fall der Raspberry Pi) einen Mikrocontroller (Arduino Uno) direkt steuern kann. Auf dem Mikrocontroller läuft dabei das *StandardFirmata*-Sketch, welches das Setzen von Pins sowie das Lesen von Eingängen ermöglicht.

---

# Teilaufgabe – Smart-Home-Umsetzung mit Home Assistant und Node-RED

**Schüler:** Janik Gierer

---

## 1. Theoretische Grundlagen

Ein Smart Home beschreibt ein vernetztes Haus, bei dem alltägliche Komponenten zentral gesteuert und ausgelesen werden können. Die Steuerung erfolgt entweder automatisch oder durch Benutzereingaben.  
Beispiele hierfür sind das Ein- und Ausschalten von Licht oder Heizung über ein Smartphone oder das automatische Herunterfahren von Rollläden zu bestimmten Uhrzeiten.

Im Rahmen dieser Diplomarbeit kommen ein Arduino Uno als Mikrocontroller, ein Raspberry Pi als Steuerzentrale sowie Home Assistant als Automatisierungsplattform zum Einsatz. Die Kommunikation zwischen Sensoren und Aktoren erfolgt über MQTT.

---

### 1.1 Sensorik, Aktorik und Steuerung im Modellhaus

Sensorik, Aktorik und Steuerung bilden die grundlegenden Bestandteile eines Smart Homes. Erst durch ihr Zusammenspiel wird ein automatisiertes System möglich.

**Sensorik**  
Sensoren erfassen Zustände und Umweltparameter wie Temperatur, Helligkeit, Bewegung oder Luftfeuchtigkeit. Diese Messwerte werden an den Mikrocontroller weitergeleitet.

**Aktorik**  
Aktoren reagieren auf Steuerbefehle oder geänderte Messwerte. Digitale Signale werden in physische Aktionen umgesetzt, beispielsweise durch LEDs, Relais oder Motoren.

**Steuerung**  
Die Steuerung verarbeitet Sensordaten und entscheidet, welche Aktoren angesteuert werden. Die Logik befindet sich in einer übergeordneten Software, während der Mikrocontroller die Befehle ausführt.

---

#### 1.1.1 Sensoren zur Messung von Umweltparametern
Temperatur, Helligkeit, Bewegung und deren Bedeutung im Smart Home

#### 1.1.2 Aktoren zur Steuerung von Licht und Geräten
Relais, LEDs und Mini-Lampen – Einsatzmöglichkeiten und Grenzen

#### 1.1.3 Mikrocontroller (Arduino) als Basis für smarte Funktionen
Programmierbare Steuerzentrale für Sensoren und Aktoren

---

### 1.2 Datenübertragung und Kommunikation im Smart Home

#### 1.2.1 MQTT als zentrales Protokoll zwischen Arduino und Home Assistant
Topic-Struktur, Payload-Formate und Zuverlässigkeit

#### 1.2.2 Node-RED zur Verarbeitung und Weiterleitung von Nachrichten
Visuelle Programmierung zur Automatisierung von Abläufen

#### 1.2.3 Serieller Zugriff auf den Arduino vom Raspberry Pi
Verbindung über `/dev/ttyUSB0` zur Übertragung von Steuerkommandos

---

### 1.3 Home Assistant als zentrale Steuereinheit

#### 1.3.1 Integration von MQTT-Geräten in Home Assistant
Manuelle Konfiguration im Vergleich zur Auto-Discovery

#### 1.3.2 Automationen in Home Assistant
Beispielsweise Lichtsteuerung bei Bewegung oder Temperaturregelung

---

### 1.4 Visualisierung und Benutzeroberfläche

#### 1.4.1 Lovelace UI zur Darstellung von Geräten und Zuständen
Dashboards für Licht, Heizung und Sensorwerte

#### 1.4.2 Visualisierung von Zustandsänderungen
Darstellung von Lampenstatus, Temperaturverläufen und Türkontakten

---

## 2. Praktische Umsetzung

### 2.1 Aufbau des Modellhauses

#### 2.1.1 Stromversorgung und Verkabelung
Mini-USB, Breadboards und Steckverbindungen

#### 2.1.2 Einbau von LEDs, Relais und Temperatursensoren
Platzierung und Verkabelung im Modellhaus

---

### 2.2 Arduino-Programmierung

#### 2.2.1 Einlesen und Senden von Sensorwerten
Übertragung von Messwerten über Serial oder MQTT

#### 2.2.2 Empfang und Ausführung von Steuerkommandos
Lichtsteuerung über serielle Befehle

---

### 2.3 Node-RED Workflows zur Kommunikation

#### 2.3.1 MQTT-IN zur Verarbeitung von Home-Assistant-Kommandos
Beispiel: `haus/licht/wohnzimmer -> Serial`

#### 2.3.2 Serial-Out an den Arduino
Steuerung der LEDs über den USB-Port

---

### 2.4 Docker-basierter Betrieb

#### 2.4.1 Container für Home Assistant, Node-RED, MQTT und Portainer
Verwaltung über `docker-compose` am Raspberry Pi

Es wird eine `docker-compose.yaml` Datei erstellt, die sich in einem eigenen Unterverzeichnis befindet, um Übersicht und Kapselung zu gewährleisten.

**Vorgehensweise:**
1. Wechsel in das gewünschte Unterverzeichnis  
2. Erstellen der Datei `docker-compose.yaml`  
3. Einfügen des Codes  
4. Speichern der Datei  
5. Setzen der erforderlichen Berechtigungen  

---

### 2.5 Bedienung und Steuerung

#### 2.5.1 Steuerung über Smartphone, Tablet und PC
Zugriff auf die Home-Assistant-Oberfläche im Browser

#### 2.5.2 Test der Licht- und Heizungssteuerung

---

### 2.6 Fehleranalyse und Optimierungen

#### 2.6.1 Serielle Fehler und Verbindungsprobleme
Behandlung von *Permission denied* und Portkonflikten

#### 2.6.2 MQTT-Verbindungsabbrüche und Topics
Vermeidung durch QoS und Last Will and Testament (LWT)

---

## 2.7 Ausblick

### 2.7.1 Erweiterung mit Sprachsteuerung (z. B. Alexa)
### 2.7.2 Erweiterung auf mehrere Räume oder Wohnungen
### 2.7.3 Einbindung weiterer Sensoren (CO₂, Luftqualität, Helligkeit)

---

## Praktische Arbeit

Zu Beginn der Arbeit wurde untersucht, wie ein Arduino Uno ohne eigene Internetverbindung mit Home Assistant verbunden werden kann.  
Dies wurde mithilfe des Programms *StandardFirmata* umgesetzt, welches auf den Arduino geladen wird. Anschließend kann der Mikrocontroller direkt vom Raspberry Pi aus gesteuert werden.

Die praxisnaheste Verwendung von Home Assistant erfolgt auf einem Raspberry Pi, auf dem Home Assistant in einem Docker-Container betrieben wird.

---

### Messergebnisse

*(noch ausständig)*

---

### Fehler

#### Berechtigungsprobleme
Diese treten sowohl bei der Erstellung der Docker-Container als auch während des laufenden Betriebs auf.

#### Node-RED Fehler
- **Board-Fehler:** nicht reproduzierbar, behoben durch Neustart von Node-RED  
- **Pin-Conflict-Error:** tritt auf, wenn mehrere Arduino-Out-Nodes denselben Pin ansprechen

---

### Fließtext
*(optional für Ergänzungen)*


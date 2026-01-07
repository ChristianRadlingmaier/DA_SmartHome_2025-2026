# Teilaufgabe Schüler Gierer

\textauthor{Janik Gierer}

Dieses Kapitel wird oft auch als _Literaturrecherche_ bezeichnet. Da gehört alles rein was der __normale__ Leser braucht um den praktischen Ansatz zu verstehen. Das bedeutet Sie brauchen einen roten Faden !

Das sind z.B: allgemeine Definitionen, Beschreibung von fachspezifischen Vorgehensweisen, Frameworks, Theorie zu verwendeten Algorithmen, besondere Umstände, ...

Es werden hier die Theoretischen und Praktischen Grundlagen zur Umsetztung von Home Assistant für ein Modelhaus gelegt und wie diese auch im echten Leben auf ein richtiges Haus angewendet werden können. Es wird das nötige Wissen dargestellt damit der Leser den praktischen teil nachvollziehen und verstehen kann. der fokus liegt hierbei auf der einrichtung des Dockers auf dem Raspberry Pi, der Kommunikation zwischen dem raspberry Pi und der Kommunikation zwischen Arduino Uno und Aktoren wie Sensoren.

### Verwendete Aktoren

- 100Pcs 1/4W 5% Toleranz 150Ohm Wiederstand
- 3mm Leuchtdioden

### Zusätlich Benötigtes

- IWILCS Dupont Crimp Set 790tlg inkl. Crimpzange
- Kabel 0,5mm²
- 4x PLA Basic Hellgrau (10104)
- 2x PLA Basic Dunkelgrau (10105)

### Verwendete Frameworks

- **Home Assistant**
    Dient als zentrales Steuerelement des Modelhauses. Es wird Praxisnahe simuliert wie man von einem Zentralen Standort sämtliche Geräte ansteuern und bedienen kann. 
- **Node-RED**
    Ermöglich die einfache erstellung und Automatisierung von Logik. Eingänge von Sensoren (Temperatur, Helligkeit) können eingelesen, verarbeitet werden und Aktoren entsprechend Angesteuert werden.  
- **MQTT**
    Wird als Kommunikationsprotokoll zwischen Mikrokontroller(Arduino Uno), dem Raspberry Pi und Home Assistant verwendet. Es sorgt für eine zuverlässige und schnelle Datenübermittlung.
- **Portainer**  
    Dient zur übersichtlichen verwaltung aller laufenden Docker-Container. Über das Webinterface können so Container leicht gestartet, gestoppt oder neu konfiguriert werden. 
- **Firmata**
    Firmata ist ein Kommunikationsprotokoll, mit dem ein Computer (in meinen Fall Raspberry Pi) einen Mikrocontroller (Arduino UNO) direkt steuern kann. Dabei läuft am Mikrocontroller das StandardFirmata Sketch dies setzt die Pins schreibt die HIGH/LOW zustände der LEDs und liest die Pins ein wenn es gebraucht wird.

# Teilaufgabe – Smart-Home-Umsetzung mit Home Assistant und Node-RED

**Schüler:** Janik Gierer

---

## 1. Theoretische Grundlagen
    Ein SmartHome beschreibt ein vernetztes Haus bei dem bestimmte meist alltägliche Komponenten von einem einzelnen Punkt aus gesteuert und ausgelesen werden können dies passiert entweder automatisch oder oder per Benutzereingabe. Beispiele dafür wären per Handy das Licht oder die Heizung ein/aus zu stellen oder ab einer bestimmten Uhrzeit die Rollläden automatisch nach unten zu fahren. Dafür werden im beispiel dieser Diplomarbeit ein Arduino als Mikrocontroller, ein raspberry Pi als Steuerzentrale sowie im konkreten Bereich Home Assitant als Automatisierungsplattform zum Einsatz Dadurch wird die Kommunikation zwischen Sensoren und Aktoren gewährleistet und die Steuerlogik wird mittels MQTT übertragen.
### 1.1 Sensorik, Aktorik und Steuerung im Modellhaus
Sensorik, Aktorik und Steuerung bilden die Grundlagen des Gesamten Modellhauses und sind in jedem Smart Home relevant. Dadurch wird die Grundlage für ein automatisertes System geschaffen. Wenn diese Komponenten zusammenarbeiten wird es möglich seine Aktoren voll automatisert zu steuern.
  **Sensorik**
  Die Sensorik sind alle Bauteile die Zustände oder die Umgebung messen. Die Sensoren dienen somit als  Sinnesorgane für das gestamte System. Es gibt Messergebnisse weiter (z.B Temperatur, Helligkeit, Bewegung oder Luftfeuchtigkeit). Diese daten werden dann an den Mikrokoontroller weiter gegäben.
  **Aktorik**
  Aktoren sind alle Komponenten die auf Basis von Benutzereingaben oder bei Änderung in den Messdaten reagieren. Es werden die Digitalen Signale in reale Aktionen umgewandelt. Aktoren wären Beispielsweise LEDs, Relais oder Motoren
  **Steuerung**
  Die Steuerung ist das zentrale Element des Modellhauses. Sie verarbeitet Eingaben und entscheidet, welche Aktoren angesteuert werden. Die Steuerlogik befindet sich in einer übergeordneten Software. Der Mikrocontroller setzt die empfangenen Befehle um. Dadurch bleibt das System einfach und flexibel.


#### 1.1.1 Sensoren zur Messung von Umweltparametern
Temperatur, Helligkeit, Bewegung und deren Bedeutung im Smart Home

#### 1.1.2 Aktoren zur Steuerung von Licht und Geräten
Relais, LEDs, Mini-Lampen – Einsatzmöglichkeiten und Grenzen

#### 1.1.3 Mikrocontroller (Arduino) als Basis für smarte Funktionen
Programmierbare Steuerzentrale für Sensoren und Aktoren

---

### 1.2 Datenübertragung und Kommunikation im Smart Home

#### 1.2.1 MQTT als zentrales Protokoll zwischen Arduino und Home Assistant
Topic-Struktur, Payload-Formate, Zuverlässigkeit

#### 1.2.2 Node-RED zur Verarbeitung und Weiterleitung von Nachrichten
Visuelle Programmierung zur Automatisierung

#### 1.2.3 Serieller Zugriff auf den Arduino vom Raspberry Pi
Verbindung über `/dev/ttyUSB0` für Steuerkommandos

---

### 1.3 Home Assistant als zentrale Steuereinheit

#### 1.3.1 Integration von MQTT-Geräten in Home Assistant
Manuelle Konfiguration vs. Auto-Discovery

#### 1.3.2 Automationen in Home Assistant
Lichtsteuerung bei Bewegung, Temperaturregelung usw.

---

### 1.4 Visualisierung und Benutzeroberfläche

#### 1.4.1 Lovelace UI zur Darstellung von Geräten und Zuständen
Dashboards für Licht, Heizung, Fensterstatus etc.

#### 1.4.2 Visualisierung von Zustandsänderungen
Lampenstatus, Temperaturverläufe, Türkontakte

---

## 2. Praktische Umsetzung

### 2.1 Aufbau des Modellhauses

#### 2.1.1 Stromversorgung und Verkabelung
Mini-USB, Breadboards, Steckverbindungen

#### 2.1.2 Einbau von LEDs, Relais und Temperatursensoren
Platzierung und Verkabelung im Hausmodell

---

### 2.2 Arduino-Programmierung

#### 2.2.1 Programm zum Einlesen und Senden von Sensorwerten
z. B. Temperatur via Serial/MQTT senden

#### 2.2.2 Empfang und Ausführung von Steuerkommandos
Licht EIN/AUS über Serial empfangen

---

### 2.3 Node-RED Workflows zur Kommunikation

#### 2.3.1 MQTT-IN zur Verarbeitung von Home-Assistant-Kommandos
z. B. `haus/licht/wohnzimmer` → Serial

#### 2.3.2 Serial-Out an den Arduino
Steuerung der Lichter via USB-Port

---

### 2.4 Docker-basierter Betrieb

#### 2.4.1 Container für Home Assistant, Node-RED, MQTT und Portainer
Verwaltet über `docker-compose` am Raspberry Pi
Es wird am Raspberry Pi eine `docker-compose.yaml` Datei erstellt 
Die `docker-compose.yaml` Datei sollte nicht im Home Verzeichnis liegen sondern in mindestens einem unter Verzeichnis zur besseren Kapselung und Übersicht 
Schritte für Erstellung 
1. cd $Unterverzeichnis
2. `sudo nano docker-compose.yaml/docker-compose.yml`
3. CODE EINFÜGEN
4. Speichern der Datei
5. Berechtigung gäben Für Datein ?!
  
 
  

---

### 2.5 Bedienung und Steuerung

#### 2.5.1 Steuerung über Smartphone, Tablet und PC
Zugriff auf Home Assistant UI im Browser

#### 2.5.2 Test der Licht- und Heizungssteuerung

---

### 2.6 Fehleranalyse und Optimierungen

#### 2.6.1 Serielle Fehler und Verbindungsprobleme
Behandlung von *Permission Denied* und Portproblemen

#### 2.6.2 MQTT-Verbindungsabbrüche und Topics
Vermeidung durch QoS und LWT

---

## 2.7 Ausblick

### 2.7.1 Erweiterung mit Sprachsteuerung (z. B. Alexa)
### 2.7.2 Erweiterung auf mehrere Räume oder Wohnungen
### 2.7.3 Einbindung weiterer Sensoren (CO₂, Luftqualität, Helligkeit)


## Praktische Arbeit

Am Beginn der Arbeit wurde überlegt wie kann man es schaffen mit einem Ardiono UNO der selbst keine Internetverbindung hat mit Home Assistant zu verbinden. Es ist möglich mit einem Programm auf den Ardiono Namens standardFirmata dies ist ein programm das man installiert und dannach ganz einfach das gennante Example Programm auf dem Arduino lädt. Danach wurde festegestellt die Realitätsnahste verwendung von Home Assistant ist auf einem Raspberry Pi bei dem Home Assistant in einem Docker Container läuft. 

### Messergebnisse




### Fehler

## Berechtigunsprobleme 
Diese Proble treten bei erstellung des Dockers auf und bei späterer Ausführung
## Node-red Fehler
`Permanent Error: Board` Fehler nicht reproduzierbar und wurde gelöst mit neustart von nodered und ändern des Pfades im Arduino Out-Node
`Error: Pin conflict` Es wird in den arduino out nodes nicht erlaubt zweimal auf den gleichen Pin zuzugreifen

### Etwas Fliesstext


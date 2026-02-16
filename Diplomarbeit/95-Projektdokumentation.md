\newpage

## Dokumentation

### Use Cases

#### Sensordaten erfassen und senden

**Beschreibung:** Das System erfasst kontinuierlich Umweltparameter (z. B. Temperatur, Helligkeit) im Modellhaus und sendet diese an die Zentrale.  
**Trigger:** Zeitintervall oder Zustandsänderung eines Sensors  
**Bedingungen:** Sensoren, Mikrocontroller (Arduino) und MQTT-Broker sind aktiv  
**Ablauf:**

1. Sensoren erfassen Messwerte  
2. Mikrocontroller verarbeitet und formatiert die Daten  
3. Daten werden über MQTT an die zentrale Plattform gesendet  

**Alternative:** Sensor liefert ungültige Werte oder fällt aus  
**Ergebnis:** Aktuelle Sensordaten stehen für Automatisierung und Visualisierung bereit

#### Beleuchtung automatisch steuern

**Beschreibung:** Bei Dunkelheit und erkannter Bewegung wird die Beleuchtung automatisch eingeschaltet.  
**Trigger:** Helligkeitswert unter Schwellwert und Bewegung erkannt  
**Bedingungen:** Sensorik, Regelwerk (Home Assistant/FHEM/Node-RED) und Aktorik sind aktiv  
**Ablauf:**

1. Helligkeit wird geprüft  
2. Bewegungsmelder meldet Aktivität  
3. Steuerlogik schaltet Licht über MQTT ein  

**Alternative:** Einer der Sensorwerte fehlt oder ist fehlerhaft  
**Ergebnis:** Licht wird für die definierte Zeit aktiviert und danach wieder ausgeschaltet


#### Sensordaten visualisieren

**Beschreibung:** Mess- und Statusdaten werden über Dashboard-Oberflächen dargestellt.  
**Trigger:** Benutzer öffnet Home-Assistant-, FHEM- oder Node-RED-Dashboard  
**Bedingungen:** Dienste und Datenquellen sind aktiv  
**Ablauf:**

1. Plattform lädt aktülle Sensordaten  
2. Daten werden als Statuswerte und Verläufe dargestellt  
3. Benutzer kann Abweichungen erkennen und reagieren  

**Alternative:** Datenqülle nicht verfügbar  
**Ergebnis:** Transparente Übersicht über aktuellen Systemzustand

#### Geräte manuell steuern

**Beschreibung:** Benutzer steuern Licht oder weitere Aktoren manuell über die Weboberfläche.  
**Trigger:** Benutzeraktion im Dashboard  
**Bedingungen:** Benutzer ist angemeldet und Berechtigungen sind vorhanden  
**Ablauf:**

1. Benutzer wählt Gerät und Aktion  
2. Plattform validiert den Befehl  
3. Befehl wird an Mikrocontroller/Aktorik übertragen  

**Alternative:** Keine Verbindung zum MQTT-Broker oder Aktor  
**Ergebnis:** Gewünschte Aktion wird im Modellhaus ausgeführt und rückgemeldet

#### Containerdienste verwalten

**Beschreibung:** Betriebsdienste (Home Assistant, FHEM, MQTT, Portainer) werden containerbasiert betrieben und verwaltet.  
**Trigger:** Wartung, Neustart oder Konfigurationsänderung  
**Bedingungen:** Docker-Umgebung auf Raspberry Pi ist aktiv  
**Ablauf:**

1. Administrator öffnet Portainer oder Docker-Setup  
2. Container werden gestartet, gestoppt oder aktualisiert  
3. Dienststatus wird kontrolliert  

**Alternative:** Container startet aufgrund Konfigurationsfehler nicht  
**Ergebnis:** Plattformdienste laufen stabil und getrennt voneinander

#### MQTT-Verbindungsabbruch behandeln

**Beschreibung:** Das System reagiert auf Kommunikationsprobleme zwischen Komponenten.  
**Trigger:** Broker oder Client verliert Verbindung  
**Bedingungen:** Monitoring/Logging ist aktiv  
**Ablauf:**

1. Verbindungsabbruch wird erkannt  
2. Reconnect-Mechanismus startet  
3. Dienststatus wird protokolliert und erneut geprüft  

**Alternative:** Reconnect scheitert mehrfach  
**Ergebnis:** Kommunikation wird wiederhergestellt oder Fehler wird sichtbar gemeldet

### Projektfortschritt 09. Juli 2025 bis 25. August 2025

#### Gesamtstatus

* Projektaufbau und technische Grundlagen wurden gestartet.
* Raspberry Pi wurde eingerichtet und erste Docker-Dienste wurden aufgesetzt.
* Home Assistant, Node-RED, MQTT und Portainer wurden in einer ersten Betriebsversion gestartet.
* Die Modellierung des Hauses in Fusion 360 wurde begonnen (Grundstruktur, Fenster/Türen, Kabelkanäle, Zwischendach, Dach).
* Erste Arbeiten für Skripting und Automatisierung (Perl) wurden aufgebaut.

| Dimension           | Status                         | Massnahmen |
|:--------------------|:-------------------------------|:-----------|
| Leistungsziele      | Teilweise erreicht             | Fokus auf stabile Sensor-/Aktoranbindung und erste End-to-End-Flows |
| Terminziele         | Im Plan                        | Priorisierung der Kernfunktionen vor Detailerweiterungen |
| Kostenziele         | Im Budget                   | Weiterhin Nutzung geplanter Komponenten und vorhandener Infrastruktur |
| Teamarbeit          | Gut                            | Regelmässige Abstimmung zwischen Modellbau, Backend und Automatisierung |

:Projektstatus am 2025-08-25

#### Notwendige Entscheidungen

* Festlegung einer stabilen Basisarchitektur für die Parallelität von Home Assistant und FHEM.
* Entscheidung, welche Automatisierungen zuerst produktiv umgesetzt werden (Licht, Temperatur, Visualisierung).
* Priorisierung von Modellbaufortschritt gegenüber zusätzlichen Komfortfunktionen.

#### Nächste Schritte

* Modellhaus in druckbare Segmente überführen und mechanisch final aufbauen.
* Sensoren und Aktoren verdrahten und in Betrieb nehmen.
* MQTT-Flows und Dashboards für Licht-, Temperatur- und Statusanzeigen finalisieren.
* Systemtests mit Fehleranalyse (Kommunikation, Sensorwerte, Schaltlogik) durchführen.

### Projektfortschritt 26. August 2025 bis 20. Februar 2026

#### Gesamtstatus

* Projektplanung und Systemaufbau wurden gemäss Meilensteinen umgesetzt.
* Modellhausaufbau, Grundverkabelung und Montage der Sensorik/Aktorik wurden abgeschlossen.
* Systemgrundlagen (Raspberry Pi, Docker, MQTT-Broker) laufen stabil.
* Home Assistant/FHEM und Node-RED wurden integriert; grundlegende Automatisierungen funktionieren.
* Testbetrieb, Optimierung und Dokumentationsarbeiten wurden bis zur Finalisierung durchgeführt.

| Dimension           | Status                         | Massnahmen |
|:--------------------|:-------------------------------|:-----------|
| Leistungsziele      | Weitgehend erreicht            | Restpunkte auf Dokumentationsqualität und Feinschliff konzentrieren |
| Terminziele         | Erreicht                       | Abschlussarbeiten entlang der verbleibenden Abgabetermine führen |
| Kostenziele         | Im Budget                   | Keine ungeplanten Zusatzanschaffungen |
| Teamarbeit          | Sehr gut                       | Rollenaufteilung (Modellbau, Steuerlogik, Plattformbetrieb) beibehalten |

:Projektstatus am 2026-02-20

#### Notwendige Entscheidungen

* Endgültige Abgrenzung des Funktionsumfangs gemäss Nicht-Zielen (kein Produktivsystem, keine native App).
* Vereinheitlichung der Formulierungen und technische Konsistenz in allen Kapitelteilen.
* Festlegung der finalen Demo-Szenarien für Präsentation und Fachgespräch.

#### Nächste Schritte

* Endkorrektur der schriftlichen Arbeit (Rechtschreibung, Grammatik, Struktur).
* Letzte Gesamtsystemtests vor Abgabe und Präsentation.
* Abgabe der Dokumentation und Vorbereitung des Projektabschlusses (Abgabe am 2026-03-06, Präsentation im März 2026).

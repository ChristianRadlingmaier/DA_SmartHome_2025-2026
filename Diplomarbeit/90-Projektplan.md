# Projekthandbuch – SmartHome Diplomarbeit

**Autor:** Janik Gierer, Christian Radlinmaier, Christian Beichtbuchner, Chloe Pripfl

## Entwicklungsplan

### Projektauftrag

Im Rahmen unserer Diplomarbeit entwickeln wir ein modellbasiertes SmartHome-System mit verschiedenen Sensoren und Aktoren. Diese werden über ein zentrales System mit FEHM (FHEM) und Home Assistant verwaltet und gesteuert. Das Projekt befasst sich mit der Automatisierung von Haushaltsprozessen auf einem Miniaturmodellhaus und bietet zusätzlich eine webbasierte Bedienoberfläche über Portainer und Node-RED. Ziel ist es, ein skalierbares, offenes System zu demonstrieren, das mit verschiedenen Protokollen wie MQTT kommuniziert.

### Projektziele

- Aufbau eines funktionstüchtigen SmartHome-Modellhauses mit realitätsnaher Steuerung.
- Integration von Home Assistant zur Steuerung und Visualisierung.
- Anbindung von Sensoren (Temperatur, Helligkeit, Türkontakt) und Aktoren (Licht, Motoren, Heizung) via MQTT.
- Visualisierung und Bedienung über Node-RED.
- Verwaltung der Containerumgebung über Portainer.
- Dokumentation der Einrichtung und Konfiguration.
- Vorbereitung für später mögliche Erweiterungen wie Fernzugriff, Spracherkennung etc.

### Nicht-Ziele

- Keine Entwicklung eigener Sensorhardware (nur Integration vorhandener Komponenten).
- Keine native App-Entwicklung.
- Kein Live-Zugriff von außerhalb ohne VPN oder Portweiterleitung.

### Projektnutzen

- Demonstration moderner Automatisierung im Kleinformat.
- Praxiserfahrung im Umgang mit Containerisierung, MQTT und Home Assistant.
- Anwendbares Wissen für spätere berufliche Aufgaben oder größere Hausautomatisierungen.
- Beitrag zum praxisnahen Unterricht an der HTL Leoben.

### Projektauftraggeber/in

**HTL Leoben** – Abteilung für Informationstechnologie  
**Betreuer:** Prof. Hutter, Prof. Poetscher

### Projekttermine

| Termin        | Inhalt                          |
|---------------|----------------------------------|
| 2025-09-15    | Projektmanagement abgeschlossen  |
| 2025-10-10    | Prototypaufbau abgeschlossen     |
| 2025-10-31    | Systemintegration abgeschlossen  |
| 2025-11-15    | Testbetrieb + Fehleranalyse      |
| 2025-12-05    | Finalisierung & Präsentation     |
| 2026-01-15    | Abgabe Dokumentation             |

### Projektkosten

| Meilenstein  | Kostenart | Menge | Einzelpreis | Gesamtkosten | Bezahlt durch     |
|--------------|-----------|-------|-------------|---------------|--------------------|
| Hardware     | Sensoren  | 6     | 7.00 €      | 42.00 €       | Schüler            |
| Hardware     | Aktoren   | 4     | 8.00 €      | 32.00 €       | Schüler            |
| Plattformen  | Raspberry Pi | 1  | 60.00 €      | 60.00 €       | Schule            |
| Haus         | 3D Druck  | 4     | 25.00 €      | 100.00€       | Schule            |
| Zubehör      | Kabel/Adapter | 1 | 10.00 €      | 10.00 €       | Schüler           |
| Druckkosten  | Dokumentation | 1 | 25.00 €      | 25.00 €       | Schüler           |

**Gesamtkosten: 169.00 €**

### Projektrisiken

| Risiko                          | Wahrscheinlichkeit | Auswirkungen                          | Maßnahmen                                 |
|---------------------------------|---------------------|----------------------------------------|-------------------------------------------|
| Hardware beschädigt             | Mittel (30%)        | Ersatz notwendig, Verzögerung möglich | Ersatzgeräte vorrätig halten              |
| WLAN-Probleme                   | Niedrig (10%)       | Keine Kommunikation zwischen Modulen  | Kabelgebundene Option vorbereiten         |
| MQTT-Verbindungsprobleme        | Mittel (20%)        | Sensoren/Aktoren nicht steuerbar      | Logging, Restart-Mechanismen implementieren|
| Komplexität Home Assistant      | Hoch (40%)          | Verzögerung durch Konfigurationsfehler| Schrittweise testen, Dokumentation lesen  |

## Projektorganisation

### Projektbeteiligte

| Vorname   | Nachname     | Organisation | Kontaktinfo                  |
|-----------|--------------|--------------|------------------------------|
| Janik     | Gierer       | HTL Leoben   | 211wita04@htl-leoben.at       |
| Christian | Beichtbuchner| HTL Leoben   | 211wita01@htl-leoben.at       |
| Christian | Radlinmier   | HTL Leoben   | 211witb--@htl-leoben.at       |
| Chloe     | Pripfl       | HTL Leoben   | 211witb--@htl-leoben.at       |

### Projektrollen

| Rolle              | Beschreibung                                      | Name                    |
|--------------------|---------------------------------------------------|-------------------------|
| Projektleiter      | Gesamtkoordination, Umsetzung in HomeAssist       | Janik Gierer        |
|                    |                                                   | Christian Beichtbuchner |
|                    |                                                   | Christian Radlingmaier  |
|                    |                                                   | Chloe Pripfl            |
| Betreuer           | Schulischer Ansprechpartner, techn. Kontrolle     | Prof. Leitner           |


### Vorgehen bei Änderungen

- Änderungen werden im GitHub-Repo dokumentiert (Changelog.md).
- Bei größeren Änderungen (z. B. Sensorwechsel) wird der Betreuer informiert.
- Der Projektleiter entscheidet in Absprache mit Team und Betreuer über Annahme.

## Meilensteine

### 2025-09-15: Projektmanagement abgeschlossen
- Projekthandbuch erstellt und bestätigt.
- Zeitplan abgestimmt.

### 2025-10-10: Aufbau SmartHome Modellhaus abgeschlossen
- Sensorik und Aktorik vollständig integriert.
- Stromversorgung getestet.

### 2025-10-31: Home Assistant lauffähig
- Docker-Container laufen stabil.
- Verbindung zu MQTT und Sensoren funktioniert.

### 2025-11-15: Systemtest und Feineinstellungen
- Automatisierungen laufen wie geplant.
- UI optimiert (Node-RED Flows).

### 2025-12-05: Präsentation vorbereitet
- Demo vorbereitet.
- Feedback eingeholt und eingearbeitet.

### 2026-01-15: Abgabe
- Dokumentation vollständig gedruckt und gebunden.
- Alle Unterlagen im DA-Portal eingetragen.

## Anwendungsfälle

### Überblick

- SmartHome automatisch beleuchten
- Temperaturabhängige Heizsteuerung
- Türkontaktmeldung per Pushnachricht
- Visualisierung der Sensordaten im Dashboard
- Fernsteuerung über Handy (lokales WLAN)
- Zeitschaltfunktionen

### Beispiel: Licht automatisch steuern

#### Kurzbeschreibung
Die Beleuchtung wird bei Dunkelheit und Bewegung im Raum automatisch eingeschaltet.

#### Trigger
Helligkeitssensor meldet Dunkelheit **und** PIR-Sensor erkennt Bewegung.

#### Vorbedingung
System ist gestartet und Sensoren sind einsatzbereit.

#### Nachbedingung
Lampe wird für 2 Minuten eingeschaltet.

#### Akteure
- Benutzer (indirekt)
- Sensoren (Bewegung, Helligkeit)

#### Standardablauf

1. Helligkeit < 200 Lux → Bedingung erfüllt
2. Bewegung erkannt → Bedingung erfüllt
3. Lampe wird via MQTT eingeschaltet

#### Fehlerfälle

- Keine Bewegung: Lampe bleibt aus
- Lichtsensor defekt: keine Aktion

#### Systemzustand im Fehlerfall
Licht bleibt aus, Status im Dashboard wird angezeigt.

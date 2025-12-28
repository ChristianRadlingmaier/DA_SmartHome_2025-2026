# Teilaufgabe Schüler Beichtbuchner
\textauthor{Christian Josef Beichtbucher}
## Theorie

### Mein Teil der Diplomarbeit
Mein Teil der Diplomarbeit ist es ein Haus zu modellieren um dieses anschließend mit Sensoren und Aktoren auszustatten. Der Plan ist es ein bereits bestehendes Haus nachzubauen, um es so Real wie möglich zu halten. Das Haus wird mithilfe von Online Downloadbaren Möbel eingerichtet und der Garten wird auf die gleiche weise angedeutet und dekoriert. Vorgesehene ansteuerbare Elemente sind LEDs. Im Unterricht hatten wir bereits eine Wetterstation gebaut, welche hier auch integriert wird. 

### Digitale Hausmodellierung

#### CAD-Programme im Überblick
CAD-Programme werden in der Architektur, im Ingenieurwesen und im Baugewerbe eingesetzt, um Projekte zu entwerfen und Konstruktionsunterlagen, wie z. B. Konstruktions- und Fertigungszeichnungen, zu erstellen.

#### Allgemeine Erklärung von CAD-Programmen
CAD steht für computergestütztes Zeichnen oder computergestütztes Entwerfen. In der Vergangenheit wurden Bauzeichnungen manuell per Hand auf Papier gezeichnet. CAD-Programme haben diese Funktion ersetzt und ermöglichen es Architekten, Ingenieuren und Designern, ihre Entwürfe digital zu erstellen. CAD-Programme ermöglichen es, Entwürfe je nach gewünschtem Ausgabeformat in 2D oder 3D zu erstellen, wie beispielsweise gedruckte 2D-Zeichnungen oder digital geteilte 3D-Modelle. Ein CAD-Programm hilft dabei, verschiedene Entwurfsoptionen zu testen, komplexe Ideen und Räume visuell zu erklären und herauszufinden, wie ein Design funktionieren und aussehen wird. Ein weiterer Vorteil von CAD-Programmen ist, dass sie während der Planungs- und Entwurfsphasen eines Projekts einen hohen Grad an Präzision ermöglichen. Exakt gezeichnete Entwürfe bedeuten, dass es während der Konstruktion weniger Fehler gibt, was Zeit und Geld spart sowie nachhaltiges Arbeiten fördert.

### Unterschiede zwischen einzelne CAD-Programmen
Industrie/Professionell
AutoCAD

SolidWorks

AutoDesk Fusion360

Privat/Hobby
FreeCAD

OpenSCAD

LibreCAD



#### Zweck der Hausmodellierung
- Warum das Haus vor dem Bau digital modelliert wird
- Vorteile für Planung, Übersicht und Änderungen



### Verkabelung im Modellhaus
- Theoretische Grundlagen der Verkabelung eines Modellhauses
- Zusammenhang zwischen Modellaufbau und Leitungsführung

#### Grundlagen der Modellhausverkabelung
- Aufbau einer einfachen Verkabelung im Modell
- Verwendung von Niederspannung

#### Stromversorgung im Modell
- Versorgung über Netzteil oder USB
- Spannungen für Arduino und Komponenten

#### Leitungen und Verbindungstechniken
- Verwendete Kabelarten
- Steckverbindungen und Lötstellen

#### Komponenten im Modellhaus
- Arduino als Steuerungseinheit
- eigenschaften der einzelnen arduinos
- ## 1. Arduino Uno
- **Beschreibung:** Das wohl bekannteste Board, ideal für Einsteiger.  
- **Merkmale:** 14 digitale I/O-Pins, 6 analoge Eingänge, USB-Schnittstelle, ATmega328P-Mikrocontroller.  
- **Einsatz:** Kleine Projekte, Lernplattform für Programmierung und Elektronik.
![](){width=80%}

## 2. Arduino Nano
- **Beschreibung:** Kompaktes Board, ideal für Platz sparende Projekte.  
- **Merkmale:** 14 digitale I/O-Pins, 8 analoge Eingänge, ATmega328P, USB-Anschluss mini/micro.  
- **Einsatz:** Wearables, kleine Roboter, tragbare Geräte.


## 3. Arduino Mega 2560
- **Beschreibung:** Größeres Board für komplexere Projekte.  
- **Merkmale:** 54 digitale I/O-Pins, 16 analoge Eingänge, ATmega2560-Mikrocontroller.  
- **Einsatz:** Projekte mit vielen Sensoren/Aktoren, 3D-Drucker, große Automatisierungen.


## 4. Arduino Leonardo
- **Beschreibung:** Unterstützt USB-HID-Funktionen, kann als Maus/Tastatur agieren.  
- **Merkmale:** ATmega32u4, 20 digitale Pins, 12 analoge Eingänge.  
- **Einsatz:** Interaktive Geräte, Steuerungen für Computer.  





















#### Sensoren und Aktoren

## 1. Sensoren
Ein **Sensor** ist ein Gerät, das physikalische, chemische oder biologische Größen aus der Umgebung **erfasst** und in ein elektrisches Signal umwandelt, damit ein Computer, Mikrocontroller oder ein anderes System diese Daten weiterverarbeiten kann.  

**Merkmale von Sensoren:**
- Erfassen Umgebungsgrößen wie Temperatur, Licht, Feuchtigkeit, Bewegung, Druck oder chemische Zusammensetzung.
- Wandeln die erfassten Größen in elektrische Signale (Spannung, Strom, Widerstand oder digitale Werte) um.
- Werden oft in automatisierten Systemen eingesetzt, um Zustände zu überwachen.

**Beispiele für Sensoren:**
| Sensor | Messgröße | Anwendung |
|--------|-----------|-----------|
| Temperatursensor | Temperatur | Raumklimasteuerung, Wetterstationen |
| Lichtsensor | Helligkeit | Automatische Beleuchtung, Kameras |
| Bewegungssensor | Bewegung | Alarmanlagen, automatische Türen |
| Feuchtigkeitssensor | Luftfeuchtigkeit | Klimakontrolle, Landwirtschaft |

**Merksatz:**  
> Sensoren *fühlen* oder *messen* die Umwelt.

---

## 2. Aktoren
Ein **Aktor** ist ein Gerät, das elektrische Signale empfängt und in eine **physikalische Aktion** umsetzt. Anders gesagt: Aktoren führen Befehle aus und verändern die Umgebung.  

**Merkmale von Aktoren:**
- Reagieren auf Steuerbefehle aus einem System.
- Wandeln elektrische Signale in mechanische, hydraulische, pneumatische oder andere physikalische Bewegungen um.
- Werden eingesetzt, um Prozesse zu automatisieren oder direkt auf Sensorinformationen zu reagieren.

**Beispiele für Aktoren:**
| Aktor | Wirkung | Anwendung |
|-------|---------|-----------|
| Elektromotor | Bewegung / Drehung | Roboterarme, Lüfter |
| Lampe | Licht erzeugen | Beleuchtungssysteme |
| Ventil | Öffnen / Schließen | Heizungs- oder Bewässerungssysteme |
| Lautsprecher | Ton / Schall | Audioausgabe, Warnsysteme |

**Merksatz:**  
> Aktoren *handeln* oder *tun etwas* in der Umwelt.

---

- LEDs, Sensoren und weitere Bauteile




























## Praktische Arbeit

### Planung des Modellhauses
- Vorbereitung für die praktische Umsetzung
- Ziel des Modellhauses

#### Anforderungen an das Modell
- Funktionsumfang des Modellhauses
- Gewählte Komponenten

#### Aufbau und Struktur des Hauses
- Aufbau des Modellhauses
- Aufteilung in Ebenen und Räume


### Hausmodellierung in Fusion 360
- Umsetzung des Modellhauses als 3D-Modell
- Grundlage für den späteren Aufbau

#### Erstellung des Grundrisses
- Abmessungen des Modellhauses
- Anordnung der Räume

#### Modellierung der Gebäudestruktur
- Modellierung von Wänden, Decken und Böden
- Berücksichtigung mehrerer Ebenen

#### Detaillierung des Modells
- Modellierung von Türen und Fenstern
- Anpassung für Elektronikbauteile

#### Parametrische Modellierung
- Nutzung von Parametern
- Vereinfachung von Änderungen


### Verkabelung des Modellhauses
- Umsetzung der Elektronik im Modell
- Verbindung von Mechanik und Elektronik

#### Planung der Verkabelung
- Planung der Kabelführung
- Platzierung der Elektronik

#### Leitungsführung im Modell
- Führung der Kabel durch das Modell
- Saubere und übersichtliche Verlegung

#### Anschluss von Arduino und Komponenten
- Verbindung von LEDs und Sensoren
- Beschreibung der Anschlüsse

#### Funktionstest
- Überprüfung der Verkabelung
- Erste Tests der Funktionen


### Visualisierung und Dokumentation
- Darstellung der Ergebnisse
- Unterstützung der Erklärung

#### Visualisierung des Hausmodells
- Darstellung des fertigen 3D-Modells
- Ansichten und Perspektiven

#### Darstellung der Verkabelung
- Visualisierung der Kabelführung
- Hervorhebung einzelner Komponenten

#### Dokumentation des Modells
- Fotos und Screenshots
- Verwendung in der Diplomarbeit


## Zusammenfassung

### Ergebnisse der Modellierung
- Bewertung des 3D-Modells
- Erfüllung der Anforderungen

### Erkenntnisse aus der Verkabelung
- Erfahrungen mit Arduino und Elektronik
- Probleme und Lösungen

### Ausblick
- Mögliche Erweiterungen
- Weitere Funktionen des Modellhauses

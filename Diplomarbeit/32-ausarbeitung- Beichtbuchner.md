# Teilaufgabe Schüler Beichtbuchner
\textauthor{Christian Josef Beichtbucher}

## Theorie

### Einordnung des Aufgabenbereichs
Mein Teil der Diplomarbeit ist es ein Haus zu modellieren um dieses anschließend mit Sensoren und Aktoren auszustatten. Der Plan ist es ein bereits bestehendes Haus nachzubauen, um es so Real wie möglich zu halten. Das Haus wird mithilfe von Online Downloadbaren Möbel eingerichtet und der Garten wird auf die gleiche weise angedeutet und dekoriert. Vorgesehene ansteuerbare Elemente sind LEDs sowie auch eine Wetterstation welche wir im Unterricht schon gebaut und Programmiert haben. 

## 1 Modellierung

### 1.1 Grundlagen der 3D-Modellierung

Unter 3D-Modellierung versteht man die digitale Erstellung dreidimensionaler Objekte mit spezieller Software. Dabei werden geometrische Elemente wie Punkte, Linien und Flächen verwendet, um virtuelle Modelle mit räumlicher Ausdehnung zu erzeugen. Diese Modelle besitzen neben Länge und Breite auch eine Tiefe und können dadurch realitätsnah dargestellt und weiterverarbeitet werden. 
[@3D-Modellierung-Adobe]

### 1.2 Ablauf der 3D-Modellierung  

Der Prozess der 3D-Modellierung lässt sich in mehrere grundlegende Schritte unterteilen. Diese Abfolge stellt einen allgemeinen Überblick dar, wobei der genaue Arbeitsablauf je nach verwendeter Software, persönlicher Arbeitsweise oder Projektanforderungen variieren kann. 

1. Konzeptphase  
Zu Beginn steht die Ideenfindung. In dieser Phase wird das geplante Objekt konzeptionell ausgearbeitet, beispielsweise durch Skizzen auf Papier oder einfache digitale Entwürfe. Ziel ist es, eine klare Vorstellung des Modells zu entwickeln, bevor mit der eigentlichen Modellierung begonnen wird.

2. Modellierungsphase  
In diesem Schritt wird das Objekt mithilfe einer 3D-Software erstellt. Dabei kommen unterschiedliche Modellierungstechniken zum Einsatz. Häufig wird mit geometrischen Grundelementen gearbeitet, die aus Punkten, Kanten und Flächen bestehen und schrittweise zu einem dreidimensionalen Modell zusammengesetzt werden. Je nach Software können auch alternative Methoden verwendet werden, die ein besonders intuitives Arbeiten ermöglichen.

3. Texturierung  
Nach der Erstellung der Grundform werden dem Modell Materialien und Oberflächen zugewiesen. Diese bestimmen das visuelle Erscheinungsbild und verleihen dem Objekt Farbe, Struktur und Detailtiefe. Texturen können individuell erstellt, automatisch generiert oder aus Bildvorlagen abgeleitet werden.

4. Rendering und Nachbearbeitung  
Im letzten Schritt wird das fertige Modell visualisiert. Dabei werden Beleuchtung, Schatten und weitere visuelle Effekte berücksichtigt, um realistische oder stilisierte Darstellungen zu erzeugen. Dieser Vorgang erfordert in der Regel eine hohe Rechenleistung. Optional können die erzeugten Bilder oder Animationen anschließend weiterbearbeitet werden, um das Endergebnis zu optimieren.  
[@3D-Modellierung-Adobe]

### 1.3 Arbeiten mit Skizzen

Bevor ein dreidimensionales Objekt erstellt werden kann, wird in der Regel zunächst eine zweidimensionale Skizze angefertigt. Diese Skizze dient als Grundlage für die spätere Modellierung und definiert die Form sowie die grundlegenden Abmessungen des Objekts. Anschließend wird die 2D-Geometrie in die dritte Dimension überführt, indem sie entlang einer Achse extrudiert oder auf andere Weise räumlich erweitert wird. Auf diese Weise entsteht ein Volumenkörper, der anschließend weiterbearbeitet, verfeinert und an die gewünschten Anforderungen angepasst werden kann.

<!-- ![Skizze](img/Skizze.png)-->

### 1.4 Volumen- und Flächenmodellierung

In CAD-Programmen stehen zahlreiche Werkzeuge zur Verfügung, mit denen dreidimensionale Objekte erstellt und weiterbearbeitet werden können. Diese Werkzeuge ermöglichen es, Körper zu erweitern, Material gezielt zu entfernen oder Öffnungen und Aussparungen zu erzeugen. Typische Bearbeitungsschritte sind beispielsweise das Hinzufügen von Volumen, das Ausschneiden von Bereichen oder das Erstellen von Bohrungen.

<!-- ![Würfel](img/wuerfel.png) -->

Bei der Volumenmodellierung arbeitet man mit geschlossenen Körpern, die ein klares Innenvolumen haben. Dadurch lassen sich Bauteile genau konstruieren, und man kann zum Beispiel ihr Gewicht, Material oder ihre Stabilität berechnen. Diese Methode eignet sich besonders für technische Teile, weil sie eine stabile und verlässliche Form liefert.

Die Flächenmodellierung arbeitet dagegen nur mit einzelnen Oberflächen, ohne dass ein richtiges Volumen entsteht. Sie wird oft für komplexe oder organische Formen genutzt, wie sie etwa in der Automobil- oder Flugzeuggestaltung vorkommen. Mit dieser Methode lassen sich sehr detaillierte und geschwungene Formen erstellen, allerdings muss man genau auf die Übergänge zwischen den Flächen achten, damit das Modell sauber bleibt. 

### 1.5 Strukturierung komplexer Modelle

Die Strukturierung komplexer CAD-Modelle ist ein wesentlicher Bestandteil einer übersichtlichen und wartbaren Konstruktion. Um auch umfangreiche Modelle nachvollziehbar zu halten, werden unterschiedliche Modellierungsstrategien eingesetzt. Eine klare Gliederung erleichtert nicht nur die Bearbeitung, sondern ermöglicht auch spätere Änderungen und Erweiterungen ohne großen Mehraufwand.

Ein häufig verwendeter Ansatz ist das sogenannte Top-Down-Design. Dabei wird zunächst eine übergeordnete Struktur, oft als „Skelettmodell“ bezeichnet, erstellt, welche die grundlegenden Abmessungen und Referenzen vorgibt. Einzelne Bauteile werden anschließend auf Basis dieses Skeletts modelliert. Änderungen an den zentralen Vorgaben wirken sich automatisch auf alle abhängigen Komponenten aus, wodurch sich dieser Ansatz besonders für flexible und anpassbare Konstruktionen eignet.

Im Gegensatz dazu steht das Bottom-Up-Design. Hier werden einzelne Bauteile unabhängig voneinander modelliert und anschließend zu einer Baugruppe zusammengefügt. Diese Vorgehensweise ist besonders sinnvoll, wenn standardisierte oder wiederverwendbare Teile eingesetzt werden. Änderungen an der Gesamtstruktur erfordern jedoch meist eine manuelle Anpassung der einzelnen Komponenten.

Ergänzend dazu spielt die parametrische Modellierung eine zentrale Rolle bei der Strukturierung komplexer Modelle. Durch die Definition von Parametern, Beziehungen und Abhängigkeiten können Änderungen gezielt und konsistent umgesetzt werden, ohne dass das Modell vollständig neu erstellt werden muss.

Zusätzlich tragen eine sinnvolle Unterteilung in Baugruppen, eine klare Benennung von Bauteilen sowie eine logische Organisation von Ebenen und Referenzen wesentlich zur Übersichtlichkeit bei. Der gezielte Einsatz spezieller Modellierungsfunktionen, wie etwa Splines oder Flächenbefehle für organische Geometrien, unterstützt die Umsetzung komplexer Formen und erhöht die Flexibilität bei der Modellierung.

### 1.6 Verwendung externer Modelle und Bibliotheken

Neben der eigenen Modellierung besteht die Möglichkeit, auf externe 3D-Modelle und Bibliotheken zurückzugreifen, die von anderen Personen oder Organisationen online zur Verfügung gestellt werden. Solche Modelle umfassen beispielsweise Möbel, Bedienelemente wie Taster oder Knöpfe sowie weitere funktionale oder dekorative Bauteile.

Der Einsatz externer Modelle kann den Modellierungsprozess deutlich beschleunigen, da häufig verwendete oder standardisierte Objekte nicht vollständig neu erstellt werden müssen. Diese Modelle können in das eigene CAD-Projekt importiert und bei Bedarf angepasst oder weiterverarbeitet werden.

Solche Modelle eignen sich auch für die physische Umsetzung mithilfe eines 3D-Druckers. Dabei können heruntergeladene Modelle ausgedruckt und anschließend in ein Projekt integriert werden. Voraussetzung hierfür ist jedoch, dass die Modelle korrekt skaliert sind und den technischen Anforderungen des jeweiligen Druckverfahrens entsprechen. Durch den gezielten Einsatz externer Modelle lässt sich der Arbeitsaufwand reduzieren, während gleichzeitig ein hoher Detailgrad erreicht werden kann. 

## 2 CAD-Programme

### 2.1 CAD-Programme im Überblick

CAD-Programme sind spezielle Softwareprogramme, die zur Erstellung und Bearbeitung von digitalen Zeichnungen und Modellen verwendet werden. Sie helfen dabei, technische Entwürfe übersichtlich und präzise darzustellen und dienen als wichtige Grundlage für die weitere Planung und Umsetzung.

>CAD-Programme werden in der Architektur, im Ingenieurwesen und im Baugewerbe eingesetzt, um Projekte zu entwerfen und Konstruktionsunterlagen, wie z. B. Konstruktions- und Fertigungszeichnungen, zu erstellen. 

[@CAD-Programme-ALLPLAN]

#### 2.2 Allgemeine Funktionsweise von CAD-Programmen

CAD ist die Abkürzung für computergestütztes Zeichnen bzw. computergestütztes Entwerfen. Während Bau- und Konstruktionszeichnungen früher manuell auf Papier erstellt wurden, werden diese Aufgaben heute größtenteils mithilfe spezieller Software durchgeführt. CAD-Programme ermöglichen es, Entwürfe digital zu erstellen und sowohl in zweidimensionaler als auch in dreidimensionaler Form darzustellen. Dadurch können Zeichnungen ausgedruckt oder digitale 3D-Modelle weiterverwendet und geteilt werden.

Der Einsatz von CAD-Software erleichtert es, unterschiedliche Entwurfsvarianten zu vergleichen und komplexe Konstruktionen anschaulich darzustellen. Zudem erlauben CAD-Programme eine sehr präzise Arbeitsweise, was bereits in der Planungsphase zu einer höheren Genauigkeit führt. Diese Präzision trägt dazu bei, Fehler während der Umsetzung zu reduzieren, wodurch Zeit und Kosten eingespart werden können. Darüber hinaus unterstützt die digitale Planung ein effizienteres und nachhaltigeres Arbeiten. 

[@CAD-Programme-ALLPLAN]

#### 2.3 Auswahl eines geeigneten CAD-Programms

Bei der Auswahl eines geeigneten CAD-Programms ist es wichtig, sich im Vorfeld Gedanken über die Komplexität des geplanten Projekts zu machen. Je nach Umfang und Detailgrad der Konstruktion werden unterschiedliche Funktionen und Werkzeuge benötigt, weshalb nicht jedes CAD-Programm für jedes Projekt gleichermaßen geeignet ist.

## 3 Elektronik

### 3.1 Grundlagen der Elektronik

Die Grundlagen der Elektronik beschäftigen sich damit, wie Strom und Spannung funktionieren und wie Bauteile wie Widerstände, Kondensatoren oder Transistoren in Schaltungen eingesetzt werden, um Geräte zu steuern oder Signale zu verarbeiten.

### 3.2 Überblick über elektronische Bauteile

Elektronische Bauteile sind einzelne Bestandteile, aus denen elektronische Schaltungen aufgebaut werden. Sie übernehmen unterschiedliche Aufgaben, wie das Steuern, Verarbeiten oder Speichern elektrischer Signale. Diese Bauteile bilden die Grundlage moderner elektronischer Systeme und kommen in zahlreichen technischen Anwendungen zum Einsatz, angefangen bei einfachen Alltagsgeräten bis hin zu komplexen elektronischen Systemen wie Computern oder automatisierten Anlagen. Man unterscheidet bei den jeweiligen Bauteil ob er Aktiv(Transistor, Diode) oder Passiv(Widerstand, Kondensator) ist. 

Der Unterschied zwischen diesen zwei Kategorien ist:

- Aktive Bauteile
  - Steuern oder verstärken den Stromfluss jedoch brauchen sie eine externe Energiequelle.
- Passive Bauteile
  - Beeinflussen den Stromfluss indem sie ihn regulieren, speichern oder verzögern ohne einer zusätzlichen externen Energiequelle.

[@Elektronische-Bauteile-HEINEN]

### 3.3 Strom, Spannung und Widerstand

#### Strom  

Elektrischer Strom bezeichnet den gerichteten Fluss von elektrischen Ladungsträgern, meist Elektronen, durch einen leitfähigen Werkstoff(Silber, Kupfer, Gold, Aluminium). Er stellt eine Form von Energie dar, mit der elektrische Geräte und Schaltungen betrieben werden können, welche allgemein als Verbraucher bezeichnet werden.
Die Stärke des elektrischen Stroms wird in der Einheit Ampere (A) gemessen. Aufgrund seiner vielseitigen Einsatzmöglichkeiten ist elektrischer Strom eine der am häufigsten genutzten Energieformen in technischen Systemen.

#### Spannung
Die elektrische Spannung beschreibt den Unterschied des elektrischen Potentials zwischen zwei Punkten in einer Schaltung. Sie ist dafür verantwortlich, dass elektrischer Strom überhaupt fließen kann. Die elektrische Spannung wird in der Einheit Volt (V) angegeben.
Als eine der grundlegenden Größen der Elektrotechnik spielt die Spannung eine zentrale Rolle bei der Berechnung von Stromstärke und elektrischem Widerstand. 

#### Widerstand
Der elektrische Widerstand beschreibt, wie stark der Stromfluss in einem Leiter oder Bauteil begrenzt wird. Er hängt von den Materialeigenschaften sowie von der Bauform des Leiters ab und bestimmt, wie leicht oder schwer sich elektrische Ladungen bewegen können.
Ein hoher Widerstand reduziert den Strom, während ein niedriger Widerstand einen stärkeren Stromfluss zulässt. Der elektrische Widerstand wird in der Einheit Ohm (Ω) angegeben. Widerstände werden gezielt als Bauteile eingesetzt, um den Strom zu begrenzen, treten jedoch auch unerwünscht in anderen elektronischen Komponenten auf und führen dort zu Energieverlusten.

[@Spannung-Strom-Widerstand-ElektronikKompendium]

### 3.4 Ohmsche Gesetz

![Ohmsche Gesetz[@Ohmsche-Gesetz-Bild]](img/URI.jpg)

Das Ohmsche Gesetz beschreibt den Zusammenhang zwischen elektrischer Spannung(U), Stromstärke(I) und Widerstand(R) in einem Stromkreis. Mithilfe dieser Beziehung lassen sich unbekannte Größen berechnen, wenn zwei der drei Werte bekannt sind.
Dieses Gesetz ist besonders wichtig für den praktischen Einsatz elektronischer Bauteile, da es hilft, den passenden Widerstand zu bestimmen. Wird ein Bauteil mit einer zu hohen Stromstärke betrieben, kann dies zu Beschädigungen oder zum Ausfall führen. Durch die richtige Berechnung lässt sich ein sicherer und zuverlässiger Betrieb gewährleisten. 

>Das Ohmsche Gesetz besagt, dass der Strom, der durch einen Widerstand fließt, direkt proportional zur angelegten Spannung und umgekehrt proportional zum Widerstand ist. Je höher die angelegte Spannung ist, desto größer ist der Strom. Aber je größer der Widerstand ist, desto geringer ist der Strom.[@Spannung-Strom-Widerstand-ElektronikKompendium]

Beim Rechnen mit dem Ohmschen Gesetz kann man sich merken, dass die elektrische Spannung (U) immer durch die Stromstärke (I) oder den Widerstand (R) geteilt wird. Die Stromstärke und der Widerstand stehen dabei in einer Multiplikationsbeziehung zueinander.

![Ohmsche Gesetz Rechnen[@Ohmsche-Gesetz-Rechnen-Bild]](img/ohms-law-triangle.svg)

### 3.5 Spannungsversorgung elektronischer Schaltungen

Die Spannungsversorgung ist ein grundlegender Bestandteil elektronischer Schaltungen. Ihre Aufgabe besteht darin, eine vorhandene Energiequelle, wie beispielsweise Netzstrom oder eine Batterie, in eine für die jeweilige Schaltung geeignete und möglichst konstante Gleichspannung umzuwandeln. Viele elektronische Bauteile benötigen feste Versorgungsspannungen, etwa 5 V oder 12 V, um zuverlässig arbeiten zu können. Dabei muss die Spannungsversorgung Schwankungen der Eingangsspannung sowie Änderungen der Stromaufnahme ausgleichen, damit die Ausgangsspannung stabil bleibt. [@Spannungsquellen-ElectronicsTutorials]

### Arten von Spannungsversorgungen
- Netzteile:
  - Ist ein Gerät, das den Strom aus der Steckdose in eine benutzbare Gleichspannung für elektronische Geräte umwandelt.
- Batterien/Akkus: 
  - Bieten mobile Gleichspannungen, die aber mit der Zeit schwanken.
- Generator:
  - Wandelt mechanische Energie in elektrischen Strom um.
- Konstantspannungsquellen: 
  - Versucht immer die gleiche Spannung am Ausgang zu liefern, egal wie sich Last oder Eingangsspannung verändert. 
[@Spannungsquellen-ElectronicsTutorials]

### Methoden zur Spannungsstabilisierung
- Z-Diode: 
  - Einfachste Methode, gut für geringe, konstante Ströme, aber mit höherem Spannungsabfall und Wärmeentwicklung bei höheren Strömen.
- Spannungsregler (IC): 
  - Integrierte Schaltungen (ICs), die eine sehr genaue und stabile Spannung liefern, auch mit Überstromschutz.
- Linearregler: 
  - Einfache Schaltung, oft mit einem Transistor, erzeugt wenig Rauschen, aber viel Wärme (Verlustleistung).
- Schaltregler: 
  - Effizienter, wandelt Spannung durch schnelles Schalten; heutzutage dominierend (z.B. in Schaltnetzteilen).
- Spannungsteiler (Widerstände): 
  - Nur für spezielle Fälle geeignet, wenn die Stromaufnahme konstant ist, da die Spannung mit abnehmender Batterie (oder steigender Last) abfällt. 
[@Schaltungstechnik-Stromversorgung-technik-reicke]

## 4 Mikrocontroller

### 4.1 Allgemeine Erklärung von Mikrocontrollern

Mikrocontroller, häufig auch als MCU (Microcontroller Unit) bezeichnet, sind sehr kompakte Recheneinheiten, bei denen alle wesentlichen Komponenten eines Computers auf einem einzigen Chip integriert sind. Dazu zählen unter anderem eine Recheneinheit, Speicher sowie Ein- und Ausgabeschnittstellen. Aufgrund dieses Aufbaus bilden Mikrocontroller ein vollständig in sich geschlossenes System.

Im Gegensatz zu klassischen Mikroprozessoren, wie sie in Personal Computern oder Tablets eingesetzt werden, sind Mikrocontroller für die Ausführung einer klar definierten Aufgabe vorgesehen. Sie führen meist ein einzelnes Programm dauerhaft und wiederholt aus, typischerweise in Form einer Endlosschleife. Solche Anwendungen werden als eingebettete Systeme bezeichnet. Durch ihre Spezialisierung eignen sich Mikrocontroller besonders für automatisierte Steuerungs- und Regelaufgaben. 

[@Mikrocontroller-RS]

### 4.2 Mikrocontroller Typen

Mikrocontroller lassen sich anhand ihrer Datenbreite in 8-Bit-, 16-Bit- und 32-Bit-Systeme einteilen. Diese Angabe beschreibt, wie viele Bits der Mikrocontroller in einem Verarbeitungsschritt verarbeiten kann und beeinflusst damit sowohl die Rechenleistung als auch die Geschwindigkeit.

8-Bit-Mikrocontroller werden häufig für einfache Anwendungen eingesetzt, da sie kostengünstig und energieeffizient sind, jedoch nur eine begrenzte Rechenleistung bieten. 16-Bit- und 32-Bit-Mikrocontroller ermöglichen komplexere Berechnungen und schnellere Verarbeitung, sind jedoch meist teurer. Die Wahl des passenden Mikrocontrollers hängt daher von den Anforderungen der jeweiligen Anwendung ab, etwa vom Funktionsumfang, der Rechengeschwindigkeit und den verfügbaren Programmiersprachen.

[@Mikrocontroller-RS]

### 4.3 Aufbau eines Mikrocontrollers

Ein Mikrocontroller setzt sich aus mehreren grundlegenden Komponenten zusammen, die gemeinsam ein vollständiges, eigenständiges System bilden. Jede dieser Komponenten übernimmt eine klar definierte Aufgabe und trägt zum reibungslosen Ablauf des gesamten Systems bei.

Die zentrale Recheneinheit eines Mikrocontrollers ist die CPU (Central Processing Unit). Sie kann als „Gehirn“ des Systems betrachtet werden und ist für das Ausführen von Programmbefehlen sowie für logische und mathematische Berechnungen zuständig.

Der Arbeitsspeicher, auch RAM (Random Access Memory) genannt, wird während der Programmausführung genutzt, um temporäre Daten zu speichern. Dieser Speicherinhalt geht beim Abschalten der Stromversorgung verloren und wird daher ausschließlich für laufende Berechnungen und Zwischenergebnisse verwendet.

Zusätzlich besitzt ein Mikrocontroller einen nichtflüchtigen Speicher, meist in Form von ROM oder Flash-Speicher. In diesem Speicher wird das Programm dauerhaft abgelegt, sodass es auch nach dem Ausschalten der Stromversorgung erhalten bleibt. Beim Start des Mikrocontrollers wird das Programm aus diesem Speicher geladen und ausgeführt.

Ein weiterer wichtiger Bestandteil ist der interne Oszillator. Dieser erzeugt den Takt für den Mikrocontroller und bestimmt, wie schnell die einzelnen Programmbefehle abgearbeitet werden. Die Taktfrequenz hat somit direkten Einfluss auf die Verarbeitungsgeschwindigkeit des Systems.

Über sogenannte Ein- und Ausgänge (Input/Output, kurz I/O) kann der Mikrocontroller mit seiner Umgebung kommunizieren. Diese Anschlüsse, meist als Pins ausgeführt, ermöglichen das Einlesen von Signalen von Sensoren sowie das Ansteuern von Aktoren wie LEDs oder Motoren.

Abhängig vom jeweiligen Mikrocontroller sind außerdem zusätzliche Peripherieeinheiten integriert. Dazu zählen unter anderem Timer und Zähler, Analog-Digital-Wandler zur Verarbeitung analoger Signale, Digital-Analog-Wandler sowie Module zur Pulsweitenmodulation (PWM). Diese erweitern die Einsatzmöglichkeiten des Mikrocontrollers und ermöglichen eine flexible Anpassung an unterschiedliche Anwendungen. 

[@Mikrocontroller-RS]

### 4.4 Funktionsweise eines Mikrocontrollers

Nach dem Einschalten eines Mikrocontrollers wird das im nichtflüchtigen Speicher abgelegte Programm geladen und von der CPU schrittweise ausgeführt. Während des Betriebs verarbeitet der Mikrocontroller eingehende Signale, beispielsweise von Sensoren oder Schaltern, und reagiert darauf durch das Ansteuern von Ausgängen wie LEDs, Motoren oder Relais.

Durch diese Arbeitsweise ist es möglich, einfache wie auch komplexere Steuerungsaufgaben zuverlässig und effizient umzusetzen. Mikrocontroller finden daher Anwendung in zahlreichen technischen Systemen, insbesondere dort, wo wiederholbare Prozesse automatisiert gesteuert werden müssen.

[@Mikrocontroller-RS]

### 4.5 Vergleich gängiger Mikrocontroller-Plattformen

---
#### Arduino Uno

![Arduino Uno[@Arduino-Uno-Bild]](img/Arduino-Uno-R3.jpg)

Der Arduino Uno ist einer der am häufigsten verwendeten Mikrocontroller und eignet sich besonders für Einsteiger sowie für einfache bis mittelkomplexe Projekte. Er basiert auf einem 8-Bit-Mikrocontroller und bietet eine übersichtliche Anzahl an digitalen und analogen Ein- und Ausgängen. Durch die einfache Programmierung und die große Verfügbarkeit an Bibliotheken und Beispielen lässt sich der Arduino Uno schnell in Betrieb nehmen. Er wird häufig für Steuerungsaufgaben, das Auslesen von Sensoren oder das Ansteuern von LEDs und anderen Aktoren verwendet. Aufgrund seiner Stabilität und guten Dokumentation ist er auch im schulischen Umfeld weit verbreitet.

---

#### Arduino Nano

![Arduino Nano[@Arduino-Nano-Bild]](img/Arduino-Nano.jpg)

Der Arduino Nano bietet im Wesentlichen denselben Funktionsumfang wie der Arduino Uno, ist jedoch deutlich kompakter aufgebaut. Dadurch eignet er sich besonders für Projekte, bei denen wenig Platz zur Verfügung steht. Trotz seiner geringen Größe kann der Arduino Nano für viele der gleichen Anwendungen eingesetzt werden wie der Uno. Er wird häufig in kleineren Schaltungen, Prototypen oder fest verbauten Systemen verwendet, bei denen eine platzsparende Bauform von Vorteil ist.

---

#### ESP32

![ESP32[@ESP32-Bild]](img/ESP32.jpg)

Der ESP32 ist ein leistungsstarker 32-Bit-Mikrocontroller, der sich vor allem durch seine integrierten Kommunikationsmöglichkeiten auszeichnet. Er verfügt über WLAN- und Bluetooth-Funktionalität und eignet sich daher besonders für vernetzte Anwendungen. Dank seiner höheren Rechenleistung und der Vielzahl an verfügbaren Schnittstellen kann der ESP32 mehrere Aufgaben gleichzeitig ausführen. Er wird häufig in Smart-Home-Anwendungen, IoT-Projekten oder Systemen eingesetzt, bei denen eine drahtlose Datenübertragung erforderlich ist. Zusätzlich bietet er Energiesparmodi, wodurch er auch für batteriebetriebene Anwendungen geeignet ist.

---

#### STM32

![STM32[@STM32-Bild]](img/STM32.jpg)

Die STM32-Mikrocontroller basieren auf einer 32-Bit-Architektur und sind in vielen unterschiedlichen Varianten erhältlich. Sie zeichnen sich durch hohe Leistungsfähigkeit, Flexibilität und einen professionellen Einsatzbereich aus. STM32-Controller werden häufig in industriellen Anwendungen, in der Automatisierungstechnik oder in technisch anspruchsvollen Projekten verwendet. Sie bieten umfangreiche Konfigurationsmöglichkeiten, zahlreiche Schnittstellen und eine hohe Rechengeschwindigkeit. Aufgrund ihrer Komplexität erfordern sie jedoch meist ein tieferes technisches Verständnis als einfache Arduino-Plattformen.


## 5 Verkabelung

### 5.1 Grundlagen der Verkabelung

Bei der Verkabelung elektronischer Bauteile müssen grundlegende Aspekte berücksichtigt werden, um die Sicherheit und Funktionsfähigkeit der Schaltung zu gewährleisten. Dazu gehört insbesondere die Begrenzung der Stromstärke, da überhöhte Ströme zu einer erhöhten Wärmeentwicklung in den Leitern führen können. Ebenso ist die Isolierung der Kabel entscheidend, um ungewollte Kurzschlüsse zwischen Leitern zu verhindern. Eine sorgfältige Planung und Ausführung der Verkabelung trägt somit wesentlich zur Zuverlässigkeit, Langlebigkeit und vor allem die Sicherheit der Schaltung bei.

### 5.2 Grundlagen elektrischer Schaltungen

#### Reihenschaltung

Bei einer Reihenschaltung werden mehrere Bauteile hintereinander geschaltet, sodass der gleiche Strom durch alle Bauteile fließt. Die Gesamtspannung der Spannungsquelle verteilt sich dabei auf die einzelnen Bauteile, abhängig von ihrem Widerstand.

![Reihenschaltung[@Reihenschaltung-Wikipedia]](img/Reihenschaltung.png)

[@Reihenschaltung-Wikipedia]

#### Parallelschaltung

Bei einer Parallelschaltung werden mehrere Bauteile so miteinander verbunden, dass jedes Bauteil direkt mit den gleichen beiden Klemmen der Spannungsquelle verbunden ist. Dadurch liegt an allen Bauteilen die gleiche Spannung an, während sich die Ströme auf die einzelnen Zweige aufteilen.

![Parallelschaltung[@Parallelschaltung-Wikipedia]](img/Parallelschaltung.png)

[@Parallelschaltung-Wikipedia]

#### Gemischte Schaltung

Eine gemischte Schaltung kombiniert Elemente einer Reihen- und Parallelschaltung, sodass einige Bauteile hintereinander und andere nebeneinander geschaltet sind. Dabei fließt der Strom durch die Reihenbauteile gleichmäßig, während die Spannung auf die Parallelelemente verteilt wird. Gemischte Schaltungen werden eingesetzt, wenn bestimmte Spannungs- oder Stromverhältnisse innerhalb einer Schaltung benötigt werden.

[@Gemischte-Schaltung-ElektronikKompendium]

### 5.3 Verbindungstechniken in der Elektronik

Verbindungstechniken in der Elektronik umfassen lösbare und nicht lösbare Methoden wie Löten (Bauteile auf Platinen), Crimpen (Pressen von Leitern in Verbinder), Schraubanschlüsse (einfach, wiederlösbar), Schneidklemmen (Isolierung wird durchtrennt) und Käfigzugfederklemmen (vibrationssicher). Wichtig sind auch Steckverbinder, Bonding (auf Mikroebene), Kleben mit Leitkleber und spezielle Techniken wie das Spleißen für Glasfasern, um zuverlässige Verbindungen für Strom und Daten zu gewährleisten. 
Nicht lösbare Verbindungen

### 5.4 Löten von Bauteilen

Löten ist ein Verfahren zur dauerhaften Verbindung von Metallteilen, insbesondere in der Elektronik. Dabei wird ein Lötmaterial (Lötzinn) auf die zu verbindende Stelle aufgebracht und durch Erwärmen mit einem Lötkolben geschmolzen. Nach dem Abkühlen härtet das Lötzinn aus und bildet eine mechanisch stabile und elektrisch leitfähige Verbindung zwischen den Bauteilen.

Dieses Verfahren wird insbesondere bei der Durchsteckmontage (THT) und der Oberflächenmontage (SMD) von Bauteilen auf Leiterplatten eingesetzt, da es präzise und zuverlässig ist und die Bauteile nur minimal thermisch belastet.
[@Richtig-löten-Hornbach]

### 5.5 Crimpen von Kabeln

Crimpen bezeichnet das Verfahren, bei dem ein Kabel mit einem Steckverbinder verbunden wird. Dabei wird zunächst ein Stück der Kabelisolierung entfernt, sodass die einzelnen Leiter freigelegt sind. Die freigelegten Drähte werden anschließend in einen Kontakt(z.B Aderendhülse) eingeführt und mit einer Crimpzange zusammengepresst. Abschließend wird ein Kunststoffkopf aufgebracht, der die Verbindung schützt und stabilisiert. 
[@Richtig-Crimpen-Jungheinrich-PROFISHOP]

![Crimpen[@Crimpen-Anleitung-Conrad]](img/korrekte-crimpverbindung.jpg)

>Bei einer korrekten Ausführung müssen an Punkt 1 die Litzendrähte und die Isolierung sichtbar sein. An Punkt 2 müssen die Drahtenden sichtbar sein.
[@Crimpen-Anleitung-Conrad]

### 5.6 Schaltplan

Ein Schaltplan ist eine grafische Darstellung einer elektrischen oder elektronischen Schaltung, die es ermöglicht, die Verbindungen zwischen Bauteilen klar zu erkennen. Er zeigt auf, wie Komponenten wie Widerstände, Kondensatoren, Mikrocontroller oder Sensoren elektrisch miteinander verbunden sind, und dient damit als übersichtliche Orientierung für Aufbau und Analyse der Schaltung.

Darüber hinaus werden Schaltpläne häufig als Grundlage für das Layout von Leiterplatten (PCB) verwendet. Da Leiterplatten sehr komplex sein können, erlaubt der Schaltplan, alle Verbindungen und Bauteilpositionen präzise zu planen, bevor die Leiterplatte gefertigt wird. Auf diese Weise dient er sowohl der Dokumentation als auch der fehlerfreien Umsetzung eines Projekts.

[@Schaltplan-Wikipedia]


## 6 Sensoren und Aktoren

Sensoren und Aktoren bilden zentrale Bestandteile automatisierter und elektronischer Systeme. Sie ermöglichen es technischen Systemen, Informationen aus ihrer Umgebung aufzunehmen und darauf gezielt zu reagieren. Sensoren übernehmen dabei die Aufgabe der Datenerfassung, während Aktoren für die Umsetzung von Aktionen verantwortlich sind. Man kann Sensoren als Eingabeelemente und Aktoren als Ausgabeelemente eines Systems verstehen.

[@Sensorik-und-Aktorik-StudySmarter]

### 6.1 Sensoren – Funktionsweise und Einsatzgebiete

Sensoren dienen dazu, physikalische oder chemische Größen aus der Umgebung zu erfassen und diese in elektrische Signale umzuwandeln. Diese Signale können anschließend von einem Mikrocontroller oder einem anderen elektronischen System verarbeitet werden. Dadurch ist es möglich, Zustände wie Temperatur, Licht oder Feuchtigkeit digital auszuwerten.

Typische Sensoren kommen in vielen technischen Anwendungen zum Einsatz. Ein Temperatursensor misst beispielsweise die Umgebungstemperatur, ein Lichtsensor erfasst die Helligkeit, und ein Feuchtigkeitssensor bestimmt den Feuchtigkeitsgehalt der Luft oder eines Materials.

Je nach Messgröße lassen sich Sensoren in verschiedene Kategorien einteilen. Häufig verwendete Sensortypen sind Temperatursensoren zur Erfassung von Wärme, Lichtsensoren zur Messung von Helligkeit, Drucksensoren zur Erkennung von Kraft- oder Druckänderungen sowie Bewegungssensoren, die Bewegungen oder Beschleunigungen wahrnehmen. Alle diese Sensoren haben gemeinsam, dass sie physikalische Informationen in elektrische Signale umwandeln, die weiterverarbeitet werden können.

[@Sensorik-und-Aktorik-StudySmarter]

### 6.2 Aktoren – Funktionsweise und Einsatzgebiete

Aktoren übernehmen die Aufgabe, elektrische Signale in eine physische Aktion umzusetzen. Sie reagieren auf Steuerbefehle eines Mikrocontrollers oder eines anderen Systems und führen daraufhin eine Bewegung oder eine andere gewünschte Funktion aus. Während Sensoren Informationen liefern, sorgen Aktoren dafür, dass auf diese Informationen reagiert wird.

Zu den häufig eingesetzten Aktoren zählen unter anderem Elektromotoren, die mechanische Bewegung erzeugen, Lautsprecher, die elektrische Signale in Schall umwandeln, sowie Leuchtdioden (LEDs), die durch elektrische Ansteuerung Licht aussenden. Aktoren spielen eine entscheidende Rolle in automatisierten Systemen, da sie digitale Steuerbefehle in reale Vorgänge umsetzen.

Ein funktionierendes Zusammenspiel zwischen Sensoren und Aktoren ist Voraussetzung dafür, dass Systeme selbstständig und zielgerichtet arbeiten können. Nur wenn Sensordaten korrekt ausgewertet werden, können Aktoren die passenden Aktionen ausführen.

[@Sensorik-und-Aktorik-StudySmarter]


### 6.3 Wie Sensoren und Aktoren Zusammenarbeiten

Das Zusammenwirken von Sensoren und Aktoren erfolgt meist in einem wiederkehrenden Ablauf. Zunächst erfassen Sensoren Daten aus der Umgebung. Diese Informationen werden anschließend verarbeitet und ausgewertet, um eine Entscheidung zu treffen. Auf Basis dieser Entscheidung wird schließlich ein Aktor angesteuert, der eine entsprechende Aktion ausführt.

Ein einfaches Beispiel für diesen Ablauf ist ein automatisches Bewässerungssystem. Ein Feuchtigkeitssensor misst den Feuchtigkeitsgehalt des Bodens. Sinkt dieser unter einen festgelegten Wert, wird ein Signal ausgelöst. Daraufhin öffnet ein elektronisch gesteuertes Ventil und startet die Bewässerung.

Damit solche Systeme zuverlässig funktionieren, ist eine sorgfältige Programmierung und Abstimmung der Sensoren und Aktoren notwendig. Nur durch genaue Messungen und präzise Steuerung können automatisierte Systeme korrekt und effizient auf Veränderungen ihrer Umgebung reagieren.

[@Sensorik-und-Aktorik-StudySmarter]


## Praktische Arbeit

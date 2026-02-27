# Teilaufgabe Schüler Beichtbuchner
\textauthor{Christian Josef Beichtbucher}

## Theorie

### Einordnung des Aufgabenbereichs
Mein Teil der Diplomarbeit ist es ein Haus zu modellieren um dieses anschließend mit Sensoren und Aktoren auszustatten. Der Plan ist es ein bereits bestehendes Haus nachzubauen, um es so Real wie möglich zu halten. Das Haus wird mithilfe von Online Downloadbaren Möbel eingerichtet und der Garten wird auf die gleiche weise angedeutet und dekoriert. Vorgesehene ansteuerbare Elemente sind LEDs sowie auch eine Wetterstation welche wir im Unterricht schon gebaut und Programmiert haben. 

## Modellierung

### Grundlagen der 3D-Modellierung

Unter 3D-Modellierung versteht man die digitale Erstellung dreidimensionaler Objekte mit spezieller Software. Dabei werden geometrische Elemente wie Punkte, Linien und Flächen verwendet, um virtuelle Modelle mit räumlicher Ausdehnung zu erzeugen. Diese Modelle besitzen neben Länge und Breite auch eine Tiefe und können dadurch realitätsnah dargestellt und weiterverarbeitet werden. 
[@3D-Modellierung-Adobe]

### Ablauf der 3D-Modellierung  

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

### Arbeiten mit Skizzen

Bevor ein dreidimensionales Objekt erstellt werden kann, wird in der Regel zunächst eine zweidimensionale Skizze angefertigt. Diese Skizze dient als Grundlage für die spätere Modellierung und definiert die Form sowie die grundlegenden Abmessungen des Objekts. Anschließend wird die 2D-Geometrie in die dritte Dimension überführt, indem sie entlang einer Achse extrudiert oder auf andere Weise räumlich erweitert wird. Auf diese Weise entsteht ein Volumenkörper, der anschließend weiterbearbeitet, verfeinert und an die gewünschten Anforderungen angepasst werden kann. 

![Skizze](img/bilder-ausarbeitung-Beichtbuchner/3D-Modellierung/Skizze.png)

### Volumen- und Flächenmodellierung

In CAD-Programmen stehen zahlreiche Werkzeuge zur Verfügung, mit denen dreidimensionale Objekte erstellt und weiterbearbeitet werden können. Diese Werkzeuge ermöglichen es, Körper zu erweitern, Material gezielt zu entfernen oder Öffnungen und Aussparungen zu erzeugen. Typische Bearbeitungsschritte sind beispielsweise das Hinzufügen von Volumen, das Ausschneiden von Bereichen oder das Erstellen von Bohrungen.

![Würfel](img/bilder-ausarbeitung-Beichtbuchner/3D-Modellierung/Wuerfel.png)

Bei der Volumenmodellierung arbeitet man mit geschlossenen Körpern, die ein klares Innenvolumen haben. Dadurch lassen sich Bauteile genau konstruieren, und man kann zum Beispiel ihr Gewicht, Material oder ihre Stabilität berechnen. Diese Methode eignet sich besonders für technische Teile, weil sie eine stabile und verlässliche Form liefert.

Die Flächenmodellierung arbeitet dagegen nur mit einzelnen Oberflächen, ohne dass ein richtiges Volumen entsteht. Sie wird oft für komplexe oder organische Formen genutzt, wie sie etwa in der Automobil- oder Flugzeuggestaltung vorkommen. Mit dieser Methode lassen sich sehr detaillierte und geschwungene Formen erstellen, allerdings muss man genau auf die Übergänge zwischen den Flächen achten, damit das Modell sauber bleibt. 

### Strukturierung komplexer Modelle

Die Strukturierung komplexer CAD-Modelle ist ein wesentlicher Bestandteil einer übersichtlichen und wartbaren Konstruktion. Um auch umfangreiche Modelle nachvollziehbar zu halten, werden unterschiedliche Modellierungsstrategien eingesetzt. Eine klare Gliederung erleichtert nicht nur die Bearbeitung, sondern ermöglicht auch spätere Änderungen und Erweiterungen ohne großen Mehraufwand.

Ein häufig verwendeter Ansatz ist das sogenannte Top-Down-Design. Dabei wird zunächst eine übergeordnete Struktur, oft als „Skelettmodell“ bezeichnet, erstellt, welche die grundlegenden Abmessungen und Referenzen vorgibt. Einzelne Bauteile werden anschließend auf Basis dieses Skeletts modelliert. Änderungen an den zentralen Vorgaben wirken sich automatisch auf alle abhängigen Komponenten aus, wodurch sich dieser Ansatz besonders für flexible und anpassbare Konstruktionen eignet.

Im Gegensatz dazu steht das Bottom-Up-Design. Hier werden einzelne Bauteile unabhängig voneinander modelliert und anschließend zu einer Baugruppe zusammengefügt. Diese Vorgehensweise ist besonders sinnvoll, wenn standardisierte oder wiederverwendbare Teile eingesetzt werden. Änderungen an der Gesamtstruktur erfordern jedoch meist eine manuelle Anpassung der einzelnen Komponenten.

Ergänzend dazu spielt die parametrische Modellierung eine zentrale Rolle bei der Strukturierung komplexer Modelle. Durch die Definition von Parametern, Beziehungen und Abhängigkeiten können Änderungen gezielt und konsistent umgesetzt werden, ohne dass das Modell vollständig neu erstellt werden muss.

Zusätzlich tragen eine sinnvolle Unterteilung in Baugruppen, eine klare Benennung von Bauteilen sowie eine logische Organisation von Ebenen und Referenzen wesentlich zur Übersichtlichkeit bei. Der gezielte Einsatz spezieller Modellierungsfunktionen, wie etwa Splines oder Flächenbefehle für organische Geometrien, unterstützt die Umsetzung komplexer Formen und erhöht die Flexibilität bei der Modellierung.

### Verwendung externer Modelle und Bibliotheken

Neben der eigenen Modellierung besteht die Möglichkeit, auf externe 3D-Modelle und Bibliotheken zurückzugreifen, die von anderen Personen oder Organisationen online zur Verfügung gestellt werden. Solche Modelle umfassen beispielsweise Möbel, Bedienelemente wie Taster oder Knöpfe sowie weitere funktionale oder dekorative Bauteile.

Der Einsatz externer Modelle kann den Modellierungsprozess deutlich beschleunigen, da häufig verwendete oder standardisierte Objekte nicht vollständig neu erstellt werden müssen. Diese Modelle können in das eigene CAD-Projekt importiert und bei Bedarf angepasst oder weiterverarbeitet werden.

Solche Modelle eignen sich auch für die physische Umsetzung mithilfe eines 3D-Druckers. Dabei können heruntergeladene Modelle ausgedruckt und anschließend in ein Projekt integriert werden. Voraussetzung hierfür ist jedoch, dass die Modelle korrekt skaliert sind und den technischen Anforderungen des jeweiligen Druckverfahrens entsprechen. Durch den gezielten Einsatz externer Modelle lässt sich der Arbeitsaufwand reduzieren, während gleichzeitig ein hoher Detailgrad erreicht werden kann. 

## CAD-Programme

### CAD-Programme im Überblick

CAD-Programme sind spezielle Softwareprogramme, die zur Erstellung und Bearbeitung von digitalen Zeichnungen und Modellen verwendet werden. Sie helfen dabei, technische Entwürfe übersichtlich und präzise darzustellen und dienen als wichtige Grundlage für die weitere Planung und Umsetzung.

>CAD-Programme werden in der Architektur, im Ingenieurwesen und im Baugewerbe eingesetzt, um Projekte zu entwerfen und Konstruktionsunterlagen, wie z. B. Konstruktions- und Fertigungszeichnungen, zu erstellen. 

[@CAD-Programme-ALLPLAN]

#### Allgemeine Funktionsweise von CAD-Programmen

CAD ist die Abkürzung für computergestütztes Zeichnen bzw. computergestütztes Entwerfen. Während Bau- und Konstruktionszeichnungen früher manuell auf Papier erstellt wurden, werden diese Aufgaben heute größtenteils mithilfe spezieller Software durchgeführt. CAD-Programme ermöglichen es, Entwürfe digital zu erstellen und sowohl in zweidimensionaler als auch in dreidimensionaler Form darzustellen. Dadurch können Zeichnungen ausgedruckt oder digitale 3D-Modelle weiterverwendet und geteilt werden.

Der Einsatz von CAD-Software erleichtert es, unterschiedliche Entwurfsvarianten zu vergleichen und komplexe Konstruktionen anschaulich darzustellen. Zudem erlauben CAD-Programme eine sehr präzise Arbeitsweise, was bereits in der Planungsphase zu einer höheren Genauigkeit führt. Diese Präzision trägt dazu bei, Fehler während der Umsetzung zu reduzieren, wodurch Zeit und Kosten eingespart werden können. Darüber hinaus unterstützt die digitale Planung ein effizienteres und nachhaltigeres Arbeiten. 

[@CAD-Programme-ALLPLAN]

#### Auswahl eines geeigneten CAD-Programms

Bei der Auswahl eines geeigneten CAD-Programms ist es wichtig, sich im Vorfeld Gedanken über die Komplexität des geplanten Projekts zu machen. Je nach Umfang und Detailgrad der Konstruktion werden unterschiedliche Funktionen und Werkzeuge benötigt, weshalb nicht jedes CAD-Programm für jedes Projekt gleichermaßen geeignet ist.

## 3D-Druck

### Grundlagen des 3D-Drucks  

Beim 3D-Druck handelt es sich um ein modernes Fertigungsverfahren, bei dem reale Gegenstände direkt aus digitalen 3D-Modellen hergestellt werden. Anstatt Material aus einem festen Werkstück zu entfernen, wird das Bauteil von Grund auf neu aufgebaut. Der Drucker erzeugt das Objekt dabei Schritt für Schritt, indem er Material in sehr dünnen Lagen aufträgt und diese übereinanderlegt. Die Form des Objekts ergibt sich aus einer zuvor erstellten digitalen Vorlage, die dem Drucker genau vorgibt, wo und wie viel Material benötigt wird. Häufig wird ein Kunststoff verwendet, der erhitzt und anschließend gezielt abgelegt wird, bis am Ende ein vollständiges dreidimensionales Bauteil entsteht.

[@3D-Printing-Grundlagen-Autodesk]

### Vorbereitung der Modelle

Die Vorbereitung eines 3D-Modells für den Druck beginnt mit der Überprüfung der Geometrie. Ein druckbares Modell muss ein geschlossenes Volumen besitzen, frei von offenen Kanten oder Löchern sein und die gewünschten Abmessungen korrekt wiedergeben. Zusätzlich ist darauf zu achten, dass filigrane Strukturen und Überhänge stabil genug sind, um während des Drucks nicht zu brechen oder zu verziehen.

Nach der geometrischen Kontrolle erfolgt der Export des Modells in ein für 3D-Drucker geeignetes Format, wie STL, OBJ oder 3MF. Diese Formate repräsentieren das Modell als Netz aus Dreiecken, das vom Slicer verarbeitet werden kann. Dabei muss die Mesh-Auflösung so gewählt werden, dass Details erhalten bleiben, während die Dateigröße handhabbar bleibt. Die korrekte Ausrichtung des Modells auf dem Druckbett wird bereits bei diesem Schritt berücksichtigt, um eine optimale Platzierung im Slicer zu ermöglichen.

[@3D-Printing-FreeCAD]

### Slicing

Der Slicer übersetzt das digitale Modell in druckbare Anweisungen für den 3D-Drucker. Dabei wird das Objekt in horizontale Schichten zerlegt, die vom Drucker nacheinander aufgebaut werden. Außerdem berechnet der Slicer die Innenstruktur, das sogenannte Infill, sowie gegebenenfalls Stützstrukturen für Überhänge.

Darüber hinaus werden alle relevanten Druckparameter festgelegt, darunter Materialwahl, Schichthöhe, Druckgeschwindigkeit und Temperatur. Moderne Slicer, wie beispielsweise Bambu Studio, automatisieren viele dieser Schritte und ermöglichen eine präzise Vorschau des Druckvorgangs. Bambu Studio veranschaulicht, wie ein Slicer das Modell analysiert, die Schichten erzeugt und den G-Code generiert, der anschließend vom Drucker interpretiert wird. Auf diese Weise wird sichergestellt, dass das digitale Modell korrekt und mit den gewünschten Eigenschaften in ein physisches Objekt umgesetzt werden kann.

[@3D-Printing-FreeCAD]

### Druckprozess und Einstellungen  

Der 3D-Druckprozess wird stark von den gewählten Parametern beeinflusst, die bestimmen, wie das Modell Schicht für Schicht aufgebaut wird. Ein entscheidender Faktor ist die Layerhöhe, also die Dicke jeder einzelnen Schicht. Dünnere Schichten erzeugen feinere Oberflächen, verlängern aber die Druckzeit, während dickere Schichten schneller gedruckt werden und sichtbare Schichtraster hinterlassen. Auch die Anzahl der oberen und unteren Schichten sowie die Dicke der Außenwände beeinflussen Stabilität und Formtreue des Bauteils.

Ebenso wichtig ist die Haftung des Modells auf dem Druckbett, die durch unterschiedliche Methoden wie *Skirt*, *Brim* oder *Raft* optimiert werden kann. Die innere Struktur, das Infill, legt fest, wie fest und schwer das Bauteil ist. Überhänge werden durch Stützstrukturen (Supports) stabilisiert, die nach dem Druck wieder entfernt werden.

Weitere Parameter, die den Druckprozess beeinflussen, sind unter anderem die Druckgeschwindigkeit, die Düsen- und Bett-Temperatur, die Geschwindigkeit der ersten Schicht und die Kühlung der Schichten. All diese Einstellungen werden im Slicer definiert, der anschließend den G-Code erzeugt, der den Drucker steuert.

Wichtige Einstellungen im Überblick:

- **Layerhöhe:** Dicke jeder Schicht, beeinflusst Oberfläche und Druckzeit  
- **Perimeter Shells:** Anzahl und Dicke der Außenwände für Stabilität  
- **Top/Bottom Solid Layers:** Anzahl der geschlossenen oberen und unteren Schichten  
- **Infill:** Muster und Füllgrad für Festigkeit und Gewicht  
- **Support:** Stützstrukturen für Überhänge  
- **Druckbett- und Düsentemperatur:** Optimiert Haftung und Materialfluss  
- **Druckgeschwindigkeit & erste Schichtgeschwindigkeit:** Beeinflussen Genauigkeit und Haftung

### Nachbearbeitung und Integration ins Projekt

Nach dem 3D-Druck eines Bauteils folgt die Phase der Nachbearbeitung, in der das gedruckte Objekt gezielt optimiert wird, um Oberflächenqualität, Funktionalität und Einsatzfähigkeit zu verbessern. Da 3D‑gedruckte Teile schichtweise aufgebaut werden, weisen sie meist sichtbare Schichtrasterungen auf. Zudem entstehen an Stellen, an denen Stützstrukturen verwendet wurden, kleine Unebenheiten. Diese Merkmale werden während der Nachbearbeitung gezielt korrigiert, um die Bauteile an die Anforderungen ihres späteren Einsatzes anzupassen.

Ein zentraler Bestandteil der Nachbearbeitung ist das Entfernen von Stützstrukturen, die während des Drucks zur Stabilisierung von Überhängen oder komplexen Geometrien eingesetzt wurden. Nach dem Abtrennen der Supports bleiben häufig kleine Kanten oder Unebenheiten zurück, die durch weitere Verfahren geglättet werden. Darüber hinaus kommen unterschiedliche Techniken zum Einsatz, um Oberflächen zu veredeln, mechanische Eigenschaften zu verbessern oder zusätzliche Funktionen zu ermöglichen. Diese Verfahren lassen sich grundsätzlich in subtraktive, additive und stoffverändernde Methoden einteilen, die jeweils unterschiedliche Herangehensweisen verfolgen, aber alle darauf abzielen, das gedruckte Bauteil für die Integration in ein größeres Projekt vorzubereiten.

Subtraktive Methoden basieren auf dem gezielten Entfernen von Material, beispielsweise durch Schleifen, Polieren, Sandstrahlen oder maschinelle Bearbeitung. Sie glätten Schichtrasterungen und korrigieren lokale Unebenheiten. Additive Verfahren fügen Material hinzu, etwa durch Spachtelmasse oder Beschichtungen, um Oberflächen auszugleichen oder die strukturellen Eigenschaften zu verbessern. Stoffverändernde Methoden wirken durch chemische oder thermische Behandlung auf das Material ein, wodurch glattere Oberflächen oder eine erhöhte Festigkeit erzielt werden können.

Nach der Nachbearbeitung können die 3D-Druckteile auf vielfältige Weise in ein übergeordnetes Projekt integriert werden. Sie eignen sich als Bestandteile größerer Baugruppen, als funktionale Prototypen oder als fertige Bauteile für Endprodukte. Durch diese Verfahren wird sichergestellt, dass die gedruckten Komponenten sowohl technisch als auch ästhetisch den Anforderungen des jeweiligen Einsatzbereichs entsprechen – sei es im industriellen Umfeld, im Prototypenbau oder in der Fertigung individueller Objekte.

[@3D-Printing-BigRep]

## Elektronik

### Grundlagen der Elektronik

Die Grundlagen der Elektronik beschäftigen sich damit, wie Strom und Spannung funktionieren und wie Bauteile wie Widerstände, Kondensatoren oder Transistoren in Schaltungen eingesetzt werden, um Geräte zu steuern oder Signale zu verarbeiten.

### Überblick über elektronische Bauteile

Elektronische Bauteile sind einzelne Bestandteile, aus denen elektronische Schaltungen aufgebaut werden. Sie übernehmen unterschiedliche Aufgaben, wie das Steuern, Verarbeiten oder Speichern elektrischer Signale. Diese Bauteile bilden die Grundlage moderner elektronischer Systeme und kommen in zahlreichen technischen Anwendungen zum Einsatz, angefangen bei einfachen Alltagsgeräten bis hin zu komplexen elektronischen Systemen wie Computern oder automatisierten Anlagen. Man unterscheidet bei den jeweiligen Bauteil ob er Aktiv(Transistor, Diode) oder Passiv(Widerstand, Kondensator) ist. 

Der Unterschied zwischen diesen zwei Kategorien ist:

- Aktive Bauteile
  - Steuern oder verstärken den Stromfluss jedoch brauchen sie eine externe Energiequelle.
- Passive Bauteile
  - Beeinflussen den Stromfluss indem sie ihn regulieren, speichern oder verzögern ohne einer zusätzlichen externen Energiequelle.

[@Elektronische-Bauteile-HEINEN]

### Spannungsversorgung elektronischer Schaltungen

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

## Mikrocontroller

### Allgemeine Erklärung von Mikrocontrollern

Mikrocontroller, häufig auch als MCU (Microcontroller Unit) bezeichnet, sind sehr kompakte Recheneinheiten, bei denen alle wesentlichen Komponenten eines Computers auf einem einzigen Chip integriert sind. Dazu zählen unter anderem eine Recheneinheit, Speicher sowie Ein- und Ausgabeschnittstellen. Aufgrund dieses Aufbaus bilden Mikrocontroller ein vollständig in sich geschlossenes System.

Im Gegensatz zu klassischen Mikroprozessoren, wie sie in Personal Computern oder Tablets eingesetzt werden, sind Mikrocontroller für die Ausführung einer klar definierten Aufgabe vorgesehen. Sie führen meist ein einzelnes Programm dauerhaft und wiederholt aus, typischerweise in Form einer Endlosschleife. Solche Anwendungen werden als eingebettete Systeme bezeichnet. Durch ihre Spezialisierung eignen sich Mikrocontroller besonders für automatisierte Steuerungs- und Regelaufgaben. 

[@Mikrocontroller-RS]

### Mikrocontroller Typen

Mikrocontroller lassen sich anhand ihrer Datenbreite in 8-Bit-, 16-Bit- und 32-Bit-Systeme einteilen. Diese Angabe beschreibt, wie viele Bits der Mikrocontroller in einem Verarbeitungsschritt verarbeiten kann und beeinflusst damit sowohl die Rechenleistung als auch die Geschwindigkeit.

8-Bit-Mikrocontroller werden häufig für einfache Anwendungen eingesetzt, da sie kostengünstig und energieeffizient sind, jedoch nur eine begrenzte Rechenleistung bieten. 16-Bit- und 32-Bit-Mikrocontroller ermöglichen komplexere Berechnungen und schnellere Verarbeitung, sind jedoch meist teurer. Die Wahl des passenden Mikrocontrollers hängt daher von den Anforderungen der jeweiligen Anwendung ab, etwa vom Funktionsumfang, der Rechengeschwindigkeit und den verfügbaren Programmiersprachen.

[@Mikrocontroller-RS]

### Aufbau eines Mikrocontrollers

Ein Mikrocontroller setzt sich aus mehreren grundlegenden Komponenten zusammen, die gemeinsam ein vollständiges, eigenständiges System bilden. Jede dieser Komponenten übernimmt eine klar definierte Aufgabe und trägt zum reibungslosen Ablauf des gesamten Systems bei.

Die zentrale Recheneinheit eines Mikrocontrollers ist die CPU (Central Processing Unit). Sie kann als „Gehirn“ des Systems betrachtet werden und ist für das Ausführen von Programmbefehlen sowie für logische und mathematische Berechnungen zuständig.

Der Arbeitsspeicher, auch RAM (Random Access Memory) genannt, wird während der Programmausführung genutzt, um temporäre Daten zu speichern. Dieser Speicherinhalt geht beim Abschalten der Stromversorgung verloren und wird daher ausschließlich für laufende Berechnungen und Zwischenergebnisse verwendet.

Zusätzlich besitzt ein Mikrocontroller einen nichtflüchtigen Speicher, meist in Form von ROM oder Flash-Speicher. In diesem Speicher wird das Programm dauerhaft abgelegt, sodass es auch nach dem Ausschalten der Stromversorgung erhalten bleibt. Beim Start des Mikrocontrollers wird das Programm aus diesem Speicher geladen und ausgeführt.

Ein weiterer wichtiger Bestandteil ist der interne Oszillator. Dieser erzeugt den Takt für den Mikrocontroller und bestimmt, wie schnell die einzelnen Programmbefehle abgearbeitet werden. Die Taktfrequenz hat somit direkten Einfluss auf die Verarbeitungsgeschwindigkeit des Systems.

Über sogenannte Ein- und Ausgänge (Input/Output, kurz I/O) kann der Mikrocontroller mit seiner Umgebung kommunizieren. Diese Anschlüsse, meist als Pins ausgeführt, ermöglichen das Einlesen von Signalen von Sensoren sowie das Ansteuern von Aktoren wie LEDs oder Motoren.

Abhängig vom jeweiligen Mikrocontroller sind außerdem zusätzliche Peripherieeinheiten integriert. Dazu zählen unter anderem Timer und Zähler, Analog-Digital-Wandler zur Verarbeitung analoger Signale, Digital-Analog-Wandler sowie Module zur Pulsweitenmodulation (PWM). Diese erweitern die Einsatzmöglichkeiten des Mikrocontrollers und ermöglichen eine flexible Anpassung an unterschiedliche Anwendungen. 

[@Mikrocontroller-RS]

### Funktionsweise eines Mikrocontrollers

Nach dem Einschalten eines Mikrocontrollers wird das im nichtflüchtigen Speicher abgelegte Programm geladen und von der CPU schrittweise ausgeführt. Während des Betriebs verarbeitet der Mikrocontroller eingehende Signale, beispielsweise von Sensoren oder Schaltern, und reagiert darauf durch das Ansteuern von Ausgängen wie LEDs, Motoren oder Relais.

Durch diese Arbeitsweise ist es möglich, einfache wie auch komplexere Steuerungsaufgaben zuverlässig und effizient umzusetzen. Mikrocontroller finden daher Anwendung in zahlreichen technischen Systemen, insbesondere dort, wo wiederholbare Prozesse automatisiert gesteuert werden müssen.

[@Mikrocontroller-RS]

### Vergleich gängiger Mikrocontroller-Plattformen

***
#### Arduino Uno

![Arduino Uno[@Arduino-Uno-Bild]](img/bilder-ausarbeitung-Beichtbuchner/Mikrocontroller/Arduino-Uno-R3.jpg)

Der Arduino Uno ist einer der am häufigsten verwendeten Mikrocontroller und eignet sich besonders für Einsteiger sowie für einfache bis mittelkomplexe Projekte. Er basiert auf einem 8-Bit-Mikrocontroller und bietet eine übersichtliche Anzahl an digitalen und analogen Ein- und Ausgängen. Durch die einfache Programmierung und die große Verfügbarkeit an Bibliotheken und Beispielen lässt sich der Arduino Uno schnell in Betrieb nehmen. Er wird häufig für Steuerungsaufgaben, das Auslesen von Sensoren oder das Ansteuern von LEDs und anderen Aktoren verwendet. Aufgrund seiner Stabilität und guten Dokumentation ist er auch im schulischen Umfeld weit verbreitet.

***

#### Arduino Nano

![Arduino Nano[@Arduino-Nano-Bild]](img/bilder-ausarbeitung-Beichtbuchner/Mikrocontroller/Arduino-Nano.jpg)

Der Arduino Nano bietet im Wesentlichen denselben Funktionsumfang wie der Arduino Uno, ist jedoch deutlich kompakter aufgebaut. Dadurch eignet er sich besonders für Projekte, bei denen wenig Platz zur Verfügung steht. Trotz seiner geringen Größe kann der Arduino Nano für viele der gleichen Anwendungen eingesetzt werden wie der Uno. Er wird häufig in kleineren Schaltungen, Prototypen oder fest verbauten Systemen verwendet, bei denen eine platzsparende Bauform von Vorteil ist.

***

#### ESP32

![ESP32[@ESP32-Bild]](img/bilder-ausarbeitung-Beichtbuchner/Mikrocontroller/ESP32.jpg)

Der ESP32 ist ein leistungsstarker 32-Bit-Mikrocontroller, der sich vor allem durch seine integrierten Kommunikationsmöglichkeiten auszeichnet. Er verfügt über WLAN- und Bluetooth-Funktionalität und eignet sich daher besonders für vernetzte Anwendungen. Dank seiner höheren Rechenleistung und der Vielzahl an verfügbaren Schnittstellen kann der ESP32 mehrere Aufgaben gleichzeitig ausführen. Er wird häufig in Smart-Home-Anwendungen, IoT-Projekten oder Systemen eingesetzt, bei denen eine drahtlose Datenübertragung erforderlich ist. Zusätzlich bietet er Energiesparmodi, wodurch er auch für batteriebetriebene Anwendungen geeignet ist.

***

#### STM32

![STM32[@STM32-Bild]](img/bilder-ausarbeitung-Beichtbuchner/Mikrocontroller/STM32.jpg)

Die STM32-Mikrocontroller basieren auf einer 32-Bit-Architektur und sind in vielen unterschiedlichen Varianten erhältlich. Sie zeichnen sich durch hohe Leistungsfähigkeit, Flexibilität und einen professionellen Einsatzbereich aus. STM32-Controller werden häufig in industriellen Anwendungen, in der Automatisierungstechnik oder in technisch anspruchsvollen Projekten verwendet. Sie bieten umfangreiche Konfigurationsmöglichkeiten, zahlreiche Schnittstellen und eine hohe Rechengeschwindigkeit. Aufgrund ihrer Komplexität erfordern sie jedoch meist ein tieferes technisches Verständnis als einfache Arduino-Plattformen.


## Verkabelung

### Grundlagen der Verkabelung

Bei der Verkabelung elektronischer Bauteile müssen grundlegende Aspekte berücksichtigt werden, um die Sicherheit und Funktionsfähigkeit der Schaltung zu gewährleisten. Dazu gehört insbesondere die Begrenzung der Stromstärke, da überhöhte Ströme zu einer erhöhten Wärmeentwicklung in den Leitern führen können. Ebenso ist die Isolierung der Kabel entscheidend, um ungewollte Kurzschlüsse zwischen Leitern zu verhindern. Eine sorgfältige Planung und Ausführung der Verkabelung trägt somit wesentlich zur Zuverlässigkeit, Langlebigkeit und vor allem die Sicherheit der Schaltung bei.

### Grundlagen elektrischer Schaltungen

#### Reihenschaltung

Bei einer Reihenschaltung werden mehrere Bauteile hintereinander geschaltet, sodass der gleiche Strom durch alle Bauteile fließt. Die Gesamtspannung der Spannungsquelle verteilt sich dabei auf die einzelnen Bauteile, abhängig von ihrem Widerstand.

![Reihenschaltung[@Reihenschaltung-Wikipedia]](img/bilder-ausarbeitung-Beichtbuchner/Verkabelung/Reihenschaltung.png)

[@Reihenschaltung-Wikipedia]

#### Parallelschaltung

Bei einer Parallelschaltung werden mehrere Bauteile so miteinander verbunden, dass jedes Bauteil direkt mit den gleichen beiden Klemmen der Spannungsquelle verbunden ist. Dadurch liegt an allen Bauteilen die gleiche Spannung an, während sich die Ströme auf die einzelnen Zweige aufteilen.

![Parallelschaltung[@Parallelschaltung-Wikipedia]](img/bilder-ausarbeitung-Beichtbuchner/Verkabelung/Parallelschaltung.png)

[@Parallelschaltung-Wikipedia]

#### Gemischte Schaltung

Eine gemischte Schaltung kombiniert Elemente einer Reihen- und Parallelschaltung, sodass einige Bauteile hintereinander und andere nebeneinander geschaltet sind. Dabei fließt der Strom durch die Reihenbauteile gleichmäßig, während die Spannung auf die Parallelelemente verteilt wird. Gemischte Schaltungen werden eingesetzt, wenn bestimmte Spannungs- oder Stromverhältnisse innerhalb einer Schaltung benötigt werden.

[@Gemischte-Schaltung-ElektronikKompendium]

### Verbindungstechniken in der Elektronik

Verbindungstechniken in der Elektronik umfassen lösbare und nicht lösbare Methoden wie Löten (Bauteile auf Platinen), Crimpen (Pressen von Leitern in Verbinder), Schraubanschlüsse (einfach, wiederlösbar), Schneidklemmen (Isolierung wird durchtrennt) und Käfigzugfederklemmen (vibrationssicher). Wichtig sind auch Steckverbinder, Bonding (auf Mikroebene), Kleben mit Leitkleber und spezielle Techniken wie das Spleißen für Glasfasern, um zuverlässige Verbindungen für Strom und Daten zu gewährleisten. 
Nicht lösbare Verbindungen

### Löten von Bauteilen

Löten ist ein Verfahren zur dauerhaften Verbindung von Metallteilen, insbesondere in der Elektronik. Dabei wird ein Lötmaterial (Lötzinn) auf die zu verbindende Stelle aufgebracht und durch Erwärmen mit einem Lötkolben geschmolzen. Nach dem Abkühlen härtet das Lötzinn aus und bildet eine mechanisch stabile und elektrisch leitfähige Verbindung zwischen den Bauteilen.

Dieses Verfahren wird insbesondere bei der Durchsteckmontage (THT) und der Oberflächenmontage (SMD) von Bauteilen auf Leiterplatten eingesetzt, da es präzise und zuverlässig ist und die Bauteile nur minimal thermisch belastet.
[@Richtig-löten-Hornbach]

### Crimpen von Kabeln

Crimpen bezeichnet das Verfahren, bei dem ein Kabel mit einem Steckverbinder verbunden wird. Dabei wird zunächst ein Stück der Kabelisolierung entfernt, sodass die einzelnen Leiter freigelegt sind. Die freigelegten Drähte werden anschließend in einen Kontakt(z.B Aderendhülse) eingeführt und mit einer Crimpzange zusammengepresst. Abschließend wird ein Kunststoffkopf aufgebracht, der die Verbindung schützt und stabilisiert. 
[@Richtig-Crimpen-Jungheinrich-PROFISHOP]

![Crimpen[@Crimpen-Anleitung-Conrad]](img/bilder-ausarbeitung-Beichtbuchner/Verkabelung/korrekte-crimpverbindung.jpg)

>Bei einer korrekten Ausführung müssen an Punkt 1 die Litzendrähte und die Isolierung sichtbar sein. An Punkt 2 müssen die Drahtenden sichtbar sein.
[@Crimpen-Anleitung-Conrad]

### Schaltplan

Ein Schaltplan ist eine grafische Darstellung einer elektrischen oder elektronischen Schaltung, die es ermöglicht, die Verbindungen zwischen Bauteilen klar zu erkennen. Er zeigt auf, wie Komponenten wie Widerstände, Kondensatoren, Mikrocontroller oder Sensoren elektrisch miteinander verbunden sind, und dient damit als übersichtliche Orientierung für Aufbau und Analyse der Schaltung.

Darüber hinaus werden Schaltpläne häufig als Grundlage für das Layout von Leiterplatten (PCB) verwendet. Da Leiterplatten sehr komplex sein können, erlaubt der Schaltplan, alle Verbindungen und Bauteilpositionen präzise zu planen, bevor die Leiterplatte gefertigt wird. Auf diese Weise dient er sowohl der Dokumentation als auch der fehlerfreien Umsetzung eines Projekts.

[@Schaltplan-Wikipedia]


## Sensoren und Aktoren

Sensoren und Aktoren bilden zentrale Bestandteile automatisierter und elektronischer Systeme. Sie ermöglichen es technischen Systemen, Informationen aus ihrer Umgebung aufzunehmen und darauf gezielt zu reagieren. Sensoren übernehmen dabei die Aufgabe der Datenerfassung, während Aktoren für die Umsetzung von Aktionen verantwortlich sind. Man kann Sensoren als Eingabeelemente und Aktoren als Ausgabeelemente eines Systems verstehen.

[@Sensorik-und-Aktorik-StudySmarter]

### Sensoren – Funktionsweise und Einsatzgebiete

Sensoren dienen dazu, physikalische oder chemische Größen aus der Umgebung zu erfassen und diese in elektrische Signale umzuwandeln. Diese Signale können anschließend von einem Mikrocontroller oder einem anderen elektronischen System verarbeitet werden. Dadurch ist es möglich, Zustände wie Temperatur, Licht oder Feuchtigkeit digital auszuwerten.

Typische Sensoren kommen in vielen technischen Anwendungen zum Einsatz. Ein Temperatursensor misst beispielsweise die Umgebungstemperatur, ein Lichtsensor erfasst die Helligkeit, und ein Feuchtigkeitssensor bestimmt den Feuchtigkeitsgehalt der Luft oder eines Materials.

Je nach Messgröße lassen sich Sensoren in verschiedene Kategorien einteilen. Häufig verwendete Sensortypen sind Temperatursensoren zur Erfassung von Wärme, Lichtsensoren zur Messung von Helligkeit, Drucksensoren zur Erkennung von Kraft- oder Druckänderungen sowie Bewegungssensoren, die Bewegungen oder Beschleunigungen wahrnehmen. Alle diese Sensoren haben gemeinsam, dass sie physikalische Informationen in elektrische Signale umwandeln, die weiterverarbeitet werden können.

[@Sensorik-und-Aktorik-StudySmarter]

### Aktoren – Funktionsweise und Einsatzgebiete

Aktoren übernehmen die Aufgabe, elektrische Signale in eine physische Aktion umzusetzen. Sie reagieren auf Steuerbefehle eines Mikrocontrollers oder eines anderen Systems und führen daraufhin eine Bewegung oder eine andere gewünschte Funktion aus. Während Sensoren Informationen liefern, sorgen Aktoren dafür, dass auf diese Informationen reagiert wird.

Zu den häufig eingesetzten Aktoren zählen unter anderem Elektromotoren, die mechanische Bewegung erzeugen, Lautsprecher, die elektrische Signale in Schall umwandeln, sowie Leuchtdioden (LEDs), die durch elektrische Ansteuerung Licht aussenden. Aktoren spielen eine entscheidende Rolle in automatisierten Systemen, da sie digitale Steuerbefehle in reale Vorgänge umsetzen.

Ein funktionierendes Zusammenspiel zwischen Sensoren und Aktoren ist Voraussetzung dafür, dass Systeme selbstständig und zielgerichtet arbeiten können. Nur wenn Sensordaten korrekt ausgewertet werden, können Aktoren die passenden Aktionen ausführen.

[@Sensorik-und-Aktorik-StudySmarter]


### Wie Sensoren und Aktoren Zusammenarbeiten

Das Zusammenwirken von Sensoren und Aktoren erfolgt meist in einem wiederkehrenden Ablauf. Zunächst erfassen Sensoren Daten aus der Umgebung. Diese Informationen werden anschließend verarbeitet und ausgewertet, um eine Entscheidung zu treffen. Auf Basis dieser Entscheidung wird schließlich ein Aktor angesteuert, der eine entsprechende Aktion ausführt.

Ein einfaches Beispiel für diesen Ablauf ist ein automatisches Bewässerungssystem. Ein Feuchtigkeitssensor misst den Feuchtigkeitsgehalt des Bodens. Sinkt dieser unter einen festgelegten Wert, wird ein Signal ausgelöst. Daraufhin öffnet ein elektronisch gesteuertes Ventil und startet die Bewässerung.

Damit solche Systeme zuverlässig funktionieren, ist eine sorgfältige Programmierung und Abstimmung der Sensoren und Aktoren notwendig. Nur durch genaue Messungen und präzise Steuerung können automatisierte Systeme korrekt und effizient auf Veränderungen ihrer Umgebung reagieren.

[@Sensorik-und-Aktorik-StudySmarter]


## Praktische Arbeit

## Digitale Modellierung des Hauses

### Auswahl der Vorbilddaten

Zu Beginn der praktischen Arbeit wurde ein geeignetes Wohnhaus als Vorlage für das Modell gesucht, das sowohl zur Aufgabenstellung als auch eine moderne Bauweise aufweist. Nachdem ein passendes Haus gefunden wurde, wurde der Eigentümer kontaktiert und um Erlaubnis für die Nachmodellierung gebeten. Nach seiner Zustimmung stellte er die originalen Baupläne zur Verfügung. Diese dienten als Grundlage für die digitale Nachmodellierung des Hauses in Fusion 360. Durch die Verwendung der vorhandenen Pläne war es möglich, das Gebäude maßstabsgetreu und detailnah nachzubauen, wodurch die Umsetzung des Modells so realitätsnah wie möglich gehalten werden konnte.

Das Haus ist in ein Erdgeschoss und einen Keller unterteilt. Für das Modell wurde jedoch nur das Erdgeschoss modelliert, da der Keller später nicht sichtbar ist und für die Elektronik des Projekts verwendet wird.

Der Maßstab der für das Modellhaus ausgesucht wurde ist 1:25.

### Auswahl des geeigneten CAD-Programms

Für die Modellierung wird das CAD-Programm Fusion 360 verwendet, da es kostenlos genutzt werden kann und eine genaue Erstellung von 3D-Modellen ermöglicht. Zudem bietet das Programm eine übersichtliche Benutzeroberfläche und eignet sich gut für die Konstruktion maßhaltiger Bauteile.

### Modellierung des Hauses

In Fusion 360 begann der Modellierungsprozess mit dem Skizzieren des Bodens beziehungsweise der Grundfläche des Hauses aus der Vogelperspektive. Dabei wurde die reale Länge und Breite des Hauses jeweils mit 0,04 multipliziert, um die korrekten Maße für den späteren 3D-Druck zu erhalten. Anschließend wurde der Skizze ein Volumen zugewiesen, indem sie um 5 mm in die Höhe extrudiert wurde. Danach wurden die äußeren Wände mit einer Wandstärke von 1,26 cm konstruiert. Im nächsten Schritt folgte die Modellierung der inneren Wände mit einer Dicke von 0,908 cm. Sowohl die äußeren als auch die inneren Wände wurden anschließend auf eine Höhe von 10,46 cm extrudiert.

![3](img/bilder-ausarbeitung-Beichtbuchner/3D-Modellierung/Haus/3.png)

Anschließend erfolgte die Modellierung der Fenster und Türen. Da hierfür im Plan keine genauen Maße vorgegeben waren, wurden passende Abmessungen aus dem Internet recherchiert. Die entsprechenden Umrisse wurden anschließend aus den Wänden ausgeschnitten. Jedes Fenster wurde zusätzlich mit einem Schlitz versehen, der auf jeder Seite 5 mm breiter als dieses ist. Dadurch können sie nach dem Druck mit Plexiglas ausgestattet werden, das von oben eingesetzt wird um das Glas zu veranschaulichen.

![4](img/bilder-ausarbeitung-Beichtbuchner/3D-Modellierung/Haus/4.png)

Im nächsten Schritt wurde das Zwischendach modelliert. Dieses besitzt die gleichen Abmessungen wie der Boden des Hauses und weist eine Materialstärke von 6 mm auf. Um ein Verrutschen nach dem Druck zu verhindern und einen sicheren Sitz zu gewährleisten, wurden auf den Wänden entsprechende Dübel vorgesehen, die das Zwischendach fixieren. Zusätzlich wurden fünf Kabelkanäle konstruiert, die durch die Wände geführt sind. Diese sind für die Verkabelung der LEDs verantwortlich, welche die funktion der Deckenlampen übernehmen, sodass man vom keller mit den Kabeln direkt auf das Zwischendach kommt.

![6](img/bilder-ausarbeitung-Beichtbuchner/3D-Modellierung/Haus/6.png)

Anschließend wurde das Dach modelliert. Es handelt sich dabei um ein Flachdach, das umlaufend mit einer niedrigen Begrenzungswand versehen ist. Das Dach liegt nicht direkt auf dem Zwischendach auf, sodass die darunter verlaufenden Kabel nicht eingeklemmt werden. Die Materialstärke des Dachs beträgt ebenfalls 6 mm.

![7](img/bilder-ausarbeitung-Beichtbuchner/3D-Modellierung/Haus/7.png)

Nun wurden noch kleinere Anpassungen vorgenommen. Dazu zählten unter anderem die Erstellung eines zusätzlichen Kabelkanals sowie das Einbringen von Öffnungen in die Zwischenplatte, durch die die LEDs geführt werden können. Außerdem wurden alle Maße noch einmal überprüft, um die Passgenauigkeit und Funktionalität des Modells sicherzustellen.

![10](img/bilder-ausarbeitung-Beichtbuchner/3D-Modellierung/Haus/10.png)

### Aufteilung des Modells in druckbare Einzelteile

Abschließend habe ich das Haus in insgesamt 11 Teile unterteilt, da ein Druck als ein einziges Bauteil aufgrund der Größe nicht möglich gewesen wäre. Das Zwischendach als auch das Dach wurde jeweils geviertelt. Zwischen den Wänden und den einzelnen Dachsegmenten habe ich Dübel modelliert, sodass die Bauteile nach dem 3D-Druck zusammengesteckt werden können. Diese Unterteilung bietet zudem den Vorteil, dass einzelne Wände oder Bauteile bei Beschädigungen einfach und unkompliziert ausgetauscht werden können.

![9](img/bilder-ausarbeitung-Beichtbuchner/3D-Modellierung/Haus/9.png)

![12](img/bilder-ausarbeitung-Beichtbuchner/3D-Modellierung/Haus/12.png)

Bei einem Element des Zwischendachs wurde festgestellt, dass es nur mit 2 Seiten auf den wänden, aufliegt. Deswegen hat man das nächstgelegene teil als Stütze genommen und eine kleine Kante modelliert somit das Herunterfallen des Teils verhindert.

![14](img/bilder-ausarbeitung-Beichtbuchner/3D-Modellierung/Haus/14.png)

## 3D-Druck der Bauteile

### Auswahl des 3D-Druckverfahrens und Materials
- Verwendetes Druckverfahren (z. B. FDM)

Das Druckmaterial wurde auf der Seite von Bambu Lab online bestellt.

Für die Wände wurden insgesamt vier Rollen hellgraues Filament verwendet, während für das Dach zwei Rollen dunkelgraues Filament zum Einsatz kamen. Auf vollständig weiße Bauteile wurde bewusst verzichtet, da diese nach dem Druck sehr stark ins Auge fallen würden und sich optisch deutlich vom Rest des Modells abheben könnten. 


### Vorbereitung der Druckdaten 

Nach der vollständigen Modellierung des Hauses wurden sämtliche Bauteile über die Funktion „3D-Drucken“ in Fusion 360 als STL-Dateien exportiert, da dieses Dateiformat vom verwendeten 3D-Drucker verarbeitet werden kann.

Anschließend wurden die Dateien in den Slicer importiert. Als Drucker wurde der Bambu Lab H2S mit einer 0,2 mm Düse ausgewählt. Dabei kam das Profil „0.10 mm Standard @ BBL H2S 0.2 nozzle“ zum Einsatz. Die grundlegenden Qualitätsparameter wurden im Bereich „Qualität“ überprüft und entsprechend angepasst.

Im nächsten Schritt erfolgte die Ausrichtung der einzelnen Bauteile im Bauraum. Diese wurden so positioniert, dass Überhänge möglichst reduziert und eine stabile Haftung auf dem Druckbett gewährleistet werden. Wo konstruktionsbedingt notwendig, wurden automatisch generierte Stützstrukturen aktiviert, um beispielsweise Tür- und Fensteröffnungen sowie Dachüberstände während des Druckvorgangs abzustützen und ein sauberes Druckergebnis zu erzielen.

### Druckparameter und Druckeinstellungen
Für den Druck wurde eine Schichthöhe von 0,1 mm gewählt. Auch die Höhe der ersten Schicht wurde auf 0,1 mm eingestellt. Die Druckgeschwindigkeit wurde entsprechend dem verwendeten Standardprofil beibehalten, um ein ausgewogenes Verhältnis zwischen Druckdauer und Druckqualität sicherzustellen. Das Infill wurde unterschiedlich und so definiert, dass die Bauteile eine ausreichende Stabilität aufweisen, ohne unnötig viel Material zu verbrauchen. Zusätzlich wurden die Wandstärken passend zur 0,2 mm Düse sowie zu den zuvor konstruierten Modellmaßen eingestellt, um robuste und formstabile Außenflächen zu erhalten.


### Durchführung des Druckvorgangs

Die einzelnen Bauteile unterscheiden sich in ihrer Größe, weshalb auch die Druckzeiten variieren. Das größte Teil benötigte etwa 10 Stunden, während das kleinste bereits nach rund 1 Stunde fertig war. Während des Druckvorgangs konnten die Teile jederzeit mithilfe einer eingebauten Kamera überwacht werden um somit mögliche Fehler oder andere Probleme schnellstmöglich festzustellen. Dadurch war es möglich, den Druck bei Bedarf sofort zu stoppen, um Materialverschwendung zu vermeiden.

#### Druckfehler

Bei zwei Teilen gab es Probleme bei denen der Druck abbgebrochen werden musste und ein erneuter Druck notwendig war.

Teil 1:

![Druckfehler1](img/bilder-ausarbeitung-Beichtbuchner/Druckfehler/Druckfehler1.png)

Hier ist die Stütze der Tür weggebrochen welche notwenig war um den oberen Teil des Türramens zu halten. Diese Konnte nicht wieder angebracht werden und somit wurde der Druck erneut begonnen.

Teil 2:

![Druckfehler2](img/bilder-ausarbeitung-Beichtbuchner/Druckfehler/Druckfehler2.png)

Bei diesem Teil Jedoch hat das Filament nicht mehr gereicht und nach dem wechsel der Rolle hat der Drucker begonnen um etwa 5mm versetzt weiterzudrucken. Dieser Fehler konnte auch nicht behoben werden und somit mussten wir wieder von vorne beginnen.

### Nachbearbeitung der gedruckten Bauteile
Nach dem Druck gab es hin und wieder Dübel oder Wände welche nicht vollständig glatt waren. Auch Verformungen der Böden von manchen Teilen aufgrund der Luftfeuchtigkeit wurde festgestellt. 


## Aufbau der Grundplatte und des Modellhauses

### Aufbau und Gestaltung der Grundplatte

Die Grundplatte, auf der das Haus und alle weiteren Komponenten platziert werden, besteht aus einer 70 cm langen, 70 cm breiten und 2 cm dicken Holzplatte. Darauf wurde ein Rahmen montiert, der exakt dem Umriss des Hauses entspricht, jedoch leicht versetzt angebracht wurde, um auf einer Seite mehr Platz für den Garten zu schaffen. An einer Seite des Rahmens wurde ein Scharnier befestigt, an dem das Haus montiert wird. Dadurch lässt es sich kippen, um einen leichteren Zugang zur darunterliegenden Elektronik zu ermöglichen. Zusätzlich wurde für die Terrasse eine weitere kleinere Holzplatte auf der Höhe des Hausbodens angebracht, um die Pflasterung mithilfe von Stickern darzustellen.


## Elektronischer Aufbau und Verkabelung

### Planung der elektrischen Verschaltung
Zu Beginn wurde eine detaillierte Planung der elektrischen Verschaltung durchgeführt. Dabei wurde eine Übersicht über alle benötigten Komponenten erstellt. Hierzu zählen der Mikrocontroller, mehrere LEDs zur Simulation der Deckenbeleuchtung sowie die entsprechenden Verbindungskabel. Der Arduino wurde zentral unter dem Haus positioniert, um möglichst kurze Leitungswege zu gewährleisten. Für jede einzelne LED wurde ein separater digitaler Pin am Arduino vorgesehen. Dadurch ist es möglich, jede Lichtquelle unabhängig voneinander anzusteuern und gezielt zu schalten. Ein weiterer wichtiger Bestandteil der Planung war die Leitungsführung. Die Kabel verlaufen von der Unterseite des Hauses durch die zuvor konstruierten Kabelkanäle innerhalb der Wände bis hin zum Zwischendach. Diese strukturierte Kabelführung sorgt für Ordnung im Modell und verhindert lose oder sichtbare Leitungen im Innenraum.

### Einbau der LEDs
Die LEDs wurden in die dafür vorgesehenen Löcher im Zwischendach eingesetzt. Die Positionierung erfolgte entsprechend der geplanten Raumaufteilung, sodass jede LED eine Deckenlampe simuliert. Anschließend begann die Verdrahtung der einzelnen LEDs. Zwischen der Anode und der jeweiligen Steuerleitung wurde ein Vorwiderstand eingebaut. Dieser dient dazu, den Strom zu begrenzen und die LEDs vor Beschädigung durch zu hohe Stromstärken zu schützen. Die Kathoden aller LEDs wurden jeweils in eine gemeinsame Klemme geführt. Dadurch konnte eine saubere und übersichtliche Zusammenführung der Masseleitungen hergestellt werden.

### Integration des Mikrocontrollers
Der Arduino wurde unterhalb des Hauses auf der Grundplatte befestigt. Durch die erhöhte und klappbare Konstruktion des Modells bleibt der Mikrocontroller jederzeit zugänglich und kann bei Bedarf gewartet oder neu programmiert werden. Die digitalen Ausgangspins des Arduino wurden jeweils mit den Steuerleitungen der einzelnen LEDs verbunden, sodass jede LED separat angesteuert werden kann. Die zuvor zusammengeführten Masseleitungen wurden über ein einzelnes Kabel mit dem Ground-Pin des Arduino verbunden. Die Spannungsversorgung des Systems erfolgt zentral über den Mikrocontroller. Dadurch wird eine kompakte und strukturierte Anordnung der gesamten Elektronik gewährleistet.

### Sicherheitsmaßnahmen bei der Verkabelung
Die einzelnen Lötstellen zwischen Kabeln, LEDs und Vorwiderständen wurden nach dem Verlöten sorgfältig isoliert. Hierfür kamen sowohl Schrumpfschläuche als auch Isolierband zum Einsatz. Durch das Abdecken der freiliegenden Kontaktstellen wird verhindert, dass leitende Teile unbeabsichtigt miteinander in Berührung kommen. Auf diese Weise können Kurzschlüsse sowie ungewollte elektrische Verbindungen zwischen einzelnen Leitungen zuverlässig vermieden werden. Zudem trägt die Isolierung zur mechanischen Stabilität der Verbindungsstellen bei und erhöht die Betriebssicherheit der gesamten Schaltung.


## Inbetriebnahme und Tests

### Erstinbetriebnahme der Elektronik
Nach Abschluss der vollständigen Verkabelung erfolgte die Erstinbetriebnahme der Elektronik. Dabei wurde das System erstmals mit Spannung versorgt und die grundlegende Funktionsfähigkeit überprüft. Ziel dieses Schrittes war es, festzustellen, ob alle Komponenten ordnungsgemäß angeschlossen sind und das Zusammenspiel zwischen Hardware und Software grundsätzlich funktioniert.

### Funktionstests der Beleuchtung
Nun wurden sämtliche LEDs überprüft. Es wurden alle Lichtquellen gleichzeitig aktiviert, um die grundsätzliche Betriebsbereitschaft der Beleuchtung sicherzustellen. Darüber hinaus erfolgte eine Kontrolle der einzelnen Schaltungen. Dabei wurden die jeweiligen Ausgangspins gezielt angesteuert, um die Funktion jeder LED separat zu prüfen. So konnte sichergestellt werden, dass jede Lichtquelle korrekt mit dem vorgesehenen Pin verbunden ist und individuell gesteuert werden kann. Zusätzlich wurde die Steuerung durch den Mikrocontroller überprüft. Hierbei wurde kontrolliert, ob die programmierten Signale ordnungsgemäß ausgegeben werden und die LEDs entsprechend reagieren.

### Fehleranalyse und Optimierungen
Es wurde festgestellt, dass zwei LEDs nicht leuchteten als alle eingeschaltet wurden. Bei einer LED lag ein Programmierfehler vor, wodurch der entsprechende Ausgangspin nicht korrekt angesteuert wurde. Dieser Fehler wurde durch eine Anpassung des Programmcodes behoben. Bei der zweiten LED wurden Anode und Kathode vertauscht angeschlossen, sodass kein Stromfluss möglich war. Nach Korrektur der Polung funktionierte auch diese LED einwandfrei. Im Zuge der Optimierung wurden sämtliche Anschlüsse nochmals systematisch überprüft. Dabei kontrollierte man Lötstellen, Steckverbindungen, Widerstände sowie die Isolierungen und die Kabelführung. Nach Abschluss dieser Maßnahmen konnte das System vollständig und fehlerfrei in Betrieb genommen werden.

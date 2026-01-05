# Teilaufgabe Schüler Radlingmaier
\textauthor{Radlingmaier Christian}

## Theorie

Dieses Kapitel wird oft auch als _Literaturrecherche_ bezeichnet. Da gehört alles rein was der __normale__ Leser braucht um den praktischen Ansatz zu verstehen. Das bedeutet Sie brauchen einen roten Faden !

Das sind z.B: allgemeine Definitionen, Beschreibung von fachspezifischen Vorgehensweisen, Frameworks, Theorie zu verwendeten Algorithmen, besondere Umstände, ... 

Hier werden die theorethischen sowie die Praktischen Grundlagen für die Umsetzung von Fhem in einem Modellhaus gezeigt und wie man es unteranderem in einem Haus anwenden kann. Das benötigte Wissen sowie die Frameworks die verwendet werden, sind hier dargestellt, damit der Leser alles nachvollziehen kann und es auch nachmachen kann.

### Verwendete Aktoren

- IWILCS Dupont Crimp Set 790tlg inkl. Crimpzange
- 100Pcs 1/4W 5% Toleranz 150Ohm Wiederstand
- 3mm Leuchtdioden

### Zusätzlich Benötigt

- Kabel 0,5mm²
- 4x PLA Basic Hellgrau (10104)
- 2x PLA Basic Dunkelgrau (10105)

### Verwendete Frameworks

- FHEM:
- Node-Red:   
- MQTT:
- Portainer:

# Teilaufgabe – Smart-Home-Umsetzung mit FHEM und Node-RED

**Schüler:** Christian Radlingmaier

## 1. Theoretische Grundlagen
    Unter einem Smart Home versteht man ein Haus, in dem verschiedene technische Komponenten miteinander vernetzt sind und zentral überwacht sowie gesteuert werden können. Diese Steuerung kann sowohl automatisch durch definierte Abläufe als auch manuell durch den Nutzer erfolgen. So ist es beispielsweise möglich, Beleuchtung oder Heizsysteme über ein mobiles Endgerät zu bedienen oder Rollläden zeitgesteuert automatisch zu bewegen.

    In dieser Diplomarbeit kommt ein Arduino als Mikrocontroller zum Einsatz, der für die Erfassung von Sensordaten sowie die Ansteuerung von Aktoren verantwortlich ist. Als zentrale Kontrolleinheit dient ein Raspberry Pi, auf dem die Smart-Home-Software FHEM betrieben wird. FHEM übernimmt die zentrale Verwaltung der angeschlossenen Geräte, verarbeitet eingehende Daten und setzt definierte Automatisierungsregeln um.

    Der Datenaustausch zwischen den einzelnen Systemkomponenten erfolgt über das MQTT-Protokoll. Dieses ermöglicht eine effiziente und zuverlässige Kommunikation zwischen Sensoren, Aktoren und der zentralen FHEM-Instanz.

### 1.2 FHEM als Steuereinheit

#### 1.2.1 FHEM
FHEM ist ein quelloffenes Smart-Home-Framework, das zur Steuerung, Überwachung und Automatisierung von Haus- und Gebäudetechnik eingesetzt wird. Die Software wird überwiegend auf Linux-basierten Systemen betrieben, wie beispielsweise einem Raspberry Pi, und fungiert als zentrale Steuereinheit innerhalb eines Smart-Home-Systems.

Das Framework ist modular aufgebaut und unterstützt eine Vielzahl von Geräten, Protokollen und Kommunikationsschnittstellen. Dadurch können sowohl Sensoren (z. B. Temperatur- oder Bewegungssensoren) als auch Aktoren (z. B. Relais, Heizungsventile oder Beleuchtungssysteme) in das System integriert werden. Die Verwaltung dieser Komponenten erfolgt zentral über FHEM.

Ein wesentliches Merkmal von FHEM ist die flexible Automatisierungslogik. Mithilfe von Regeln, Zeitplänen und Ereignissen können Abläufe definiert werden, die automatisch auf bestimmte Zustände oder Sensordaten reagieren. Zusätzlich bietet FHEM verschiedene Möglichkeiten zur Benutzerinteraktion, etwa über eine webbasierte Oberfläche oder externe Anwendungen.

Die Kommunikation zwischen FHEM und externen Geräten kann über unterschiedliche Protokolle erfolgen. In dieser Diplomarbeit wird hierfür das MQTT-Protokoll verwendet, da es eine effiziente und zuverlässige Datenübertragung zwischen Mikrocontrollern, Sensoren und der FHEM-Zentrale ermöglicht.

Aufgrund seiner Offenheit, Erweiterbarkeit und großen Community eignet sich FHEM besonders für individuelle und anpassbare Smart-Home-Lösungen. Aus diesen Gründen wurde FHEM als zentrale Automatisierungsplattform für diese Diplomarbeit ausgewählt.

### 1.3 Kommunikation und Datenübertragung im SmartHome

#### 1.3.1 Node-RED
Node-RED ist ein quelloffenes, ereignisgesteuertes Entwicklungsframework, das insbesondere im Bereich Smart Home und Internet of Things (IoT) eingesetzt wird. Es ermöglicht die grafische Erstellung von Steuerungs- und Automatisierungslogiken mithilfe eines webbasierten Editors. Die einzelnen Funktionsbausteine, sogenannte Nodes, werden per Drag-and-Drop miteinander verbunden und bilden gemeinsam sogenannte Flows, welche den Daten- und Kontrollfluss innerhalb des Systems abbilden.

Innerhalb eines Smart-Home-Systems übernimmt Node-RED die Verarbeitung von Sensordaten sowie die Umsetzung von logischen Abläufen. Eingehende Informationen, beispielsweise von Temperatur- oder Bewegungssensoren, können analysiert, gefiltert und anschließend zur Steuerung von Aktoren wie Beleuchtung, Heizung oder Rollläden verwendet werden. Dadurch lassen sich sowohl einfache Automatisierungen als auch komplexe Abhängigkeiten realisieren.

Ein wesentlicher Vorteil von Node-RED ist die Unterstützung zahlreicher Kommunikationsprotokolle und Schnittstellen. Dazu zählen unter anderem MQTT, HTTP sowie WebSockets, wodurch eine einfache Integration von Mikrocontrollern, Smart-Home-Zentralen und externen Diensten möglich ist. In dieser Diplomarbeit wird Node-RED insbesondere zur Verarbeitung von MQTT-Nachrichten und zur Umsetzung der Steuerlogik eingesetzt.

Zusätzlich besteht die Möglichkeit, eigene Funktionslogiken mithilfe von JavaScript zu implementieren, wodurch Node-RED flexibel erweitert werden kann. Über optionale Erweiterungen wie Dashboards können zudem grafische Benutzeroberflächen zur Visualisierung von Daten und zur manuellen Steuerung erstellt werden.

Aufgrund seiner übersichtlichen grafischen Programmierumgebung, der hohen Erweiterbarkeit und der aktiven Community eignet sich Node-RED besonders für die Entwicklung individueller Smart-Home-Lösungen. Daher wird das Framework in dieser Diplomarbeit als zentrales Werkzeug zur Umsetzung von Automatisierungs- und Steuerungsprozessen verwendet. 

## Praktische Arbeit

Hier beschreiben Sie ihren praktischen Teil. Es geht darum seine Implementierung / Versuche so darzustellen dass anhand dieser dre Leser erkennen kann was sie wie gemacht haben.

Die Frage nach der Detailgenauigkeit lässt sich wie folgt beantworten: So, dass man Ihre Aufgabenstellung vollständig  nachvollziehen kann wenn man nur diese Diplomarbeit in Händen hat!

### Erzeugen von Java Quellcode

Unter einem Array in Java versteht man ein Feld oder Container, das in der Lage ist, mehrere Objekte vom gleichen Typ aufzunehmen und zu verwalten. Dabei wird in Java das Array als eine spezielle Klasse repräsentiert, was unter anderem mit sich bringt, dass man auf spezielle Methoden und Operationen bei Arrays zurückgreifen kann. Der Umgang mit Arrays mag gerade am Anfang etwas schwerer sein und birgt viele Fehlerquellen, nach und nach wird man das System das hinter den Arrays steht aber gut nachvollziehen können. 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~{caption="Initialisieren eines Arrays" .java}
Typ[] Name = new Typ[Anzahl];
Typ Name[] = new Typ[Anzahl];
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Etwas erfahrenere Programmierer werden jetzt schon erkennen, worauf es beim Zugriff auf Elemente im Array meist hinausläuft: Auf Schleifen!
Schleifen sind ein komfortables Mittel um alle Elemente eines Arrays durchzugehen und auf Wunsch auszugeben oder andere Operationen darauf anzuwenden. Allerdings muss man nicht nur hier aufpassen, dass man die länge des Arrays in der Schleife nicht überschreitet und so auf Felder zugreift die gar nicht existieren. Damit so etwas erst gar nicht passiert, kann man in der Abbruchbedingung der for-Schleife direkt die Länge des Arrays ausgeben mit: array.length.

Möchte man nun also alle 5 Elemente unseres Beispiels-Arrays mit einer Schleife ausgeben lassen, dann würde das so gehen:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~{caption="Examples of array manipulations" .java}
// (c) by Mike Scott

public class ArrayExamples
{	public static void main(String[] args)
	{	int[] list = {1, 2, 3, 4, 1, 2, 3};
		findAndPrintPairs(list, 5);
		bubblesort(list);
		showList(list);

		list = new int[]{ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11};
		bubblesort(list);
		showList(list);

		list = new int[]{11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1, 0, -1, -2};
		bubblesort(list);
		showList(list);

		list = new int[]{1};
		bubblesort(list);
		showList(list);
	}


	// pre: list != null, list.length > 0
	// post: return index of minimum element of array
	public static int findMin(int[] list)
	{	assert list != null && list.length > 0 : "failed precondition";

		int indexOfMin = 0;
		for(int i = 1; i < list.length; i++)
		{	if(list[i] < list[indexOfMin])
			{	indexOfMin = i;
			}
		}

		return indexOfMin;
	}
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Obwohl hier nur java gezeigt ist, unterstützt das Template auch scala, java, javascript, css, html5 und xml

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~{caption="Ein einfaches XML" .xml}
<?xml version="1.0" standalone="yes"?>
<!DOCTYPE module [
    <!ELEMENT module (module|property|metadata|message)*>
    <!ATTLIST module name NMTOKEN #REQUIRED>
    <!ELEMENT property EMPTY>
    <!ATTLIST property
        name NMTOKEN #REQUIRED
        value CDATA #REQUIRED
        default CDATA #IMPLIED
    >
    <!ELEMENT metadata EMPTY>
    <!ATTLIST metadata
        name NMTOKEN #REQUIRED
        value CDATA #REQUIRED
    >
    <!ELEMENT message EMPTY>
    <!ATTLIST message
        key NMTOKEN #REQUIRED
        value CDATA #REQUIRED
    >
]>

<!--
    Checkstyle configuration that checks if the braces are set correctly
 -->

<module name = "Checker">
    <property name="charset" value="UTF-8"/>
    <property name="severity" value="warning"/>

    <property name="fileExtensions" value="java"/>
    <!-- Checks for whitespace                               -->
    <!-- See http://checkstyle.sf.net/config_whitespace.html -->

    <module name="TreeWalker">
        
        <module name="NeedBraces"/>
        <module name="LeftCurly">
        	<property name="option" value="nl"/>
        </module>

        <module name="RightCurly">
            <property name="id" value="RightCurlyAlone"/>
            <property name="option" value="alone"/>
            <property name="tokens"
             value="CLASS_DEF, METHOD_DEF, CTOR_DEF, LITERAL_FOR, LITERAL_WHILE, STATIC_INIT,
                    INSTANCE_INIT,LITERAL_TRY, LITERAL_CATCH, LITERAL_FINALLY, LITERAL_IF, LITERAL_ELSE,
                    LITERAL_DO"/>
        </module>
    </module>
</module>
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Hier etwas in kotlin

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~{caption="Ein einfaches Kotlin Beispiel" .kotlin}
// this is a simple code listing:
println("hello kotlin from latex")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Und noch ein Beispiel in vba

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~{caption="Ein einfaches Visual Basic for Applications Beispiel" .vba}
Private Sub ExitSub()
 
    Dim i As Integer
 
    For i = 1 To 10      
        If i = 5 Then
            Exit Sub
            MsgBox "The value of i is" & i
        End If
    Next i 
 
End Sub
 
 
Private Sub CallExitSub()
    Call ExitSub
    MsgBox "Exit Sub"  
End Sub
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


und noch was in Dart (im Markdown direkt als Latex Quellcode eingefügt - damit funktionieren jegliche Sprachen welche als langdef vorliegen) 

\begin{lstlisting}[language=Dart, caption={Ein Beispiel für Dart}]
library hallo;

void main() {
  String x;
  print('Hello, World!');
  x = 'hallo';
}
\end{lstlisting}


### Auswertung der Ergebnisse

Anhand von XY kann man folgende Tabelle ableiten:

| Right | Left | Default | Center |
|------:|:-----|---------|:------:|
|   12  |  12  |    12   |    12  |
|  123  |  123 |   123   |   123  |
|    1  |    1 |     1   |     1  |

: Eine Tolle tabelle

#### Eine Überschrift 4ter Ordnung

Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext.


#### Noch ein Überschrift 4ter Ordnung

Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext.

Und mit einer Aufzählung:

* Alpha
* Bravo
* Charlie
    * Charlie 1
    * Charlie 2
    * Charlie 3
    * Charlie 4
* Delta
* Epsilon

 Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext. Mit etwas Fließtext.


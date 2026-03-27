# Zusammenfassung

Im Rahmen dieser Diplomarbeit wurde ein modular aufgebautes Smart Home-System in Form eines Modellhauses geplant, umgesetzt und dokumentiert. Ziel war es, typische Funktionen moderner Hausautomation nicht nur theoretisch zu beschreiben, sondern als nachvollziehbares Gesamtsystem praktisch zu realisieren. Dabei standen die saubere Trennung von Hardware, Kommunikationslogik und Bedienoberfläche sowie die Erweiterbarkeit des Systems im Vordergrund.

Das Thema war für eine schulische Diplomarbeit passend gewählt, weil es mehrere Fachbereiche sinnvoll verbindet: mechanischer Aufbau, Elektronik, Netzwerktechnik, Automatisierung und Softwareintegration. Statt isolierter Einzelversuche entstand ein gemeinsamer Prototyp mit klarer Systemarchitektur und dokumentierten Schnittstellen. Damit wurde das zentrale Projektziel erreicht.

Die Teilaufgaben haben sich dabei direkt ergänzt:

- Modellierung und Aufbau des Hauses mit Fusion 360 und 3D-Druck (Massstab 1:25, Segmentierung in druckbare Bauteile, strukturierte Verkabelung, montagefreundlicher Aufbau).
- Elektronische Umsetzung mit LEDs und Mikrocontrolleranbindung inklusive Inbetriebnahme, Fehlersuche und Korrektur von Verdrahtungs- und Programmierfehlern.
- Aufbau der zentralen Systemplattform auf dem Raspberry Pi mit Docker, MQTT, Node-RED und Dashboardsteuerung sowie Integration einer Wetterstation.
- Umsetzung einer alternativen Steuerungslogik mit FHEM/Perl als zusätzlicher technischer Ansatz für die Hausautomatisierung.

Als wesentliche Ergebnisse wurden die zentralen Use Cases umgesetzt und getestet: Sensordaten erfassen und übertragen, Licht automatisch bzw. manuell schalten, Zustände visualisieren und Dienste stabil betreiben. Die durchgängige Kommunikation zwischen Sensorik/Aktorik, Arduino, Node-RED, MQTT und Plattformebene funktioniert im Projektstand reproduzierbar. Typische Probleme (z. B. Druckfehler, vertauschte Polung der LEDs, serielle Portkonflikte, instabile Gerätepfade) konnten analysiert und mit konkreten Maßnahmen behoben werden.

Offen geblieben sind vor allem Punkte, die bewusst außerhalb des Projektumfangs lagen: kein produktiver Außenzugriff, keine native App, keine industrielle Sicherheitszertifizierung und keine vollständige Abdeckung aller Smart Home-Szenarien. Für die Weiterarbeit bieten sich folgende Schritte an: Vereinheitlichung der final genutzten Steuerungsplattform, Ausbau der Sensorik (z. B. CO2/Luftqualität), zusätzliche Automationen, konsequente Sicherheitshärtung (TLS, Zugriffstrennung, Backupstrategie) sowie optional Sprachsteuerung.

Zusammenfassend hat die Arbeit gezeigt, dass mit kostengünstiger Hardware und Open-Source-Software ein technisch sauberes, didaktisch gut nutzbares und erweiterbares Smart Home-Demonstrationssystem aufgebaut werden kann. Die entwickelte Architektur ist eine belastbare Grundlage für Folgeprojekte.

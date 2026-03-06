# Zusammenfassung

Im Rahmen dieser Diplomarbeit wurde ein modular aufgebautes Smart-Home-System in Form eines Modellhauses geplant, umgesetzt und dokumentiert. Ziel war es, typische Funktionen moderner Hausautomation nicht nur theoretisch zu beschreiben, sondern als nachvollziehbares Gesamtsystem praktisch zu realisieren. Dabei standen die saubere Trennung von Hardware, Kommunikationslogik und Bedienoberflaeche sowie die Erweiterbarkeit des Systems im Vordergrund.

Das Thema war fuer eine schulische Diplomarbeit passend gewaehlt, weil es mehrere Fachbereiche sinnvoll verbindet: mechanischer Aufbau, Elektronik, Netzwerktechnik, Automatisierung und Softwareintegration. Statt isolierter Einzelversuche entstand ein gemeinsamer Prototyp mit klarer Systemarchitektur und dokumentierten Schnittstellen. Damit wurde das zentrale Projektziel erreicht.

Die Teilaufgaben haben sich dabei direkt ergaenzt:

- Modellierung und Aufbau des Hauses mit Fusion 360 und 3D-Druck (Massstab 1:25, Segmentierung in druckbare Bauteile, strukturierte Verkabelung, montagefreundlicher Aufbau).
- Elektronische Umsetzung mit LEDs und Mikrocontroller-Anbindung inklusive Inbetriebnahme, Fehlersuche und Korrektur von Verdrahtungs- und Programmierfehlern.
- Aufbau der zentralen Systemplattform auf dem Raspberry Pi mit Docker, MQTT, Node-RED und Dashboard-Steuerung sowie Integration einer Wetterstation.
- Umsetzung einer alternativen Steuerungslogik mit FHEM/Perl als zusaetzlicher technischer Ansatz fuer die Hausautomatisierung.

Als wesentliche Ergebnisse wurden die Kern-Use-Cases umgesetzt und getestet: Sensordaten erfassen und uebertragen, Licht automatisch bzw. manuell schalten, Zustaende visualisieren und Dienste stabil betreiben. Die End-to-End-Kommunikation zwischen Sensorik/Aktorik, Arduino, Node-RED, MQTT und Plattformebene funktioniert im Projektstand reproduzierbar. Typische Probleme (z. B. Druckfehler, vertauschte LED-Polung, serielle Portkonflikte, instabile Geraetepfade) konnten analysiert und mit konkreten Massnahmen behoben werden.

Offen geblieben sind vor allem Punkte, die bewusst ausserhalb des Projektumfangs lagen: kein produktiver Aussenzugriff, keine native App, keine industrielle Sicherheitszertifizierung und keine vollstaendige Abdeckung aller Smart-Home-Szenarien. Fuer die Weiterarbeit bieten sich folgende Schritte an: Vereinheitlichung der final genutzten Steuerungsplattform, Ausbau der Sensorik (z. B. CO2/Luftqualitaet), zusaetzliche Automationen, konsequente Security-Haertung (TLS, Zugriffstrennung, Backup-Strategie) sowie optional Sprachsteuerung.

Zusammenfassend hat die Arbeit gezeigt, dass mit kostenguenstiger Hardware und Open-Source-Software ein technisch sauberes, didaktisch gut nutzbares und erweiterbares Smart-Home-Demonstrationssystem aufgebaut werden kann. Die entwickelte Architektur ist eine belastbare Grundlage fuer Folgeprojekte.

## Lesen und lesen lassen

Nach der Fertigstellung sollte die gesamte Arbeit mindestens in zwei eigenen Korrekturdurchgaengen gelesen werden: zuerst inhaltlich-technisch (Stimmigkeit von Architektur, Begriffen, Abbildungen, Verweisen), danach sprachlich (Rechtschreibung, Grammatik, Stil, einheitliche Formulierungen). Besonders wichtig ist dabei die Konsistenz zwischen den Teilkapiteln, damit keine Widersprueche bei Technologien, Zustaendigkeiten oder Projektstaenden entstehen.

Zusaetzlich sollte mindestens eine externe Person die Arbeit vollstaendig gegenlesen. Externe Leser erkennen unklare Stellen, fehlende Uebergaenge und Formulierungen, die fuer das Team selbst bereits betriebsblind geworden sind. Die Rueckmeldungen sollten gesammelt, priorisiert und strukturiert eingearbeitet werden.

Fuer den finalen Stand empfiehlt sich ein kurzer Abschluss-Check: Kapitelreihenfolge, Abbildungs- und Quellenverweise, Terminangaben, Einheitlichkeit der Fachbegriffe sowie ein letzter Test aller beschriebenen Demo-Szenarien. So wird sichergestellt, dass die schriftliche Dokumentation den tatsaechlichen Projektstand korrekt und verstaendlich abbildet.

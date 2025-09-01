# Diplomarbeit_2025-26: SmartHome

In dieser Diplomarbeit wird ein intelligentes SmartHome-Modellhaus entwickelt, das zentrale Automatisierungs- und Steuerungskomponenten eines modernen SmartHomes im Miniaturformat demonstriert. Ziel ist es, verschiedene Sensoren (z. B. Temperatur, Helligkeit) und Aktoren (z. B. Heizung, Beleuchtung, Lüftung) miteinander zu vernetzen und diese über eine zentrale Steuerung (Home Assistant und/oder FHEM) automatisiert sowie manuell bedienbar zu machen.

Zum Einsatz kommt ein Raspberry Pi als Steuerzentrale, auf dem über Docker-Container die nötige Infrastruktur läuft (z. B. MQTT-Broker, Node-RED, Portainer). Die Kommunikation erfolgt überwiegend über das MQTT-Protokoll. Zusätzlich wird ein Fokus auf Visualisierung, Fernzugriff und mögliche Erweiterungen gelegt.

Hilfe zu Benutzung dieses Templates finden Sie in der Datei [USAGE.md](USAGE.md)

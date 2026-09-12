# Fedora ThinkPad Update via Ansible

Automatisierte Systemaktualisierung für ein Lenovo ThinkPad (Fedora) gesteuert von einem DELL OptiPlex Control Node.

## Demo

[![asciicast](https://asciinema.org/a/1265250.svg)](https://asciinema.org/a/1265250)

## Projektstruktur

* update-thinkpad.yml: Playbook zur Aktualisierung von DNF-Paketen sowie systemweiten und User-Flatpaks.
* hosts: Inventory-Datei mit der Zuordnung des Managed Nodes (thinkpad).
* ansible.cfg: Lokale Ansible-Konfiguration für automatisches Inventory-Loading.
* commands.md: Dokumentation der wichtigsten Terminal-Befehle und Workflows.

## Voraussetzungen

* Control Node: Ansible & SSH-Schlüssel eingerichtet
* Managed Node: Fedora Workstation (mit Sudo-Rechten für den Ansible-User)

## Schnellstart

1. Verbindung testen:
   ansible notebooks -m ping

2. Update-Playbook ausführen:
   ansible-playbook update-thinkpad.yml -K

> Hinweis: Bei LUKS-verschlüsselten Systemen muss das Gerät nach einem Neustart erst physisch entschlüsselt werden, bevor der SSH-Dienst erreichbar ist.

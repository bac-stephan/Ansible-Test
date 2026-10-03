# Fedora ThinkPad Update via Ansible

Automatisierte Systemaktualisierung (DNF-Pakete und Flatpaks) für mehrere Fedora Workstation Nodes (`optiplex`, `thinkpad`, `dell_laptop`), gesteuert von einem zentralen DELL OptiPlex Control Node.

## Demo

[![asciicast](https://asciinema.org/a/1265250.svg)](https://asciinema.org/a/1265250)

## Projektstruktur

* `update-all.yml`: Playbook zur zentralen Aktualisierung aller Fedora-Nodes (DNF, Systemwide & User-Flatpaks, bedingter Reboot).
* `hosts`: Inventory-Datei mit strukturierter Gruppenzuordnung (`all_nodes`, `notebooks`, `local`).
* `ansible.cfg`: Lokale Ansible-Konfiguration für automatisches Inventory-Loading.
* `projekt_dokumentation.md`: Ausführliche Projektdokumentation und Lernschritte.
* `commands/`: Dokumentation der Terminal-Befehle und Workflows (`01-commands.md`, `02-commands.md`).
* `code-py/`: Python-Hilfsskripte zur Bearbeitung und Konvertierung von Terminalaufnahmen (`convert.py`, `trim_cast.py`).
* `casts/` & `gifs/`: Terminal-Aufzeichnungen und Demos des automatisierten Update-Prozesses.

## Voraussetzungen

* Control Node: Ansible & SSH-Schlüssel eingerichtet
* Managed Node: Fedora Workstation (mit Sudo-Rechten für den Ansible-User)

## Schnellstart

1. Playbook auf Linter-Konformität prüfen:
   ansible-lint update-all.yml

2. Verbindung testen:
   ansible notebooks -m ping

3. Update-Playbook ausführen:
   ansible-playbook update-thinkpad.yml -K

> Hinweis: Bei LUKS-verschlüsselten Systemen muss das Gerät nach einem Neustart erst physisch entschlüsselt werden, bevor der SSH-Dienst erreichbar ist.

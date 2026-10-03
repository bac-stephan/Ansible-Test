# Automatisierte Systemwartung via Ansible (Fedora Infrastructure)

Automatisierte Systemaktualisierung (DNF & Flatpak) für den Control Node (DELL OptiPlex) sowie Remote-Notebooks (Lenovo ThinkPad, DELL Laptop) gesteuert über Ansible.

## Demo

[![asciicast](https://asciinema.org/a/1265250.svg)](https://asciinema.org/a/1265250)

## Projektstruktur

* `update-all.yml`: Zentrales Playbook zur Aktualisierung von DNF-Paketen sowie systemweiten und User-Flatpaks auf allen Fedora-Nodes.
* `hosts`: Inventory-Datei mit Unterteilung in `local` (OptiPlex), `notebooks` (ThinkPad, DELL Laptop) und `all_nodes`.
* `ansible.cfg`: Lokale Ansible-Konfiguration für automatisches Inventory-Loading.
* `commands.md`: Dokumentation der wichtigsten Terminal-Befehle, Git-Workflows und Linter-Pipelines.

## Voraussetzungen

* **Control Node (DELL OptiPlex):** Ansible & `ansible-lint` installiert, SSH-Schlüssel eingerichtet.
* **Managed Remote Nodes (Notebooks):** Fedora Workstation mit aktivem SSH-Dienst und Sudo-Rechten für den Ansible-User.

## Schnellstart

1. **Verbindung zu allen Nodes testen:**
   ```bash
   ansible all_nodes -m ping
   ```

2. **Update-Playbook für die gesamte Infrastruktur ausführen:**
   ```bash
   ansible-playbook update-all.yml -K
   ```

> **Hinweise:**
> * Der Control Node (`optiplex`) verarbeitet Updates lokal (`ansible_connection=local`) und überspringt den automatischen Neustart, damit die Ansible-Sitzung geordnet beendet werden kann.
> * Bei LUKS-verschlüsselten Laptops muss nach dem Neustart das Festplattenpasswort eingegeben werden, damit das System vollständig bootet und der SSH-Dienst erreichbar wird.
# Ansible ThinkPad Update Workflow

Befehlssammlung und Notizen zur Verwaltung des ThinkPads.

## 1. Verbindung prüfen
ansible notebooks -m ping

## 2. System-Update ausführen
ansible-playbook update-thinkpad.yml -K

## 3. Neustart-Bedarf nach DNF-Updates prüfen
ssh -t thinkpad "sudo dnf needs-restarting -r"

## 4. ThinkPad neustarten
ssh -t thinkpad "sudo reboot"

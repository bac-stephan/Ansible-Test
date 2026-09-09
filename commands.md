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

## 5. Trockenlauf (Dry-Run) durchführen, ohne System zu verändern
ansible-playbook update-thinkpad.yml --check -K

## 6. Playbook auf Best Practices und Fehler prüfen
ansible-lint update-thinkpad.yml

## 7. Trailing Whitespaces (Leerzeichen am Zeilenende) automatisch entfernen
sed -i 's/[ \t]*$//' update-thinkpad.yml

## 8. Tipp in Vim, ...eingeben, um unsichtbare Leerzeichen und Tabulatoren anzuzeigen.
:set list

## 9. Trockenlauf (Dry-Run): Prüfe vor dem scharfen Ausführen, was Ansible auf dem Ziel-Host verändern würde.
ansible-playbook -i hosts update-thinkpad.yml --check

## 10. Sichtbarkeit auf öffentlich ändern
gh repo edit --visibility public --accept-visibility-change-consequences

## 11. Kontrolliere den neuen Status des Repositories
gh repo view --json visibility

## 12. Änderung prüfen
git diff update-thinkpad.yml

## 13. Datei für den Commit vormerken
git add update-thinkpad.yml

## 14. Änderung lokal speichern
git commit -m "pip-Task aus ThinkPad Update-Playbook entfernt"

## 15. Status kontrollieren
git status

## 16. Auf GitHub hochladen
git push origin main

## 17. Falls GitHub noch nicht als remote hinterlegt ist, erstelle ein neues Repository auf GitHub und verknüpfe es.
## Falls noch kein Remote existiert (BEISPIEL-URL anpassen):
git remote add origin git@github.com:DEIN_GITHUB_USERNAME/Ansible-Test.git
git branch -M main
git push -u origin main

## 18. Anmeldestatus bei GitHub prüfen
gh auth status

## 19. Repository auf GitHub erstellen und pushen
gh repo create Ansible-Test --private --source=. --remote=origin --push

## 20. Kontrolliere, ob die Remote-Adresse korrekt eingetragen wurde.
git remote -v

## 21. Repository auch direkt über das Terminal im Browser öffnen.
gh repo view --web

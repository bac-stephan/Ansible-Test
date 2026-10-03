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

## 22. `:r !tail -n 50 ~/.bash_history`

cd Dokumente/
Gitlab/
cd Gitlab/
ls -rtlh
glab snippet list
tldr glab
cd
cd Dokumente/
cd Podman/
ls -rtlh
mkdir 2026-09-11
cd 2026-09-11/
whoami
id
podman run -d --name web -p 8080:80 nginx
history | grep login
podman login registry.docker.io
podman login docker.io
podman run -d --name web -p 8080:80 nginx
podman logout docker.io
podman login -u stephanbac docker.io
podman run -d --name web -p 8080:80 nginx
podman ps
curl http://127.0.0.1:8080
podman exec web id
podman info --format 
podman info --format json 
podman info --format '{{.Host.Security.Rootless}}'
podman ps
podman ps -a
systemd-cgls /user.slice
id
 podman top web user huser pip hpid 
tldr  podman top web user huser pip hpid 
podman top web user huser pip 
sudo podman top web user huser pip hpid 
podman ps
podman top
podman top web
podman logs -f web
podman exec -it web bash
podman stop web
podman rm web
podman ps
cat /proc/self/loginuid 
cd
history |grep sudo
sudo dnf upgrade --refresh && flatpak update
reboot

## 23. python3 trim_cast.py

## 24. asciinema upload ansible-demo.cast

## 25. asciinema auth

## 26. [![asciicast](https://asciinema.org/a/123456.svg)](https://asciinema.org/a/123456)

## 27. head -n 1 ansible-demo.cast

## 28. python3 -c 'import json; lines = open("ansible-demo.cast").readlines(); h = json.loads(lines[0]); h["version"] = int(h["version"]); lines[0] = json.dumps(h) + "\n"; open("ansible-demo.cast", "w").writelines(lines)'

## 29. asciinema upload ansible-demo.cast

## 30. python3 convert.py

## 31. head -n 1 ansible-demo.cast

## 32. asciinema upload ansible-demo.cast

## 33. [![asciicast](https://asciinema.org/a/<DEINE_CAST_ID>.svg)](https://asciinema.org/a/<DEINE_CAST_ID>)

## 34. [![asciicast](https://asciinema.org/a/<DEINE_CAST_ID>.svg?theme=solarized-dark&speed=1.5)](https://asciinema.org/a/<DEINE_CAST_ID>)

## 35. asciinema upload ansible-demo.cast

## 36. podman run --rm -v "$(pwd)":/data ghcr.io/asciinema/agg --theme solarized-dark --speed 1.2 /data/ansible-demo.cast /data/demo.gif

## 37. ![Ansible Control Node Demo](demo.gif)

## 38. [![Ansible Control Node Demo](demo.gif)](https://asciinema.org/a/<DEINE_CAST_ID>)

## 39. podman run --rm -v "$(pwd)":/data:z ghcr.io/asciinema/agg --theme solarized-dark --speed 1.2 /data/ansible-demo.cast /data/demo.gif

## 40. ls -lh demo.gif

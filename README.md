# MeinProjekt – GitHub Repository Setup und Workflow

## 📝 Einführung

In diesem Projekt wird Schritt für Schritt erklärt, wie man ein GitHub-Repository erstellt, mit einem SSH-Schlüssel absichert, lokal klont, konfiguriert und typische Workflows mit Branches, Commits und Merges durchführt.

## ✅ Voraussetzungen

- [x] GitHub-Konto erstellt
- [x] SSH-Key generiert
- [x] Repository erstellt
- [x] Git konfiguriert
- [x] Lokales Repository geklont


## 🧩 GitHub Repository Setup

- Konto bei GitHub erstellt / eingeloggt

![Mein GitHub-Konto](${images}/2025-04-11-10-52-24.png)

- Neues Repository namens **"MeinProjekt"** erstellt

![Neues Repository](${images}/2025-04-11-09-50-05.png)

- Repository-URL (SSH): `git@github.com:Clyphi/MeinProjekt.git`

## 🔑 SSH-Schlüssel

- Im Terminal geprüft: `ls ~/.ssh/`

![SSH-Keys anzeigen, falls vorhanden](${images}/2025-04-11-09-54-23.png)

- SSH-Schlüssel bereits vorhanden: `ssh-keygen -t rsa -b 4096 -C "leins.claudia@wtnet.de"`

![Mein Public SSH-Key](${images}/2025-04-11-09-46-49.png)

- Skript für public SSH-Key
Kopiert den öffentlichen SSH-Schlüssel in die Zwischenablage
(Verhindert, dass man Ausversehen den privaten SSH-Schlüssel weitergibt.)

```bash
#!/bin/bash

# Zeigt den öffentlichen SSH-Schlüssel an
PUB_KEY=$(cat ~/.ssh/id_rsa.pub)

# Kopiert den Schlüssel in die Zwischenablage (macOS / Linux)
if command -v pbcopy &> /dev/null; then
  echo "$PUB_KEY" | pbcopy
  echo "Dein öffentlicher SSH-Schlüssel wurde in die Zwischenablage kopiert!"
elif command -v xclip &> /dev/null; then
  echo "$PUB_KEY" | xclip -selection clipboard
  echo "Dein öffentlicher SSH-Schlüssel wurde in die Zwischenablage kopiert!"
else
  echo "Fehler: Keine geeignete Kopiermethode gefunden. Bitte kopiere den Schlüssel manuell."
  echo "$PUB_KEY"
fi
```

## 💻 Lokales Repository & Workflow

- Repository lokal geklont: `git clone git@github.com:Clyphi/MeinProjekt.git`

![Repository klonen](${images}/2025-04-10-16-58-37.png)

- Git konfiguriert: `user.name`, `user.email`

![Mein Name konfigurieren](${images}/2025-04-11-10-18-36.png)
![Meine E-Mail-Adresse konfigurieren](${images}/2025-04-10-17-00-03.png)

- `main.py` erstellt und erster Commit

!['main.py' und Commit erstellt](${images}/2025-04-10-17-01-04.png)

- Branch `feature` erstellt

![feature Branch erstellt](${images}/2025-04-10-17-01-32.png)

- `utils/database.py` hinzugefügt und commitet

![Verzeichnis und database.py erstellt](${images}/2025-04-10-17-02-11.png)

- `main.py` im Feature-Branch geändert

![Änderung in 'main.py' und Commit erstellt](${images}/2025-04-10-17-03-20.png)

- Zurück auf `master`, `main.py` erneut geändert Fehlermeldung.

Mit 'git branch' die Namen der Branches überprüft.

Hauptbranch heißt nicht 'master' sondern 'main'.

Änderung: 'git checkout main' statt 'git checkout master' eingegeben.

![Wechsel in den main branch](${images}/2025-04-10-17-04-22.png)

- Merge durchgeführt → Merge-Konflikt

![Merge Konflikt](${images}/2025-04-10-17-07-54.png)

- Merge-Konflikt manuell gelöst und committed

![Merge Konflikt anzeigen](${images}/2025-04-10-17-08-16.png)

![Merge Konflikt behoben](${images}/2025-04-10-17-11-45.png)

## 📁 Verzeichnisstruktur

![Mein Projekt](${images}/2025-04-11-11-05-10.png)

## 🧠 Nützliche Git-Befehle

| Befehl                     | Bedeutung                                 |
|----------------------------|-------------------------------------------|
| `git clone`                | Klont ein Repository                      |
| `git status`               | Zeigt den aktuellen Status                |
| `git add <datei>`          | Fügt alle Änderungen zum Staging hinzu    |
| `git commit -m "msg"`      | Commitet die Änderungen mit Nachricht     |
| `git branch`               | Listet alle Branches                      |
| `git checkout <branch>`    | Wechselt zu einem anderen Branch          |
| `git merge <branch>`       | Führt Branch in aktuellen Branch zusammen |
| `git log`                  | Zeigt Historie der Commits                |
| `git push`                 | Überträgt lokale Änderungen zu GitHub     |


## 🔗 Weitere Ressourcen

- [Git – Offizielle Doku](https://git-scm.com/doc)
- [SSH-Zugang zu GitHub einrichten](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
- [VSCode Markdown Guide](https://code.visualstudio.com/docs/languages/markdown)
- [GitHub Docs – Erste Schritte mit Git](https://docs.github.com/en/get-started/quickstart)
- [GitHub Docs – Branches erstellen und verwalten](https://docs.github.com/en/get-started/using-git/creating-and-deleting-branches)
- [Markdown Cheat Sheet (GitHub)](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
- [Oh My Git! – Interaktives Git-Lernspiel](https://ohmygit.org/)
- [Pro Git Buch (online & kostenlos)](https://git-scm.com/book/de/v2)




# MeinProjekt - GitHub Repository Setup und Workflow

## 1. GitHub Repository Setup

Für dieses Projekt habe ich ein neues GitHub-Repository mit dem Namen **"MeinProjekt"** erstellt. Hier sind die Schritte:

1. Ich habe mich bei GitHub (www.github.com) angemeldet.
2. Nach dem Login habe ich auf "+ New" geklickt und ein neues Repository mit dem Namen **"MeinProjekt"** erstellt.
3. Die URL des erstellten Repositories lautet: `https://github.com/muratyes/MeinProjekt.git`.

---

## 2. SSH-Schlüssel erstellen

Um GitHub über SSH zu verbinden, habe ich überprüft, ob bereits ein SSH-Schlüssel vorhanden ist:

```bash
ls ~/.ssh/

## Schritte zum Erstellen eines SSH-Schlüssels

- SSH-Schlüssel mit `ssh-keygen` erzeugt und zu GitHub hinzugefügt.
Nach der Erstellung des Schlüssels habe ich den öffentlichen Schlüssel (id_rsa.pub) zu meinem GitHub-Konto unter SSH and GPG keys hinzugefügt.

## Lokales Klonen und Konfigurieren von Git

- Das Repository MeinProjekt wurde auf meinen lokalen Rechner geklont. Repository wurde mit `git clone git@github.com:uratyes/MeinProjekt.git` geklont. 
Ich habe nun das Repository auf meinen lokalen Rechner geklont und Git entsprechend konfiguriert:
git clone git@github.com:muratyes/MeinProjekt.git

- dann habe ich mit `git config user.name` und `git config user.email` konfiguriert.
git config user.name "Murat Yesilyurt"
git config user.email "deine_email@beispiel.com"

-Eine neue Datei main.py hinzugefügt und den ersten Commit durchgeführt:
git add main.py
git commit -m "Initialer Commit"

## Erstellen des Feature-Branches

- Ein neuer Branch "feature" wurde erstellt.
git checkout -b feature

- Eine neue Datei `utils/database.py` wurde hinzugefügt und committet.
git add utils/database.py
git commit -m "Neue Funktion hinzugefügt"


## Mergen des Feature-Branches in den Master-Branch
- Zuerst in den master Branch gewechselt:
git checkout master
- Dann den feature Branch in den master Branch gemergt:
git merge feature

- Merge-Konflikt wurde beim Mergen des Feature-Branches in den Master-Branch gelöst.
Während des Merges gab es einen Merge-Konflikt, da sowohl der master als auch der feature Branch Änderungen an derselben Datei vorgenommen hatten. Ich habe den Konflikt manuell aufgelöst, indem ich die entsprechenden Zeilen ausgewählt habe.

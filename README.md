# MeinProjekt - GitHub Repository Setup und Workflow

## Schritte zum Einrichten des GitHub-Repositorys

1. Repository auf GitHub erstellt.

Ich habe mich mit meinem Benutzernamen und Passwort bei meinem GitHub-Konto angemeldet. Klicken Sie oben rechts auf das „+“-Symbol und wählen Sie „Neues Repository“ aus. Ändern Sie den Namen des Repositorys in „MeinProjekt“ „Öffentlich“.
Mit einem Klick auf den Button „Repository erstellen“ habe ich den Vorgang abgeschlossen.

## Schritte zum Erstellen eines SSH-Schlüssels

```powershell
PS C:\Users\Nutzer> ls ~/.ssh/
    Directory: C:\Users\Nutzer\.ssh
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        26.11.2024     11:17            304 known_hosts
-a----        26.11.2024     11:15            112 known_hosts.old

SSH-Schlüssel mit ssh-keygen erzeugt und zu GitHub hinzugefügt.
PS C:\Users\Nutzer> ssh-keygen -t rsa -b 4096 -C "mr.yesilyurt@gmail.com"
Generating public/private rsa key pair.
Enter file in which to save the key (C:\Users\Nutzer/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in C:\Users\Nutzer/.ssh/id_rsa
Your public key has been saved in C:\Users\Nutzer/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:5swrtG6lLS/hJwZN4copAEYVDSBUloJ4A+PYHgJiflo mr.yesilyurt@gmail.com
The key's randomart image is:
+---[RSA 4096]----+
|@*+*=            |
|%=+. ..          |
|=++E . .         |
|.o+.  o          |
| o.. =  S        |
|  . = +=.        |
|   . + *+        |
|      @ o.       |
|     +.Bo        |
+----[SHA256]-----+
PS C:\Users\Nutzer> ls ~/.ssh/
    Directory: C:\Users\Nutzer\.ssh
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        13.02.2025     14:44           3381 id_rsa
-a----        13.02.2025     14:44            738 id_rsa.pub
-a----        26.11.2024     11:17            304 known_hosts
-a----        26.11.2024     11:15            112 known_hosts.old


Dann GitHub → Einstellungen → SSH- und GPG-Schlüssel → Neuer SSH-Schlüssel
Im Abschnitt „Titel“ habe ich „MeinProjekt_key“ eingetragen.
Als Schlüsseltyp habe ich „Authentifizierungsschlüssel“ gewählt.
Ich habe den von Ihnen kopierten SSH-Schlüssel in das Feld „Schlüssel“ eingefügt.
Ich habe auf die Schaltfläche „SSH-Schlüssel hinzufügen“ geklickt und den Schlüssel unten angezeigt. In der Zwischenzeit habe ich einige Male die Meldung „ungültiger Schlüssel“ erhalten.
Ich habe geprüft, ob ich das richtige Passwort kopiert habe.
Ich habe die Datei .ssh/id_rsa im Editor geöffnet und es von dort aus versucht.
Ich habe überprüft, ob die Option Dienste → OpenSSH-Authentifizierungsagent funktionierte. Meiner wurde gestoppt. Ich habe ihn neu gestartet und das Problem war behoben. Ich habe es manuell gestartet, aber Sie können es mit diesem Befehl starten: Start-Service ssh-agent
Dann habe ich mit diesem Befehl ssh-add C:\Users\Nutzer\.ssh\id_rsa meinen Schlüssel in den SSH-Agent geladen.
Zuletzt habe ich die SSH-Verbindung mit diesem Befehl getestet: ssh -T git@github.com
Hallo, Muratyes! Sie haben sich erfolgreich authentifiziert, aber GitHub bietet keinen Shell-Zugriff.

## Lokales Klonen und Konfigurieren von Git

PS C:\Users\Nutzer> d:
PS D:\> cd weiterbildung/webentwicklung
PS D:\weiterbildung\webentwicklung> git clone git@github.com:muratyes/MeinProjekt.git
Cloning into 'MeinProjekt'...
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Während des Klonvorgangs habe ich diesen Fehler erhalten: Um diesen Fehler zu beheben, musste ich eine .ssh/Config-Datei erstellen. Diese Datei enthielt den Verbindungspfad.

Host github.com
    Hostname github.com
    IdentityFile C:/Users/Nutzer/.ssh/id_rsa


PS D:\weiterbildung\webentwicklung> git clone https://github.com/muratyes/MeinProjekt.git
Cloning into 'MeinProjekt'...
warning: You appear to have cloned an empty repository.
PS D:\weiterbildung\webentwicklung> cd MeinProjekt
PS D:\weiterbildung\webentwicklung\MeinProjekt> git config user.name "Murat Yesilyurt"
PS D:\weiterbildung\webentwicklung\MeinProjekt> git config user.email "mr.yesilyurt@gmail.com"
PS D:\weiterbildung\webentwicklung\MeinProjekt> touch main.py
touch : The term 'touch' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ touch main.py
+ ~~~~~
    + CategoryInfo          : ObjectNotFound: (touch:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

touch komutu Power shell kullanilmadigini ögrendim ve onun yerine „New-Item main.py -ItemType File“ komutu ile main.py olusturdum :
New-Item main.py -ItemType File
PS D:\weiterbildung\webentwicklung\MeinProjekt> git add main.py
PS D:\weiterbildung\webentwicklung\MeinProjekt> git commit -m "Initialer Commit"
[main (root-commit) 740d50d] Initialer Commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 main.py


PS D:\weiterbildung\webentwicklung\MeinProjekt> git add main.py
PS D:\weiterbildung\webentwicklung\MeinProjekt> git commit -m "Initialer Commit"
[main (root-commit) 740d50d] Initialer Commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 main.py

## Erstellen des Feature-Branches
PS D:\weiterbildung\webentwicklung\MeinProjekt> git checkout -b feature
Switched to a new branch 'feature'
PS D:\weiterbildung\webentwicklung\MeinProjekt> New-Item -Path utils/database.py -ItemType File -Force

    Directory: D:\weiterbildung\webentwicklung\MeinProjekt\utils
Mode                 	LastWriteTime         		Length Name
----                		 -------------         		------ ----
-a----        		13.02.2025     15:54              	0 database.py


Dann habe ich diese Datei (utils/database.py) hinzugefügt und committed:

PS D:\weiterbildung\webentwicklung\MeinProjekt> git add utils/database.py
PS D:\weiterbildung\webentwicklung\MeinProjekt> git commit -m "Neue Funktion hinzugefügt"
[feature 7121a2f] Neue Funktion hinzugefügt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 utils/database.py

## Mergen des Feature-Branches in den Master-Branch

PS D:\> cd weiterbildung/webentwicklung/MeinProjekt
PS D:\weiterbildung\webentwicklung\MeinProjekt> git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)
PS D:\weiterbildung\webentwicklung\MeinProjekt> git branch master
PS D:\weiterbildung\webentwicklung\MeinProjekt> git checkout master
Switched to branch 'master'
PS D:\weiterbildung\webentwicklung\MeinProjekt> git add main.py
PS D:\weiterbildung\webentwicklung\MeinProjekt> git commit -m "Hauptdatei aktualisiert"

Abschließend werden Sie aufgefordert, den Feature-Branch in den Master-Branch zu integrieren:
PS D:\weiterbildung\webentwicklung\MeinProjekt> git merge feature
PS D:\weiterbildung\webentwicklung\MeinProjekt> git branch
  feature
  main
* master


----------------------------------------------------------------------------------------------------------------------
Konfliktlösung
Wenn während des Zusammenführungsvorgangs ein Konflikt auftritt, warnt Sie Git vor dem Konflikt und kennzeichnet die widersprüchlichen Dateien. In dieser Situation:

Zunächst werden die Codes untersucht. Weil Git anzeigt, welche Zeilen innerhalb der Konfliktdateien Konflikte verursachen. Hier können Sie sehen, welcher iv´cerik welcher Zweig ist. Somit werden fehlerhafte Inhalte direkt gelöscht und die Zeilen gelöscht und protokolliert.

<<<<<<< HEAD "Dies ist der Inhalt in Ihrem „Master“-Zweig" ======= "Inhalt in diesem "Feature"-Zweig" >>>>>>> Eigenschaften

Anschließend fügen wir es mit folgendem Befehl hinzu:
git add <konflikt_Datei>             # Fügen Sie die Datei, bei der der Konflikt behoben wurde, zum Staging-Bereich hinzu
git commit -m "Konflikt gelöst"      # Commit des Konflikts nach dessen Lösung

Nach dem Zusammenführungsvorgang werden die Änderungen übertragen.

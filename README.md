# MeinProjekt - GitHub Repository Setup und Workflow
## Schritte zum Einrichten des GitHub-Repositorys
1. Repository auf GitHub erstellt.
Ich habe mich mit meinem Benutzernamen und Passwort bei meinem GitHub-Konto angemeldet. Klicken Sie oben rechts auf das „+“-Symbol und wählen Sie „Neues Repository“ aus. Ändern Sie den Namen des Repositorys in „MeinProjekt“ „Öffentlich“.
Mit einem Klick auf den Button „Repository erstellen“ habe ich den Vorgang abgeschlossen.

## Schritte zum Erstellen eines SSH-Schlüssels
PS C:\Users\Nutzer> ls ~/.ssh/
    Directory: C:\Users\Nutzer\.ssh
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        26.11.2024     11:17            304 known_hosts
-a----        26.11.2024     11:15            112 known_hosts.old

- SSH-Schlüssel mit `ssh-keygen` erzeugt und zu GitHub hinzugefügt.
- PS C:\Users\Nutzer> ls ~/.ssh/
    Directory: C:\Users\Nutzer\.ssh
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        13.02.2025     14:44           3381 id_rsa
-a----        13.02.2025     14:44            738 id_rsa.pub
-a----        26.11.2024     11:17            304 known_hosts
-a----        26.11.2024     11:15            112 known_hosts.old

PS C:\Users\Nutzer> ssh-keygen -t rsa -b 4096 -C "mr.yesilyurt@gmail.com"
Generating public/private rsa key pair.
Enter file in which to save the key (C:\Users\Nutzer/.ssh/id_rsa):
C:\Users\Nutzer/.ssh/id_rsa already exists.
Overwrite (y/n)? y
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
PS C:\Users\Nutzer>

Dann Github→Einstellungen → SSH- und GPG-Schlüssel → Neuer SSH-Schlüssel
Im Abschnitt „Titel“ habe ich „MeinProjekt_key“ eingetragen.
Als Schlüsseltyp habe ich „Authentifizierungsschlüssel“ gewählt.
Ich habe den von Ihnen kopierten SSH-Schlüssel in das Feld „Schlüssel“ eingefügt.
Ich habe auf die Schaltfläche „SSH-Schlüssel hinzufügen“ geklickt und den Schlüssel unten angezeigt. In der Zwischenzeit habe ich einige Male die Meldung „ungültiger Schlüssel“ erhalten.
1. Ich habe geprüft, ob ich das richtige Passwort kopiert habe.
2. Ich habe die Datei .ssh/id_rsa im Editor geöffnet und es von dort aus versucht.
3. Ich habe überprüft, ob die Option Dienste → OpenSSH-Authentifizierungsagent funktionierte. Meiner wurde gestoppt. Ich habe ihn neu gestartet und das Problem war behoben. Ich habe es manuell gestartet, aber Sie können es mit diesem Befehl starten: „Start-Service ssh-agent“
Dann habe ich mit diesem Befehl „ssh-add C:\Users\Nutzer\.ssh\id_rsa“ meinen Schlüssel in den SSH-Agent geladen.
Zuletzt habe ich die SSH-Verbindung mit diesem Befehl getestet: „ssh -T git@github.com“

Hallo, Muratyes! Sie haben sich erfolgreich authentifiziert, aber GitHub bietet keinen Shell-Zugriff.
## Lokales Klonen und Konfigurieren von Git

- Repository wurde mit `git clone git@github.com:DeinBenutzername/MeinProjekt.git` geklont.
- Git wurde mit `git config user.name` und `git config user.email` konfiguriert.

## Erstellen des Feature-Branches

- Ein neuer Branch "feature" wurde erstellt.
- Eine neue Datei `utils/database.py` wurde hinzugefügt und committet.

## Mergen des Feature-Branches in den Master-Branch

- Merge-Konflikt wurde beim Mergen des Feature-Branches in den Master-Branch gelöst.

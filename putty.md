SSH Putty 
====

# Ziel

Das Ziel ist über Putty auf die TBZ Linux Maschine zugreiffen zu können ohne sich jedesmal mit dem PW Anzumelden.

# Putty Private Key hinterlegen

- Als erstes verbindet man auf die TBZ Linux Maschine

- Schüsselpaar für SSH erstellen 
   ```
   ssh-keygen -t rsa
   ```

   - Erstellten öffentlichen Schlüsselteil auf der Linux Maschine zu den bekannten Schlüssel hinzufügen
   ```
   cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
   ```

   - Inhalt des private Schlüssels anzeigen
   ```
   cat ~/.ssh/id_rsa
   ```
- Inhalt des Public Schlüssels anzeigen
   ```
   cat ~/.ssh/id_rsa.pub
   ```

- Markiere den kompletten private Schlüssel und koppiere ihn in ein leheres Text File auf deinem Winodws Desktop Computer

![SSHKey](images/puttyssh.jpg)

- Öffne das Schlüsselprogramm Puttygen und unter `Conversions > Import Key` lade das soeben erstellte Textfile 

- Dann gehe auf `File > Save private key` und sichere die Schlüsseldatei im `ppk` Format, bestätige die rückfrage mit yes.

- Nun muss man in Putty nur noch das neu erstellte ppk File unter ` Connection > SSH > Auth unter "Private key file for authentivation"` angegeben werden

- Definiere unter `Connection Data > Auto-login username` deinen Loginnamen `ubuntu`

- Unter `Session > Hostname` gib deine IP Adresse ein und speichere das ganze in `Saved Sessions` unter einem belibigen Namen ab. 

---

> [⇧ **Zurück zur Basic Seite**](/basic/README.md)

---

SSH Basic 
====
Das Ziel ist, einen Überblick über einige grundlegende SSH Kommandos und Workflows zu geben.

### Workflows
***

![GitHub](/github.png)***SSH Key zu GitHub hinzufügen*** 

1. Lokalen SSH Key erstellen (falls noch nicht vorhanden)
    ``` 
      $ ssh-keygen -t rsa 
    ``` 
2. Public SSH Key anzeigen und den Inhalt koppieren
    ```
     $ cat ~/.ssh/id_rsa.pub 
    ```
3. Zu Github wechseln, auf Benutzerkonto klicken, **Settings** aufrufen und zu **SSH und GPG keys** wechseln
4. Auf **New SSH key** klicken
5. **Title** vergeben und den zuvor kopierten Key einfügen und auf **Add SSH key** klicken

![AWS](/amazon_icon.png)***Auf EC2 Instance verbinden*** 

1. Mit folgendem Befehl kann auf die EC2 Instance verbunden werden.
    ``` 
      $ ssh -i <Pfad Public Key.PEM> <username>@<public-ip>
      $ ssh -i "labsuser.pem" ec2-user@3.81.45.73
    ``` 

### Basic SSH Commands 
***
| Behfehl | Beschreibung |
| ---     | ---   |
|`ssh-keygen -t rsa` | **Neuen SSH Key erstellen**| 
| `cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys` | **Neuen SSH Key in authorized_keys hinzufügen** | **
| `cat ~/.ssh/id_rsa` | Privaten SSH Key anzeigen |
| `cat ~/.ssh/id_rsa.pub` | **Public SSH Key anzeigen** | 
| `ssh-keygen --help` | Übersicht Befehls Optionen |
| `ssh-keygen -t ecdsa -f ./test_ecdsa_key -N ''`| Genieriert neuen Key "-t ecdsa" = Key Type und -f ./test_ecdsa_key = File und -N '' = lehrer Keypharse   |
| `ssh-copy-id -i ~/test_ecdsa_key.pub user1@10.10.5.5`| Koppiert Public Key zu User1 auf Remote Maschine |
| `ssh -i ~/test_ecdsa_key user1@10.10.5.5` | **Private Key mitgeben um ohne PW auf die Remote Maschine zu verbinden** |
| `ssh-keygen -f test_ecdsa_key -p -P "" -N "12345"` | `-f File und -p -P "Altes Passwort" -N "Neues Passwort"` |
| `/usr/sbin/sshd -p 8888 -d`| SSH Demond in Debugg mode starten auf Port 8888    |
| `eval "$(ssh-agent -s)"`| output of ssh-agent as shell commands |
| `ssh-add test_ecdsa_key`| Fügt das Passwort für den Privat Key dem ssh-agent hinzu    |

### SSH Agent Commands 
***
| Behfehl | Beschreibung |
| ---     | ---   |
| `ssh-add -l` | **ssh key in agent anzeigen**| 
| `ssh-agent` | **agent starten** | **
| `output in Console posten` | agent starten |
| `ssh-add ~/.ssh/id_rsa` | agent mit private key verknüpfen |

### SSH Port Forwading
***
Local Computer 
TBZ Rechner : 10.3.44.12 /ubuntu / Equahxi8
Client: 10.10.5.6 / user1 /tbz4ever

| Where| Behfehl | Beschreibung |
|--- | ---     | ---   |
|On Local Computer | `ssh -L 33333:10.10.5.6:22 ubuntu@10.3.44.12` | Forwading von local Port 33333 auf Client Port 22 über TBZ Rechner |
|On Local Computer -> In new Shell | `ssh user1@localhost -p 33333`| Verbindet SSH auf den Localhost Port 33333 mit user1   |


### SSH 2 AWS
***
| Behfehl | Beschreibung |
| ---     | ---   |
| `ssh -i "dam-key-new.pem" ubuntu@ec2-18-208-130-205.compute-1.amazonaws.com` | Verbinde auf AWS Instance with Local Maschin und keypair |
| `chmod 400 dam-key-new.pem`| Berrechtigungen für Keyfile richtig konfigurieren   |

---

> [⇧ **Back to top**](#Ziel)

---

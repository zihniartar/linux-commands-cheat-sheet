# linux-commands-cheat-sheet


# Linux/Ubuntu Server Cheatlist

## Systemverwaltung

### System-Informationen
```bash
uname -a           # Kernel-Version anzeigen
lsb_release -a     # Distribution anzeigen
hostnamectl        # Hostname und OS-Informationen anzeigen
```

### Paketverwaltung
```bash
sudo apt update            # Paketlisten aktualisieren
sudo apt upgrade           # Alle Pakete aktualisieren
sudo apt install <paket>   # Paket installieren
sudo apt remove <paket>    # Paket entfernen
sudo apt autoremove        # Nicht mehr benötigte Pakete entfernen
```

### Dienstverwaltung
```bash
sudo systemctl status <dienst>     # Dienststatus anzeigen
sudo systemctl start <dienst>      # Dienst starten
sudo systemctl stop <dienst>       # Dienst stoppen
sudo systemctl restart <dienst>    # Dienst neu starten
sudo systemctl enable <dienst>     # Dienst beim Booten aktivieren
sudo systemctl disable <dienst>    # Dienst beim Booten deaktivieren
```

## Dateimanagement

### Navigation und Verzeichnisse
```bash
pwd                           # Aktuelles Verzeichnis anzeigen
ls                            # Dateien und Verzeichnisse auflisten
ls -la                        # Ausführliche Liste anzeigen
cd <verzeichnis>              # Verzeichnis wechseln
mkdir <verzeichnis>           # Neues Verzeichnis erstellen
rmdir <verzeichnis>           # Leeres Verzeichnis löschen
```

### Dateien kopieren und verschieben
```bash
cp <quelle> <ziel>            # Datei kopieren
cp -r <quelle> <ziel>         # Verzeichnis rekursiv kopieren
mv <quelle> <ziel>            # Datei oder Verzeichnis verschieben/umbenennen
```

### Dateien löschen
```bash
rm <datei>                    # Datei löschen
rm -r <verzeichnis>           # Verzeichnis rekursiv löschen
rm -f <datei>                 # Datei ohne Bestätigung löschen
```

## Rechteverwaltung

### Dateirechte anzeigen und ändern
```bash
ls -l                        # Dateirechte anzeigen
chmod u+x <datei>            # Ausführungsrechte für den Besitzer hinzufügen
chmod 755 <datei>            # Setzt Rechte auf rwxr-xr-x
chown <benutzer>:<gruppe> <datei>  # Besitzer und Gruppe ändern
```

### Beispiele für `chmod`
```bash
chmod 644 <datei>            # Rechte auf rw-r--r-- setzen
chmod 600 <datei>            # Rechte auf rw------- setzen
chmod +x <datei>             # Datei ausführbar machen
```

## Nginx-Verwaltung

### Nginx installieren
```bash
sudo apt update
sudo apt install nginx
```

### Nginx-Dienst verwalten
```bash
sudo systemctl start nginx          # Nginx starten
sudo systemctl stop nginx           # Nginx stoppen
sudo systemctl restart nginx        # Nginx neu starten
sudo systemctl reload nginx         # Nginx-Konfiguration neu laden
sudo systemctl enable nginx         # Nginx beim Booten aktivieren
sudo systemctl disable nginx        # Nginx beim Booten deaktivieren
```

### Nginx-Konfiguration
```bash
sudo nano /etc/nginx/nginx.conf                 # Hauptkonfigurationsdatei bearbeiten
sudo nano /etc/nginx/sites-available/default    # Standard-Serverblock bearbeiten
sudo ln -s /etc/nginx/sites-available/<site> /etc/nginx/sites-enabled/    # Site aktivieren
sudo rm /etc/nginx/sites-enabled/<site>         # Site deaktivieren
sudo nginx -t                                   # Nginx-Konfiguration testen
sudo systemctl reload nginx                     # Nginx-Konfiguration neu laden
```

### Nginx-Logs
```bash
sudo tail -f /var/log/nginx/access.log    # Access-Log anzeigen
sudo tail -f /var/log/nginx/error.log     # Error-Log anzeigen
```

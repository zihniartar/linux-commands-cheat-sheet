
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

## FTP

### FTP installieren
```bash
sudo apt update
sudo apt install vsftpd
```

### FTP-Dienst verwalten
```bash
sudo systemctl start vsftpd          # FTP starten
sudo systemctl stop vsftpd           # FTP stoppen
sudo systemctl restart vsftpd        # FTP neu starten
sudo systemctl enable vsftpd         # FTP beim Booten aktivieren
sudo systemctl disable vsftpd        # FTP beim Booten deaktivieren
```

### FTP-Konfiguration
```bash
sudo nano /etc/vsftpd.conf           # FTP-Konfigurationsdatei bearbeiten
```

## wget

### Dateien herunterladen
```bash
wget <url>                          # Datei von URL herunterladen
wget -c <url>                       # Abgebrochenen Download fortsetzen
```

## zip und tar

### zip

### Dateien und Verzeichnisse komprimieren
```bash
zip -r archiv.zip <verzeichnis>      # Verzeichnis in ZIP-Archiv komprimieren
zip datei.zip <datei>                # Datei in ZIP-Archiv komprimieren
```

### Dateien und Verzeichnisse entpacken
```bash
unzip archiv.zip                     # ZIP-Archiv entpacken
```

### tar

### Dateien und Verzeichnisse komprimieren
```bash
tar -cvf archiv.tar <verzeichnis>    # Verzeichnis in TAR-Archiv komprimieren
tar -czvf archiv.tar.gz <verzeichnis> # Verzeichnis in TAR.GZ-Archiv komprimieren
```

### Dateien und Verzeichnisse entpacken
```bash
tar -xvf archiv.tar                  # TAR-Archiv entpacken
tar -xzvf archiv.tar.gz              # TAR.GZ-Archiv entpacken
```

## SSL

### SSL-Zertifikate erstellen und verwalten
```bash
sudo apt install openssl
openssl genrsa -out privkey.pem 2048          # Privaten Schlüssel generieren
openssl req -new -key privkey.pem -out cert.csr # CSR erstellen
openssl x509 -req -days 365 -in cert.csr -signkey privkey.pem -out cert.pem # Selbstsigniertes Zertifikat erstellen
```

## MySQL

### MySQL installieren
```bash
sudo apt update
sudo apt install mysql-server
```

### MySQL-Dienst verwalten
```bash
sudo systemctl start mysql          # MySQL starten
sudo systemctl stop mysql           # MySQL stoppen
sudo systemctl restart mysql        # MySQL neu starten
sudo systemctl enable mysql         # MySQL beim Booten aktivieren
sudo systemctl disable mysql        # MySQL beim Booten deaktivieren
```

### MySQL-Befehle
```bash
sudo mysql_secure_installation      # MySQL sichern
mysql -u root -p                    # MySQL-Client mit root-Benutzer starten
```

## MS-SQL

### MS-SQL installieren
```bash
sudo apt update
sudo apt install mssql-server
sudo /opt/mssql/bin/mssql-conf setup
```

### MS-SQL-Dienst verwalten
```bash
sudo systemctl start mssql-server   # MS-SQL starten
sudo systemctl stop mssql-server    # MS-SQL stoppen
sudo systemctl restart mssql-server # MS-SQL neu starten
sudo systemctl enable mssql-server  # MS-SQL beim Booten aktivieren
sudo systemctl disable mssql-server # MS-SQL beim Booten deaktivieren
```

## IP-Adresse

### IP-Adresse anzeigen
```bash
ip addr show                        # IP-Adressen anzeigen
hostname -I                         # Nur IP-Adressen anzeigen
```

### Netzwerk neu starten
```bash
sudo systemctl restart networking   # Netzwerkdienst neu starten
```

## chmod

### Dateirechte ändern
```bash
chmod 755 <datei>                   # Rechte auf rwxr-xr-x setzen
chmod 644 <datei>                   # Rechte auf rw-r--r-- setzen
chmod u+x <datei>                   # Ausführungsrechte für den Besitzer hinzufügen
```

### Beispiele für `chmod`
```bash
chmod 644 <datei>                   # Rechte auf rw-r--r-- setzen
chmod 600 <datei>                   # Rechte auf rw------- setzen
chmod +x <datei>                    # Datei ausführbar machen
```

## SSL

### SSL-Zertifikate erstellen und verwalten
```bash
sudo apt install openssl
openssl genrsa -out privkey.pem  &#8203;:citation[oaicite:0]{index=0}&#8203;

```


## Smartstore

### Smartstore.Web ausführbar machen
```bash
chmod +x Smartstore.Web           # Make Smartstore.Web executable
# Set file und folder rights - begin
chown -R www-data /var/www/smartstore/ && 
chgrp -R www-data /var/www/smartstore/ &&
chmod -R 750 /var/www/smartstore/ &&
chmod g+s /var/www/smartstore/ &&
chmod -R g+w /var/www/smartstore/App_Data &&
chmod -R g+w /var/www/smartstore/Modules &&
chmod +x Smartstore.Web
# Set file und folder rights - end
```

### Datei- und Ordnerrechte setzen
```bash
chown -R www-data /var/www/smartstore/ && 
chgrp -R www-data /var/www/smartstore/ &&
chmod -R 750 /var/www/smartstore/ &&
chmod g+s /var/www/smartstore/ &&
chmod -R g+w /var/www/smartstore/App_Data &&
chmod -R g+w /var/www/smartstore/Modules &&
chmod +x Smartstore.Web
```


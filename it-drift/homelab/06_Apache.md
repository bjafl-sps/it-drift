# Installasjon og oppsett av Apache Webserver

## 1. Forberedende tiltak

### Systemoppdatering
```bash
# Oppdater pakkelister og system
sudo apt update
sudo apt upgrade -y
```

### Nettverkskonfigurasjon
```bash
# Sjekk IP-adresse og nettverksstatus
ip a
# Test internettforbindelse
ping -c 4 8.8.8.8
```

## 2. Apache installasjon

### Installer Apache
```bash
# Installer Apache webserver
sudo apt install apache2 -y

# Sjekk status
sudo systemctl status apache2
```

### Aktiver ved oppstart
```bash
# Sørg for at Apache starter ved boot
sudo systemctl enable apache2
```

## 3. Brannmurkonfigurasjon

### UFW oppsett
```bash
# Sjekk UFW status
sudo ufw status

# Aktiver nødvendige tjenester
sudo ufw allow OpenSSH
sudo ufw allow 'Apache Full'

# Aktiver brannmur
sudo ufw enable
```

## 4. Test og verifisering

### Test Apache
```bash
# Test Apache konfigurasjon
sudo apache2ctl configtest

# Sjekk versjon
apache2 -v
```

### Test webtilgang
1. Fra serveren:
   ```bash
   curl localhost
   ```

2. Fra din PC:
   - Åpne nettleser
   - Gå til: http://[server-ip-adresse]

## 5. Grunnleggende konfigurasjon

### Mappestruktur
```bash
# Standardmapper
/var/www/html/         # Webroot
/etc/apache2/          # Konfigurasjonsfiler
/var/log/apache2/      # Logger
```

### Rettigheter
```bash
# Sett riktige rettigheter
sudo chown -R www-data:www-data /var/www/html
sudo chmod -R 755 /var/www/html
```

## 6. Opprett testside

### Lag en enkel testside
```bash
# Opprett index.html
sudo nano /var/www/html/index.html
```

Innhold for index.html:
```html
<!DOCTYPE html>
<html>
<head>
    <title>Min Testserver</title>
</head>
<body>
    <h1>Homelab Webserver</h1>
    <p>Dette er min første Apache webserver!</p>
</body>
</html>
```

## 7. Loggføring og overvåking

### Sjekk logger
```bash
# Tilgangslogg
sudo tail -f /var/log/apache2/access.log

# Feillogg
sudo tail -f /var/log/apache2/error.log
```

## 8. Sikkerhetstiltak

### Grunnleggende sikkerhet
```bash
# Fjern serverinformasjon
sudo nano /etc/apache2/conf-enabled/security.conf
```
Sett følgende verdier:
```apache
ServerTokens Prod
ServerSignature Off
```

### Restart Apache
```bash
sudo systemctl restart apache2
```

## Dokumentasjon
Noter ned:
- Apache versjon
- Åpne porter
- Brannmurkonfigurasjon
- Mappestruktur og rettigheter
- URL til testside

## Feilsøking
- Apache starter ikke: Sjekk logger og konfigurasjon
- Nettside ikke tilgjengelig: Sjekk brannmur og nettverksoppsett
- Rettighetsproblemer: Verifiser mappetilganger

## Neste steg
- Sette opp virtuell host
- Konfigurere SSL/HTTPS
- Implementere bedre sikkerhet
- Sette opp egen nettside
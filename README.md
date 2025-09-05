# ATAK
ATAK in the UK

This repository contains miscellaneous files related to using ATAK:

## 1. WallpaperATAK.jpg
This is a wallpaper based on the ATAK splashscreen and includes AJ Johansson's "TAK is the Way"slogan.

## 2. takserver_renewLE24.sh
This is a bash script for use on a TAK server which employs Let's Encrypt public server certificates. It is based on the version 002 script published by the TAK syndicate, with the following updates
- Checks that nothing is running on port 80 to prevent certbot conducting an http challenge validation;
- Checks to see if the script has had a hostname added in the configuration section;
- Uses the password data contained in the CoreConfig.xml file on the TAK server rather than a hardcoded password; and
- logs to the syslog rather than std out.

## 3. taklecr
This is an extension and replacement for takserver_renewLE.  It checks the validity of the LE certificate by querying it on the public port (by default 8446). If the the certificate life is less that the renewal threshold it conducts a certificate renewal.  The script can be triggered by either creating a cronjob or using the systemd service and timer files included in this repo.  
To install: copy the file to the /usr/local/bin directory Then:
```
chown root:takadmin /usr/local/bin/taklecr
chmod 710 /usr/local/bin/taklecr
```

## 4. taklecr.service
This is the systemd service file to be used in conjuction with the taklecr script and taklecr timer.  
To install: copy the file to /etc/systemd/system/ directory Then:
```
chown root: /etc/systemd/system/taklecr.service
chmod 644 /etc/systemd/system/taklecr.service
systemctl daemon-reload
```
Once you have instaled the script edit the script and change the configuration values in the configuration section to reflect the setup of your TAK server.  If you have a default set up this will only require changing the line certNameVar="PUT_DOMAIN_HERE" to you domain name - eg: certNameVar="tak.example.com".

## 5. taklecr.timer
This is the systemd timer file to run the taklecr command every day at 04:00. It is used in conjuction with the taklecr script and taklecr service files.  
To install: copy the file to /etc/systemd/system/ directory Then:
```
chown root: /etc/systemd/system/taklecr.timer
chmod 644 /etc/systemd/system/taklecr.timer
systemctl daemon-reload
systemctl start taklecr.timer
systemctl enable taklecr.timer
```

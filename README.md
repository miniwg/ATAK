# ATAK
ATAK in the UK

This repository contains miscellaneous files related to using ATAK:

1. WallpaperATAK.jpg
This is a wallpapaer based on the ATAK splashscreen and includes AJ Johansson's "TAK is the Way"slogan.

2. takserver_renewLE23.sh
This is a bash script for use on a TAK server which employs Let's Encrypt public server certificates. It is based on the version 002 script published by the TAK syndicate, with the following updates
- Checks to see if the script has had a hostname added in the configuration section;
- Uses the password data contained in the cert-metadata.sh file on the TAK server rather than a hardcoded password; and
- logs to the syslog rather than std out.





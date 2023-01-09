# Template clamav
## Overview

This template for ClamAV


The template adds monitoring of:

* ClamAV Service
* ClamAV Version
* ClamAV DB Version

The following agent parameters can be used to add the metrics into Zabbix:

UserParameter=clamav.version,/usr/bin/clamscan --version  | awk 'BEGIN { FS="/" } { print $1}' | awk '{print $2}'
UserParameter=clamav.dbversion,/usr/bin/clamscan --version  | awk 'BEGIN { FS="/" } { print $2}'
UserParameter=clamav.update_date,/usr/bin/clamscan --version  | awk 'BEGIN { FS="/" } { print $3}'
UserParameter=clamav.dbage,echo $(( $(date +"%s") - $(date -d "$(/usr/bin/clamscan --version  | awk 'BEGIN { FS="/" } { print $3}')" +"%s") ))

## Author

Dorofeev Andrei
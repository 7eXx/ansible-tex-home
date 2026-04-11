# Ansible Tex Home
This contains a series of playbook ansible to create the homelab infrastructure

## Precheck
Allow GPU passthrough.  
To allow Intel GPU passthrough, change permissions to 666 for the following dirs:
- /dev/dri/card0
- /dev/dri/renderD128

Then go to Synology > Scheduled Tasks, add script to change permissions at every boot.

# Self signed certificate for Registry
To work with self signed certificates in docker registry:
- copy certificate crt on `/var/db/ca-certificates`
- set proper permission wih 
    - `sudo chmod 644 /var/db/ca-certificates/cert.crt`
- update certificates with script:
    - `sudo /usr/syno/bin/update-ca-certificates.sh`
- portainer bind mount certs folder inside container (see docker-compose.yaml)

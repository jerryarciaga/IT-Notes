# Nextcloud
**NextCloud** is an open source collaboration software that started as a fork of Owncloud. Now, it has evolved into a full-fledged collaboration software offering file-, calendar-, and contact-syncing, plus much more.

# Deployment Design
I will be basing this deployment design off of the Fedora Magazine article I found. This deployment will consist of the Nextcloud instance and a database, all within the same network. Here the commands provided are a little loose, so I would like to set some more parameters on it.
## Container / Images
In this case, I will be using the Nextcloud Apache httpd + MariaDB installation.
## Volumes
Volumes are used to persist data between updates or shutdowns/reboots.;; 

---
Related Links
[Install NextCloud via Podman](https://fedoramagazine.org/nextcloud-20-on-fedora-linux-with-podman/)

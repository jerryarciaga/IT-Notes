# TO DO
- [ ] Manage secrets such as admin and database credentials.
- [ ] Turn this guide into a compose file for an automated build.
- [ ] Update GitHub repository with said compose file.
# What is Nextcloud?
**Nextcloud** is an open source collaboration software that started as a fork of Owncloud. Now, it has evolved into a full-fledged collaboration software offering file-, calendar-, and contact-syncing, plus much more.

# Deployment Design
I will be basing this deployment design off of the Fedora Magazine article I found. This deployment will consist of the Nextcloud instance and a database, all within the same network. Here the commands provided are a little loose, so I would like to set some more parameters on it.
## Container / Images
In this case, I will be using the Nextcloud Apache httpd + MariaDB installation.
* `docker.io/library/nextcloud:20` - Nextcloud container
* `docker.io/library/mariadb:10` - MariaDB
## Volumes
Volumes are used to persist data between updates or shutdowns/reboots. It is also recommended to have volumes for the database, the container, and the data folder in separate volumes. As such, I will be following the guide in creating the following volumes:
* `nextcloud-app`
* `nextcloud-data`
* `nextcloud-db`
## Networking
Finally, networking also has to be considered in this project. This also demonstrates the concept of network segmentation.
# Deploying Nextcloud
All commands can be run using privileged or rootless.
## Configure your networking
The following commands allow you to create a DNS zone with the name `dns.podman`. This can be useful because any container in this network are reachable via `container_name.dns.podman`.
```
# Creating a new network
$ podman network create nextcloud-net

# Listing all networks
$ podman network ls

# Inspecting a network
$ podman network inspect nextcloud-net
```
## Prepare your volumes
This step can actually be skipped, but is recommended for persistence.
```
# Creating the volumes
$ podman volume create nextcloud-app
$ podman volume create nextcloud-data
$ podman volume create nextcloud-db

# Listing volumes
$ podman volume ls

# Inspecting volumes (also provides the full path)
$ podman volume inspect nextcloud-app
```
## Deploy the containers
Networking and volumes are now prepared and ready to go. Finally, we can start using them in our deployment.
### Deploy MariaDB
According to the MariaDB image documentation, we need to provide some additional environment variables. We also would need to attached the volume, connect it to the network and provide a name to the container.
Note that you would have to replace `DB_USER_PASSWORD` and `DB_ROOT_PASSWORD` with respective passwords. We can get into secrets management once I learn secrets management using Podman.
```
# Deploy MariaDB
$ podman run --detach \
	--env MYSQL_DATABASE=nextcloud \
	--env MYSQL_USER=nextcloud \
	--env MYSQL_PASSWORD=DB_USER_PASSWORD \
	--env MYSQL_ROOT_PASSWORD=DB_ROOT_PASSWORD \
	--volume nextcloud-db:/var/lib/mysql \
	--network nextcloud-net \
	--restart on-failure \
	--name nextcloud-db \
	docker.io/library/mariadb:10
```
### Deploy Nextcloud
After successfully starting the MariaDB container, we can finally start the Nextcloud container. Replace `DB_USER_PASSWORD`, `NC_ADMIN` and `NC_PASSWORD` with the usernames and passwords. 
```
# Deploy Nextcloud
$ podman run --detach \
	--env MYSQL_HOST=nextcloud-db.dns.podman \
	--env MYSQL_DATABASE=nextcloud \
	--env MYSQL_USER=nextcloud \
	--env MYSQL_PASSWORD=DB_USER_PASSWORD \
	--env NEXTCLOUD_ADMIN_USER=NC_ADMIN \
	--env NEXTCLOUD_ADMIN_PASSWORD=NC_PASSWORD \
	--volume nextcloud-app:/var/www/html \
	--volume nextcloud-data:/var/www/html/data \
	--network nextcloud-net \
	--restart on-failure \
	--name nextcloud \
	--publish 8080:80 \
	docker.io/library/nextcloud:20

# Check running containers
$ podman container ls
```
Now that both containers are running, you can now configure these containers. Notice the line `--publish 8080:80` starts up the container such that `port 80` in the container gets mapped into `port 8080` in the host. Fire up a browser and point into `localhost:8080`. This should load up your self-hosted Nextcloud site. If not, you may want to wait a couple minutes or wait until `podman ps` shows the containers `nextcloud` and `nextcloud-db` both as `Up`.

---
Related Links
[Install NextCloud via Podman](https://fedoramagazine.org/nextcloud-20-on-fedora-linux-with-podman/)

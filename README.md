# My Proxmox Installation Steps


Step1:
Install Proxmox from USB

Step2:
```
lvremove /dev/pve/data
lvresize -l +100%FREE /dev/pve/root
resize2fs /dev/mapper/pve-root
```

Now to go your Datacenter, Storage, select local-lvm then remove.
Now select local, edit under content: add disk image and container, OK.

Now move down to pve host, select Repositories, click Add
In Repository: select No-Subscription then click add.

Move up to Updates section:
click refresh, now click Upgrade.

Now go to your shell then type in:
```
pveam update
```

```
bash -c "$(wget -qLO - https://github.com/tteck/Proxmox/raw/main/misc/post-pve-install.sh)"
```
#### The system will reboot automatically.

Step3:
### Adding username
```
adduser localusers
usermod -aG sudo localusers
apt update && apt upgrade -y
apt install -y sudo bash unzip nano wget curl git 
```

#


## Troubleshooting Docker Container

#### Start HERE!

To stop and remove all containers at once, you can use:
```
docker ps -a
```
```
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
docker volume ls
docker volume prune -f
docker network ls
docker network prune -f
docker image prune -a -f
docker volume prune --filter all=1 -f
docker volume ls --filter "dangling=true"
docker ps --filter "status=exited"
docker ps --format {{.Names}}
```
### removing directory
````
rm -rf /path/to/nextcloud/data
rm -rf /path/to/nextcloud/config
````
### Recreating docker
```
docker compose up -d --force-recreate
docker compose up -d --rebuild
docker compose up -d --build
```
#### End HERE!



### How to use wget from terminal
Check out the sample below:

```
wget https://raw.githubusercontent.com/francisuadm/nextcloud/main/Installer.g2g.sh
sudo chmod +x Installer.g2g.sh
sudo ./Installer.g2g.sh
```

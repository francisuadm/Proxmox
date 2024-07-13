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
apt install -y sudo bash unzip nano wget
```


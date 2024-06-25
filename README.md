# raspberry-pi-portainer
My custom Raspberry Pi Portainer setup and configuration. 

## Setup

Execute the following command:

```
sudo raspi-config
```

To turn on the following
- Interfaces > VNC > Enable
- System Options > Network at Boot > Yes
- Display Options > VNC Resolution > Highest
- Update

Set the Raspberry Pi's [Static IP Address](https://www.tomshardware.com/how-to/static-ip-raspberry-pi)

Install Vim

```
sudo apt install vim
```

Update and Upgrade Raspberry Pi

Execute the following commands:

```
sudo apt-get update
sudo apt full-upgrade
sudo reboot
```

Install [Docker](https://docs.docker.com/engine/install/raspberry-pi-os/#uninstall-old-versions)

Execute the following commands:

```
curl -fsSL https://get.docker.com | sh
sudo usermod -aG docker $USER
```

Install [Portainer](https://hub.docker.com/r/portainer/portainer-ce/tags)

*Look for the latest version with OS/ARCH = linux/arm/v7*

```
sudo docker pull portainer/portainer-ce:alpine-sts

sudo docker run -d -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:alpine-sts
```

In Portainer set the following: 

1. Settings > General > [App Templates](https://github.com/novaspirit/pi-hosted?tab=readme-ov-file#login-to-portainer-to-update-the-app-template)

```
https://raw.githubusercontent.com/pi-hosted/pi-hosted/master/template/portainer-v2-arm32.json
```

2. Environment-related > Environments > local > Public IP. 

Use the Raspberry Pi's IP Address. For example: 192.168.x.x
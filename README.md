# Cray-Zero-2-W

## Based on
- https://www.clustered-pi.com/blog/clustered-pi-zero.html#stl-files
- ansible playbook

## Setup Steps

I tried making an image and cloning but could not get working, so just loaded OS on each SD card
- load Debian Lite SD card
- login on Pi 4 with keyboard and monitor
- set static IP
  - `sudo nmtui edit "preconfigured"`
  - set: Address, Gateway, DNS
- add root password
  - `sudo passwd root`
- allow root ssh
  - `sudo nano /etc/ssh/ssd_config`
  - `PermitRootLogin yes`
- place in Pi Zero 2 W and confirm I can ssh into it

## Automated build of HA k3s Cluster with `kube-vip` and MetalLB

![Fully Automated K3S etcd High Availability Install](https://img.youtube.com/vi/CbkEWcUZ7zM/0.jpg)

- based on this repo: https://github.com/techno-tim/k3s-ansible


## Create Admin Machine
- created a Debian instance on Windows using WSL
- ensure you are logged in as root
- install Ansible
  - `sudo apt update`
  - `sudo apt upgrade -y`
  - `sudo apt install ansible`
  - `sudo apt install sshpass`
- add in `ansible.cfg` and `hosts.ini`
- install some requirements for ansible:
  - `ansible-galaxy collection install kubernetes.core`
  - `ansible-galaxy install -r ./collections/requirements.yml`
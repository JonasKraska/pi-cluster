# Network

## Prerequisites
- [pi imager](https://www.raspberrypi.com/software/) `sudo apt install rpi-imager`
- [nmap](https://nmap.org) `sudo apt install nmap`
- [ansible](https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html) `sudo add-apt-repository --yes --update ppa:ansible/ansible && sudo apt install ansible`

## Initialization

- flash all need SD card with the prefered OS (make sure to configure the ssh access via the pi imager settings)
- power up pi boards and connect them to the network
- execute `sudo nmap -sP 192.168.178.0/24` to identify the pi IP and MAC addresses

## Setup

- ssh into the individual pi computers and run `sudo raspi-config` > `Advanced Options` > `Expand Filesystem` (reboot on finish)
- adjust `vars.yml` by inserting all the desired IP addresses and hostname given the corresponding MAC addresses obtained from the nmap scan (MAC addresses have to be lower case for ansible to work)
- run `ansible-playbook -i inventory main.yml`
- restart all nodes via the ansible command `ansible all -i inventory -m shell -a "sleep 1s; shutdown -r now" -b -B 60 -P 0`


## Sources

- https://www.pidramble.com/wiki/setup/network
- https://github.com/geerlingguy/raspberry-pi-dramble/tree/master/setup/networking
- https://www.daemon-systems.org/man/dhcpcd.conf.5.html
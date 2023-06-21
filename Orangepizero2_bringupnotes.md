# Notes on bringing up Orange Pi Zero 2 headless

Using Ubuntu Focal server OS, version Orangepizero2_2.2.0_ubuntu_focal_server_linux4.9.170
Connect serial to usb converter with voltage selected as 3.3V

`screen /dev/ttyUSB0 115200`

username:`root`
password:`orangepi`

Use `orangepi-config` to set static ip, wifi etc.

Login as root and add your preferred <username>
`adduser <username>`
`usermod -aG sudo <username>`
`groups <username>` to inspect the user groups

`deluser --remove-home orangepi` to remove the obvious login with orangepi username
login with the new <username>
`sudo nano /etc/ssh/sshd_config`
change `PermitRootLogin yes` to `PermitRootLogin no` to remove root login attempts via ssh
`sudo systemctl restart sshd` so that the changes work.

If you have ethernet as the headless connection, remove it as apt update tries it first !

### Optional step to change the repo location, if the Tsinghua ones are not accessible or slow

`sudo nano /etc/apt/sources.list`
and change all instances of the address to (for example example) http://mirrors.ocf.berkeley.edu/ubuntu-ports/

### Set NTP 
`sudo apt install ntp` and check the time with `timedatectl`
`sudo apt-get update`



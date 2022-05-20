# CSGO Server AWS

Tutorial reviews steps by connect and create aws instance with csgo server

## Create EC2 instance AWS

For example is recommended to usage `c5.2xLarge` EC2 instance, Ubuntu 20.04 with `40Gb` EBS as link below.
Visit to link [here](https://marcusm.dk/2020/07/how-to-set-up-your-own-csgo-server-using-amazon-web-services-for-free/)

## Connect server linux

```sh
chmod 600 <pem-location>
ssh -i <pem-location> ubuntu@<public-ip-instance-aws>
```

## Install Steam Linux

Visit to link [here](https://developer.valvesoftware.com/wiki/SteamCMD#Downloading_SteamCMD)

```sh
sudo apt-get install lib32gcc1 -y
sudo useradd -m steam
sudo passwd steam
sudo -u steam -s
cd /home/steam
sudo -- sh -c 'dpkg --add-architecture i386; add-apt-repository multiverse; apt-get update; apt-get -y dist-upgrade'
sudo apt install steamcmd -y
```

## Install CSGO

Visit to link [here](https://marcusm.dk/2020/07/how-to-set-up-your-own-csgo-server-using-amazon-web-services-for-free/)

```sh
export SETSTEAMACCOUNT=<setsteamaccount>
mkdir ~/csgosv
cd csgosv/
steamcmd
force_install_dir /home/ubuntu/csgosv
login anonymous
app_update 740 validate
quit
/home/ubuntu/csgosv/srcds_run -game csgo -console -usercon -autoupdate -steam_dir "/home/ubuntu/.steam/steam/steamcmd" -steamcmd_script "/home/ubuntu/update.txt" +game_type 0 +game_mode 1 +mapgroup mg_active +map de_mirage +sv_setsteamaccount $SETSTEAMACCOUNT -tickrate 128 -net_port_try 1 -nobots
```

## Admins players

Visit to link [here](https://shockbyte.com/billing/knowledgebase/354/How-to-Setup-Player-Permissions-in-CSGO.html)
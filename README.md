# Install HomeAssistant in Rpi

```
sudo apt-get update &&
sudo apt-get upgrade -y &&
sudo apt-get install -y python3 python3-dev python3-venv python3-pip libffi-dev libssl-dev libjpeg-dev zlib1g-dev autoconf &&
sudo useradd -rm homeassistant -G dialout,gpio,i2c &&
sudo mkdir /srv/homeassistant &&
sudo chown homeassistant:homeassistant /srv/homeassistant &&
sudo -u homeassistant -H -s &&
cd /srv/homeassistant &&
python3 -m venv /srv/homeassistant &&
source /srv/homeassistant/bin/activate &&
python3 -m pip install wheel &&
pip3 install homeassistant &&
hass
```

or with Docker 
```
sudo apt-get install docker.io docker-compose
sudo reboot
mkdir ~/home-assistant
nano docker-compose.yml
```
in the docker-compose.yml file write the following:

```
version: '3'
services:
  homeassistant:
    container_name: home-assistant
    image: homeassistant/raspberrypi4-homeassistant:stable
    volumes:
      - /home/pi/homeassistant:/config
    environment:
      - TZ=Europe/Warsaw
    restart: always
    network_mode: host
 ```
 Finally: 
 ```
 sudo docker-compose up -d
 ```
 
# Install HomeAssistant in Your phone

Once HomeAssistant running in the rpi , you will be able to install the app from the playstore in your phone and 
add it as part of your automations. In my case the url will be 192.168.0.17:8123, the phone if in the same WIFI as the rpi, it will detect it automatically
If some problem , go to HomeAssistant app and delete all the cache and files and reinstall again

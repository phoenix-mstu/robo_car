# Примеры кода для робо-машинок FunCorp

Предварительно скачиываем Raspberry Pi OS Lite. Заливаем её на sd карту.
Прописываем настройки wifi: https://www.raspberrypi.org/documentation/configuration/wireless/headless.md
Включаем ssh: _For headless setup, SSH can be enabled by placing a file named ssh, without any extension, onto the boot partition of the SD card from another computer._

### Примеры кода для робо-машинок FunCorp

Дальше запускаем малинку, заходим по ssh. Заливаем туда этот код.

```
sudo apt-get update
sudo apt-get install python3-smbus i2c-tools python3-pip python3-venv git vim
sudo apt-get install libopenjp2-7 libtiff5 Python-opencv
sudo apt-get install libatlas-base-dev libilmbase-dev libopenexr-dev libgstreamer1.0-dev

sudo raspi-config -> ok -> interface options -> i2c -> yes -> ok -> escape
sudo raspi-config -> interface options -> camera -> yes
sudo i2cdetect -y 1 (должны увидеть табличку)
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 6f 
70: 70 -- -- -- -- -- -- --     

sudo reboot - иначе камера не заработает

mkdir ~/robo_car
python3.7 -m venv venv
source venv/bin/activate
python -m pip install requirements.txt

jupyter notebook --ip=0.0.0.0 --no-browser --port=8888
```

Заходим в jupyter. Оттуда запускаем код из примеров.
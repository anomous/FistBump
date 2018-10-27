# FistBump
ProtoType for a handheld device used to grab WPA four way handshakes

## Overview
This repository contains (UNDER CONSTRUCTION) all the Schematics, Reference Photos, Boot images, scripts, and even 3d printable encloser parts for creating what i am affectionitly calling "FistBump," a handheld device used to capture WPA/WPA2
4 way handshakes and storing them to removable storage so that the can be bruteforced later.

## Disclaimer
_This Device was developped as a proof of concept and for White Hat Purposes.  You should only use this device on your own or a consenting network and in a controlled enviroment as sending the necessary deauth packets used in the contained scripts could be illegal in your given part of the world. I do not endorse or warrent breaking the law or invading the privacy of others. What you do with this information is up to you. You alone are fully responsible for what you do with this info, and how you use it. I am not responsible for your actions. Please do not hack Wifi points that you are not allowed to!!!
Don't be a jerk!_

## Parts List

* [1 pi zero v1.3](https://www.raspberrypi.org/products/raspberry-pi-zero/)
_Do **NOT** use the wifi model as the chip doesn't support monitor/package injection and creates interferience on usb hub_

* [1 zero4u usb hub adapter](https://www.adafruit.com/product/3298?gclid=Cj0KCQjw6rXeBRD3ARIsAD9ni9CGzOos99HaKls0MxgqrZMt_sKTnR6LVGsSJiN6rdDrbmr9ndM0L3QaAk_SEALw_wcB)

* [1 MakerSpot RPi Raspberry Pi Zero W Protoboard Breadboard](https://www.amazon.com/MakerSpot-Raspberry-Protoboard-Breadboard-Prototyping/dp/B01J9ILH7S)

* [2 10k resistors](https://www.amazon.com/Projects-25EP51410K0-10K-Resistors-Pack/dp/B01F06T56I/ref=sr_1_1_sspa?ie=UTF8&qid=1540222052&sr=8-1-spons&keywords=10k+resistor&psc=1)

* [1 100k resistor](https://www.amazon.com/Projects-25EP514100K-100k-Resistors-Pack/dp/B0185FCGEY/ref=sr_1_1_sspa?ie=UTF8&qid=1540222085&sr=8-1-spons&keywords=100k+resistor&psc=1)

* [3 1N4007 diodes]( https://www.amazon.com/100-Pieces-1N4007-Rectifier-Electronic/dp/B079KBFKK5/ref=sr_1_1_sspa?ie=UTF8&qid=1540222123&sr=8-1-spons&keywords=1n4007+diode&psc=1)

* 1 [small momentary button for power button](https://www.amazon.com/GZFY-6x6x4-5mm-Momentary-Tactile-Button/dp/B01N6GU7TA/ref=sr_1_14?ie=UTF8&qid=1540222185&sr=8-14&keywords=small+momentary+button)

* 1 [regular momentary button for Attack Trigger](https://www.amazon.com/Cylewet-12x12x7-3mm-Momentary-Tactile-Arduino/dp/B01NCQVGLC/ref=sr_1_9?ie=UTF8&qid=1540222185&sr=8-9&keywords=small+momentary+button)

* 1 [2.5 pi nylon screw set](https://www.adafruit.com/product/3299)

* 1 usb wifi adapter capable of monitor mode/ packet injection. I'd recommend the [Panda 300Mbps Wireless N USB Adapter](https://www.amazon.com/gp/product/B00EQT0YK2/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1) or even the [canaKit Wifi adapter](https://www.amazon.com/gp/product/B00GFAN498/ref=oh_aui_detailpage_o00_s01?ie=UTF8&psc=1) _both are capable of packet injection and fairly small YAY!_ or you could also use [this guy if you want and even smaller profile but its not as strong]( https://www.amazon.com/gp/product/B019XUDHFC/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1) 
For a more complete list of recommended devices [click here](https://null-byte.wonderhowto.com/how-to/buy-best-wireless-network-adapter-for-wi-fi-hacking-2018-0178550/)

* 1 [lo profile sandisk flash storage for saving handshakes in a removable manner](https://www.amazon.com/SanDisk-Cruzer-Low-Profile-Drive-SDCZ33-008G-B35/dp/B005FYNSUA/ref=sr_1_7?s=electronics&ie=UTF8&qid=1540222662&sr=1-7&keywords=sandisk+flash+drive+8gb)

* 1 [16-32gb class 10 mirco sd card for pi boot image](https://www.amazon.com/s/ref=nb_sb_ss_i_5_10?url=search-alias%3Delectronics&field-keywords=16gb+micro+sd+card+class+10&sprefix=16gb+micro%2Celectronics%2C132&crid=5DO4BAWIZ2SP)

* 1 [Pwerboost 1000c or 500c](https://www.adafruit.com/product/2465)

* 1 [3.7V 1200mAh PKCELL LP503562](https://www.amazon.com/s?k=3.7V+1200mAh+PKCELL+LP503562&ref=nb_sb_noss) _size matters we want a low profile as we will have a tight fit but feel free to alter this as you see fit espcially if you deisgn your own enclosuer etc_

* 1 [Pimoroni Blinkt!](https://shop.pimoroni.com/products/blinkt) _this will be your status indicator_

# Physical Assembly
For instructions on the physical assmebly follow the README file, [here](https://github.com/eliddell1/FistBump/tree/master/schematics%26referenceImages) I have also supplied freecad/stl files for the encloser [here](https://github.com/eliddell1/FistBump/tree/master/EncloserFreeCad)

# Software Dependencies
This repository will supply an image built of [Raspbian STRETCH OS](https://www.raspberrypi.org/downloads/raspbian/) that you could just write to a micro sd, pop into your piZero and be good to go! That said, should you choose to build this yourself off of another OS or with modifications, be aware of the following dependencies.  The scripts for powering on and off the device as well as the trigger and attack button have been suplied in the [scripts folder](https://github.com/eliddell1/FistBump/tree/master/scripts)

* aircrack-ng
`sudo apt install aircrack-ng`

* cowpatty 
`wget http://www.willhackforsushi.com/code/cowpatty/4.6/cowpatty-4.6.tgz
tar zxfv cowpatty-4.6.tgz
cd cowpatty-4.6
make cowpatty
sudo cp cowpatty /usr/bin`

* blinkt! python library
`curl https://get.pimoroni.com/blinkt | bash`

# Credit
Credit where credit is due, the powering on/off schematic and script were deigned by [NeonHorizon](https://github.com/NeonHorizon/lipopi/blob/master/README.power_up_power_down.md)  

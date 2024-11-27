This series of posts is an experience report on creating a sunrise alarm using Home assistant and a smart light bulb. In this  post, I will go over the choice of hardware and setting up Home Assistant on the Raspberry Pi 4.

# Hardware
I used the following hardware:
* Raspberry Pi 4: the oldest version recommended is RPi 3. Home assistant also sell plug and play devices on their website. 
* Ethernet cable: needed for the installation, and it is recommended to keep using it as it is more reliable than Wifi. 
* Micro SD card + SD card adaptator for flashing it
* Ikea Tradfri smart lightbulb: or any smart lamp that works with the Zigbee wireless communication protocol. 
* Ikea Remote control (optional): also works over Zigbee.
* SONOFF Zigbee dongle: used to communicate between the RPi and the smart bulbs.

At first I thought that smart devices all communicated over Wifi - it turns out that most smart devices use [Zigbee](https://en.wikipedia.org/wiki/Zigbee), a specification for communication protocols that used to create smaller and lower-power networks than Bluetooth or Wifi.
# Installing home assistant
I chose to flash Home assistant OS directly on my SD Card as it seemed like the easiest solution, but you can chose to [run it in a docker container](https://stevessmarthomeguide.com/running-home-assistant-in-a-docker-container/) if you already have programs running on your RPi. For this section, I'll simply refer to the [Home assistant RPi installation guide](https://www.home-assistant.io/installation/raspberrypi) for more details, but basically, you need to:
* Flash the Home assistant OS image on the SD card
* Connect the RPi to your router via Ethernet cable
* Wait for the installation to complete

The only thing I'll add is that you *do need* an Ethernet connection for the installation, or the installation will not work. I was used to setting up Wifi credentials and SSH access to my RPi in RPi imager, but this does not work for Home assistant OS. It [isn't based on a regular Linux distribution](https://www.home-assistant.io/installation/raspberrypi),  even connecting a monitor and a keyboard to the RPi doesn't give you access to the file system out of the box.

If the installation was successful, you should be able to access your Home assistant through any device connected to the same Wifi network by entering [homeassistant.local:8123](http://homeassistant.local:8123) in your browser. It will detect any available device within reach (be sure to ignore your neighbour's bluetooth speaker or you might start playing music on it by accident).

Once you're set up, you'll be able to connect the Zigbee dongle and start connecting to your smart lightbulbs. But more on that in the next post. 

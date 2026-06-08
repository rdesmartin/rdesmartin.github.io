---
tags:
  - it
  - misc
---
This series of posts is an experience report on creating a sunrise alarm using Home assistant and a smart light bulb. After going through the steps to [[How to make a sunrise alarm with Home assistant + and a smart light bulb (pt. 2) | install Home Assistant and access its user interface through your Web browser]], in this  post I will explain how to connect HA to an Ikea Tradfri lightbulb, or any smart lightbulb that uses the Zigbee communication protocol. 

NB: I will give short explanations of HA-specific notions (like integrations, automations, entities etc.) but I highly recommend reading the full documentation of Home Assistant as it is clear and short.
# Zigbee connection

In order to setup the HA instance to communicate with Zigbee devices, you'll need 2 things:
* a Zigbee dongle, i.e. a physical emitor/receptor that communicates with devices through radio signal (I used the [Sonoff dongle](https://sonoff.tech/product/gateway-and-sensors/sonoff-zigbee-3-0-usb-dongle-plus-p/) but any will do);
* install the ZHA integration from the HA user interface.
## Zigbee dongle
The Sonoff zigbee dongle is plug-and-play, it comes with HA-compatible firmware so it should work by plugging it to your Raspi's USB port out of the box.

## ZHA integration
Home assistant communicates with external devices, and services through *integrations*. Some are installed by default (e.g. Bluetooth, weather), but some other, like Zigbee, need to be installed manually. To do that, you need to navigate to `Settings > Devices & Services > Integrations` then click on `Add integrations` and select Zigbee Home Automation from the list.

Note that another integration exists to communicate with Zigbee devices called zmqtt. From what I gather, it allows more customisation than ZHA but it can also be less stable, and it might require flashing the dongle with a different firmware.

After having plugged the dongle and installed the ZHA integration, you need to restart the HA instance.

# Connecting the light bulb and remote
To connect the Ikea Tradfri light bulb, you need to put it in pairing mode first. To do that, first plug the light bulb to any lamp, then starting on an **on** position, switch it on and off 6 times. The light bulb should start to flicker lightly (it is very faint but should be noticeable).

You should then see your light bulb show up in the Zigbee devices in the HA interface. Once the light bulb is connected, you can turn it on and off from the HA interface to check if everything went OK.

 For the remote, you need to first remove the cover on the back with a screwdriver and press 4 times on the pairing button for a factory reset. then hold the pairing button down for 6 seconds to enter pairing mode (the red light should flicker). You can add it from the HA interface similarly to the bulb. It will not work yet, you need to install an *automation* to set it up.

# Installing the remote control automation
Automations are HA programs running constantly in the background; they allow to create rules that trigger an action when an event happens or some conditions are met, like "send a notification on my phone if a window is left open after 10pm" or "Increase the light bulb's brightness when the 'up' button of the remote control is pressed". They can be created by editing TOML files, or through the user interface.

For handling the remote control's inputs, we will use a *blueprint*, a template that allows to re-use and personnalise an automation created by someone else. To import it into HA, simply go to [this page](https://community.home-assistant.io/t/zha-ikea-four-button-remote-styrbar-for-lights-and-switches/395248) and click on the blue `Import blueprint` button. Once the blueprint is imported, you can navigate to `Settings > Automations & Scenes > Automations` and click on `Create Automation`. In the pop-up window, select the Blueprint `ZHA - IKEA four button remote for lights`. You can then configure the blueprint to use the right light bulb and remote devices, and select what the left and right buttons do.

You can test your remote, now clicking on the up and down buttons should control the light bulb's brightness - hurray! In the next post, we'll finally get to implementing the sunrise alarm.
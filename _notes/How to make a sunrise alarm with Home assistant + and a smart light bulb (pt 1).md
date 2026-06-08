---
tags:
  - it
  - misc
---
This series of posts is an experience report on creating a sunrise alarm using Home assistant and a smart light bulb. In this  short first post, I will explain the goal of the project and give the reasons why I chose Home assistant. 
# Introduction
A sunrise alarm is a bedside lamp cum alarm clock which gradually increases its light for 30 minutes before the set alarm time, which makes waking up easier especially during the dark winter months. My motivation was simple: I had a dedicated [sunrise alarm](https://www.lumie.com/products/sunrise-alarm), but its UX was plain bad, with a bunch of inconveniently placed buttons, and I found it not as good-looking as my previous basic bedside lamp. 

So I decided to replace the sunrise alarm by my inconspicuous bedside lamp fitted with a smart light bulb, and my old raspberry pi set up as a smart home server. Using a smart home platform also has the benefit of allowing to use one's native phone alarm, without having to set a separate alarm. 

Overall it was quite a smooth process, even though I had no experience in home automation at all. The initial research and solving random issues were the two most time-consuming steps so I hope that sharing my experience and focusing on these aspects will be of some help to other home automation novices. 
# Choosing a smart home platform
The first step in creating the smart sunrise alarm is to chose a home automation. The two main reasons for chosing Home Assistant (HA) are privacy, and balance between programmability and user-friendliness.

The most user-friendly home automation solutions are proprietary ones like Apple Home, or Ikea's Dirigera system. The problem with these is that they are usually expensive, not great privacy-wise as all your data is stored on the provider's cloud storage, and they are very limiting in what you can program or what device you can interface with.

When looking for local, open-source, customisable tools, the solutions that pop up first are [OpenHAB](https://www.openhab.org/), [Gladys](https://gladysassistant.com/) and [Home Assistant](https://www.home-assistant.io/).
- OpenHAB is based on Java and it has a high level of customisability. As someone who knows how to program, the possibility to write automation in a standard programming language was appealing. However its doc fully discloses that it is part of the tool's philosophy to make the user work hard: "openHAB is fully customizable, but doing so will require substantial effort on your part". Maybe I was too easily intimidated but that seemed a bit too demanding (and gatekeepy) for my taste.
- Gladys is a (mostly) one-man project that aims to make home automation accessible to less tech-savvy people. The UI and plug-and-play setup seemed nice but the tool is quite new so I was worried about long-term support, and it seemed not customisable enough for what I was looking for. 
- Home Assistant hits the sweet spot between programmability and user-friendliness. It is mature and has an active community, which is always reassuring when considering adopting an open-source tool. The biggest downside is that scripts are written in YAML; this is clunky to say the least, but better that than nothing (or having to manually manage an events database), and we'll see in later posts that it is possible to use alternative automation tools.

That's it for this first post, in the next one I will get into the meat of the project and talk about what hardware to use, and how to set up a Home assistant instance on a Raspberry Pi. 


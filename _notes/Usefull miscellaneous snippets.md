---
toc: true
tags: tools snippets
season: spring
---
# Use Wildcard With apt

Use the asterisk wildcard syntax when installing packages with Ubuntu's package manager.

`apt install '?name(libkf5.*)'`

[source](https://manpages.debian.org/bullseye/apt/apt-patterns.7.en.html)

# I3-wm: assign a workspace to a monitor


When working in a multi-monitor setup and apps are assigned to specific workspaces,
it is useful to assign workspaces to a specific monitor; for instance, in order to have
wide-screen apps like VLC always be displayed on the wider monitor.

List your monitors's handles using
```
$ xrandr --listmonitors | awk '{print $4}'
> HDMI-A-0
> eDP
```

Then define variables and assign workspaces to monitors in the i3 config file
```
set $monitor_builtin "eDP"
set $monitor_external "HDMI-A-0"
workspace $ws8 output $monitor_external
```

Note: if workspace have names containing spaces (such as those generated by [regolith](https://regolith-linux.org/))
numbers should be used:

```
workspace 8 output $monitor_external
```


[source](https://www.reddit.com/r/i3wm/comments/lv3xd0/assigning_workspaces_to_specific_monitors/)
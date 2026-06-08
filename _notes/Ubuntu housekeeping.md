---
tags:
  - programming
  - tools
---
# Free up memory
* Clean snap's cached versions (Ubuntu's application installer and manager): https://itsfoss.com/clean-snap-packages/
* Clean apt cache: `sudo apt-get clean` (size of cache can be seen with `du -sh /var/cache/apt/archives`)
* Clean old linux kernels: `sudo apt remove $(dpkg-query --show 'linux-modules-*' | cut -f1 | grep -v "$(uname -r)")` ([source](https://serverfault.com/questions/1098556/how-to-cleanup-usr-lib-modules-and-usr-lib-x86-64-linux-gnu) with nice detailed explanation). Don't forget to run `sudo apt autoremove` after. 
* Clean apt cache: `sudo du -sh /var/cache/apt` to see how much space it's taking, `sudo apt clean` to remove all cache, `sudo apt autoclean` to remove only obsolete cached items
* `du -sh` to see the size of a directory/file

# Create .desktop file
In the `~/.local/share/applications`, create the `<application name>.desktop` file:

```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Terminal=false
Exec=/path/to/executable
Name=Name of Application
Icon=~/.local/share/icons/path/to/icon
```
---
layout: post
title: "Using iPad as a 2nd monitor on Linux"
categories: linux
author: "Bumsik Kim"
tags: linux bash x11
# permalink: /:categories/:year/:month/:day/:title:output_ext
---

![dual_screen]({{ "/assets/dual_screen.jpg" }})

A year ago, I switched to Linux from Windows, and I am happy with it. I had always used a VM to run Linux before, but I am finally getting to know how things work in Linux after natively installing it. There are many Linux alternatives for Windows programs, so I normally have no problem using Linux programs.

The only thing I missed about Windows is iPad dual monitor apps like [Duet Display][Duet]. No Linux programs work automagically like Duet. A little bit of searching the web led me to some solutions like [Aditya's post][ref-aditya] and [a thread in Arch Linux forum][ref-arch], so I was able to make my iPad a second display. However, the solutions in the post required to input some command manually every time I enable dual screen and don’t work nicely as-is.

As I tired typing commands by hand and memorizing them, I decided to write my own script `ipad_monitor.sh`. This script is still far from “automagically” but it works mostly out of the box. All you need to do is changing `WIDTH` and `HEIGHT` at the beginning of the code. Since it uses VNC to connect to an iPad, it also works with any tablet and computer with a VNC client. Here it goes:

[Duet]: https://www.duetdisplay.com/
[ref-aditya]: http://www.adityavaidya.com/2015/03/ipad-as-2nd-monitor-now-on-linux.html
[ref-arch]: https://bbs.archlinux.org/viewtopic.php?id=191555

<script src="https://gist.github.com/kbumsik/e9717525fec7b6e98524765958044146.js"></script>

So, what the script does is 1. to parse arguments to set a proper resolution, 2. add a display mode using `XRandR`, 3. Output it next to a primary display, 4. and run `x11vnc` to transmit the screen through VNC.

## How to use

1. Install [`x11vnc`](https://github.com/LibVNC/x11vnc) first: `sudo apt-get install x11vnc`.
2. Change `WIDTH` and `HEIGHT` in the script to change the resolution.
3. Figure out your local IP address using `ip addr` or `ifconfig`
4. Run this script. Addtional arguments are self-explanatory. Example arguments:
```bash
./ipad_monitor.sh -r    # or --right. Second screen appears right to the primary monitor.
./ipad_monitor.sh -l    # or --left
./ipad_monitor.sh -a    # or --above
./ipad_monitor.sh -b    # or --below
./ipad_monitor.sh -r -h    # or --hidpi. HiDPI mode. It doubles the resolution.
./ipad_monitor.sh -r -p    # or --portrait. Portrait mode.
./ipad_monitor.sh -l -p -h    # Left, portrait mode, and HiDPI mode.
```
5. Connect your iPad using your favorite VNC app. IP address is : `your.ip.addr.ess:5900`

## Performace

I use an i5-4210M laptop as a VNC server and iPad Pro 2nd Gen as a client. Testing is done on a local area network, meaning that the VNC server and client are connected to the same home router using WiFi, and with VNC screen both at 1368x1024 and 2736x2048 with full colors.

Just like I do daily with a second screen, I tried using a web browser on the VNC screen. Although it did not work as smoothly as paid dual screen apps or Windows RDP, it worked pretty fine. It showed the browser window almost instantly and the screen update rate was not bad when I fast scrolled up and down the browser. The screen shutterEverything worked without a big issue.

Note that the performance depends on routers. I also tried it on a public WiFi and it was almost useless. If this is the case, I would suggest using the offline solutions mentioned in QnA below. Actually the offline solutions usually perform better than connecting via a home router.

Regarding resource usage, `x11vnc` uses very few RAM but constantly uses 2% to 5% while showing a still image. Its CPU usage occasionally spikes up to 40% while scrolling the browser, so it obviously drains laptop battery.

That’s it. I hope someone finds it useful.

## QnA

### How I can use it offline?

You may want to connect them directly using WiFi hotspot. There are two ways:

1. Create a WiFi hotspot on your laptop. You can do this simply using [`create_ap`][create-ap] package, e.g. `sudo create_ap wlp0s0 wlp0s0 _Your_SSID_ _Your_Password_`. Note that not all hardware support this feature.
2. Enable “Personal Hotspot” on your tablet and connect your laptop. WARNING: It will drain your mobile data, although I personally checked my iPad that it doesn’t use mobile data for VNC connection.

In either way, use a proper local network IP managed by the laptop/iPad.

[create-ap]: https://github.com/oblique/create_ap

### Wayland?

This script heavily relies on an x11 utility, `XRandR`. Unfortunately, Wayland [dropped support for XRandR screen control.][xrandr_dropped] And there doesn't seem to be an `XRandR` command alternative for Wayland. It looks like [Wayland doesn't want user apps to change monitor resolution][wayland_monitor] (but...why?). So I don't know how to do the same thing using simple bash scripts for now.

[xrandr_dropped]: https://fedoraproject.org/wiki/Wayland_features#XRandR_control_of_Wayland_outputs
[wayland_monitor]: https://fedoraproject.org/wiki/How_to_debug_Wayland_problems#Games_and_other_apps_can.27t_change_monitor_resolution

### How to set a VNC password?

You can set a password by editing the last `x11vnc` command in the script file. See [this Wiki article][x11vnc-password] to set up a password.

[x11vnc-password]: https://wiki.archlinux.org/index.php/x11vnc#Setting_a_password

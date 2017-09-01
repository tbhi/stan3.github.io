---
layout: post
---
This often comes in handy to enable and start vino via ssh (on Ubuntu 16.04)

    export DISPLAY=:0.0
    gsettings set org.gnome.Vino network-interface lo
    gsettings set org.gnome.Vino prompt-enabled false
    gsettings set org.gnome.Vino enabled true
    /usr/lib/vino/vino-server &

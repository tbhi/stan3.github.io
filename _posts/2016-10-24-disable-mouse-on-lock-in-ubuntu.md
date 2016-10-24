---
layout: post
---
I like to have my monitors off to save power when the screen is locked.
Unfortunately it seems like my mouse is rather sensitive so nearby movements
cause the screens to come back on.  I preferred to have only a keyboard press
do this.

    #!/bin/sh
    XINPUT_ID=8
    gdbus monitor -e -d com.canonical.Unity -o /com/canonical/Unity/Session |
      while read x; do
        case "$x" in
          *.Locked*) xinput --disable $XINPUT_ID;;
          *.Unlocked*) xinput --enable $XINPUT_ID;;  
        esac
      done

This script achives that.  I have it listed in the startup applications so
starts on logon.  Use `xinput list` to find the correct xinput ID.

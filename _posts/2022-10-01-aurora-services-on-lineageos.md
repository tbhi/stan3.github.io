---
layout: post
title: Aurora Services on LineageOS
---

Unsure about installation instructions on <https://gitlab.com/AuroraOSS/AuroraServices> some searching found <https://gitlab.com/AuroraOSS/AuroraServices/-/issues/5> so thought I'd try sideloading from LineageOS recovery. 

Not working, then found <https://gitlab.com/AuroraOSS/AuroraServices/-/issues/51>.  Last comment mentions Fdroid so downloaded <https://f-droid.org/en/packages/org.fdroid.fdroid.privileged.ota/> and noticed the `update-binary` script was doing `mount "/dev/block/bootdevice/by-name/system" "$MOUNT_POINT"`.  So tried `mount /dev/block/bootdevice/by-name/system_a /mnt/system` from `adb shell` which worked.

So falling back to the old instructions copied the apk to `/mnt/system/system/priv-app` and permissions to `/mnt/system/system/etc/permissions/` (these were in `/tmp` from the sideload).  Umount and reboot, select Aurora Services in Aurora settings then worked and updated apps without prompting.

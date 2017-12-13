---
layout: post
---
I've recently been trying to setup [hardware encryption in Windows](https://docs.microsoft.com/en-us/windows/device-security/encrypted-hard-drive)
on a Samsung 960 Evo.  Samsung Magician suggests to a secure erase as part of this
process.  However, I've been getting problems with a

> The selected Samsung drive is locked. Secure Erase is not supported on this drive.  

error.  Emailing Samsung support said:

> Please initialize the locked SSD using diskpart.
>
> 1. Go to diskpart
> 2. Go to the list of disks
> 3. select the disk "number of the locked SSD"
> 4. Clean
>

Which looks like a it would just wipe the partition table to me and not securely erase the data on the drive.  Probing further:

> Than you for your inquiry.
> Either way, the partition as well as any other data on the drive will be deleted.
> Initializing a drive deletes data that is on it.
>
> When initializing or secure erase is not possible, you will need to return the drive to our service center.

Not sure about that.  Perhaps Samsung Magician has problems with m.2 drives?
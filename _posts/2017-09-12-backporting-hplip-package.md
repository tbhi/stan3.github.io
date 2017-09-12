---
layout: post
---

As I'm running Ubuntu LTS when I got a new HP OfficeJet I needed to backport
the hplip package to get a newer version.  Quick cheat sheet:

    backportpackage -d xenial -s zesty -w hplip_backport hplip

from the ubuntu-dev-tools package, then

    dpkg-source -x hplip_3.16.11+repack0-2~ubuntu16.04.1.dsc

in this case I wanted to modify the debian/rules file to change an argument to
one of the debhelpers that had changed, so I did this change manually, then

    dpkg-buildpackage -rfakeroot -d -us -uc -S -nc -sa -v3.16.3+repack0-1
    cd ..
    debsign hplip_3.16.11+repack0-2~ubuntu16.04.1_source.changes
    dput ppa:stan/hplip hplip_3.16.11+repack0-2~ubuntu16.04.1_source.changes

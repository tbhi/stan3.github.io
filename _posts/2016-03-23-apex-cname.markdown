---
layout: post
title:  "CNAMEs for apex domains"
date:   2016-03-23 12:42:45 +0000
---
As outlined at [heroku](https://devcenter.heroku.com/articles/apex-domains)
example.com style domains can be a pain to host as they must use A records.
Numerous DNS providers provide a work around with the ALIAS/ANAME pseudo record
type.  The good news for open source users is this is now also supported by
[PowerDNS](https://en.wikipedia.org/wiki/PowerDNS) as an
[ALIAS](https://doc.powerdns.com/md/types/) record type.

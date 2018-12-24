---
title: "A IPv6/IPv4 mixed world"
date: 2018-12-23T19:06:48-05:00
draft: false
---

A couple weekends ago one of my sons had a bunch of his friends over and before
I knew it, I was told they were having trouble with the Internet. I checked
Google, FaceBook and YouTube and didn't have any problems connecting. Fast.com
showed that bandwidth was at expected levels.

An hour later, I was having trouble connecting to some web sites being returned
from Google searches. Then I realized that only websites that had IPv6 addresses
where reachable.

Further investigation found that my home network was no longer serving IPv4 addresses
and the hosts were assigning themselves IPv4 addresses from the 169.254 subnet. I had
to reset the router back to factory defaults to fix the problem.

While it seems totally normal that IPv6 and IPv4 only hosts are not able to
connect to each other, there has been lots of work to actually make it so they
can. I was overly optimistic that the networks were at this state.

I'll be doing some research to see if individuals at home could solve this themselves.

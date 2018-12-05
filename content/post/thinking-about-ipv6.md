---
title: "Thinking About Ipv6"
date: 2018-11-29T20:46:04-05:00
draft: false
---
Ipv6 is the successor to IPv4. It essentially allows everyone to have a lot of
IP addresses. I'm a Comcast subscriber. Comcast gives subscribers a /64. That means
there are 2^64 (18,446,744,073,709,551,616) addresses available to assign hosts to.

Because there are so many available IPs in IPv6, most modern Operating Systems assign
multiple IPv6 addresses to a single computer. Currently my computer has several
different types of IPv6 addresses assigned to it. I'd simply categorize them into
two groups. Public addresses and private addresses.

The private addresses are like the non-routable IPv4 addresses. They are meant for local networks.
The public addresses are accessible from other locations on the Internet, without
having to resort to NAT trickery. Unless your router has an IPv6 firewall in place,
anyone on the Internet can directly connect to that IP. I'll be exploring this
direct connectivity.

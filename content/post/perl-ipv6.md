---
title: "Perl and IPv6"
date: 2018-12-06T20:54:08-05:00
draft: false
---
Since Perl 5.20, IPV6 support was improved to support a family neutral socket.
This allows programs to be written for IPv4 and IPv6 in a fairly seamless way.

```perl
#!/usr/bin/env perl

use v5.20.0;
use IO::Socket::IP;

# taken directly from man page
my $sock = IO::Socket::IP->new(
   PeerHost => "www.google.com",
   PeerPort => "http",
   Type     => SOCK_STREAM,
) or die "Cannot construct socket - $@";

my $familyname = ( $sock->sockdomain == PF_INET6 ) ? "IPv6" :
                 ( $sock->sockdomain == PF_INET  ) ? "IPv4" :
                                                     "unknown";

printf "Connected to google via %s\n", $familyname;
printf "Local address is: %s\n", $sock->sockhost;
printf "Remote address: %s\n", $sock->peerhost;
```

I get the following output:
```shell
Jeffs-MacBook-Pro:perl-ipv6 jeff$ ./connect
Connected to google via IPv6
Local address: 2601:18f:601:6b55:14ae:26e9:d343:12f0
Remote address: 2607:f8b0:4006:81b::2004
```

`ifconfig` can help us verify that a temporary IPv6 address was used.

```shell
Jeffs-MacBook-Pro:perl-ipv6 jeff$ ifconfig en0
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	ether 8c:85:90:0e:e3:05
	inet6 fe80::800:c5e9:8c17:9c36%en0 prefixlen 64 secured scopeid 0x8
	inet6 2601:18f:601:6b55:373:3eb7:8af3:f146 prefixlen 64 autoconf secured
	inet6 2601:18f:601:6b55:14ae:26e9:d343:12f0 prefixlen 64 autoconf temporary
	inet 192.168.1.126 netmask 0xffffff00 broadcast 192.168.1.255
	nd6 options=201<PERFORMNUD,DAD>
	media: autoselect
	status: active
```

`host` can be used to see what IPs DNS provided. Applications should use IPv6
when available.

```shell
Jeffs-MacBook-Pro:perl-ipv6 jeff$ host www.google.com
www.google.com has address 172.217.12.196
www.google.com has IPv6 address 2607:f8b0:4006:81b::2004
```

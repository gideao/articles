---
title: How to filter ads
date: 2018-03-09 16:07:35 -03:00
layout: post
---

```
deb http://deb.torproject.org/torproject.org wheezy main
```

```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
```

```
apt-get install deb.torproject.org-keyring
```

```
aptitude install tor privoxy
```

# open /etc/privoxy/config and add lines below

```
user-manual /usr/share/doc/privoxy/user-manual
confdir /etc/privoxy
logdir /var/log/privoxy
actionsfile match-all.action # Actions that are applied to all sites and maybe overruled later on.
actionsfile default.action   # Main actions file
actionsfile user.action      # User customizations
filterfile default.filter
filterfile user.filter      # User customizations
logfile logfile
listen-address  localhost:8118
toggle  1
enable-remote-toggle  0
enable-remote-http-toggle  0
enable-edit-actions 0
enforce-blocks 0
buffer-limit 4096
forward-socks5   /               127.0.0.1:9150 .
forward         192.168.*.*/     .  
forward         10.*.*.*/        .  
forward         127.*.*.*/       .
forwarded-connect-retries  0
accept-intercepted-requests 0
allow-cgi-request-crunching 0
split-large-forms 0
keep-alive-timeout 5
socket-timeout 300
```

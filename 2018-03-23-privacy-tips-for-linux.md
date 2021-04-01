---
title: Privacy tips for Linux
date: 2018-03-23 20:58:51 -03:00
layout: post
---


```
apt-get update
apt-get install build-essential automake unbound
```

## install libsodium

```
wget https://download.libsodium.org/libsodium/releases/libsodium-1.0.8.tar.gz
tar -vzxf libsodium-1.0.8.tar.gz
cd libsodium-1.0.8/
```

```
./configure && make
make install
```

## install libevent

```
wget https://github.com/libevent/libevent/releases/download/release-2.0.22-stable/libevent-2.0.22-stable.tar.gz
tar -vzxf libevent-2.0.22-stable.tar.gz
cd libevent-2.0.22-stable/
```

```
./configure && make
sudo make install
```

## install dnscrypt-wrapper

```
wget https://github.com/Cofyc/dnscrypt-wrapper/releases/download/v0.2/dnscrypt-wrapper-v0.2.tar.bz2
tar -vjxf dnscrypt-wrapper-v0.2.tar.bz2
cd dnscrypt-wrapper-v0.2/
```

```
ldconfig
make configure
./configure
make install
```

## install dnscrypt-proxy

```
wget https://github.com/jedisct1/dnscrypt-proxy/releases/download/1.6.0/dnscrypt-proxy-1.6.0.tar.bz2
tar -vjxf dnscrypt-proxy-1.6.0.tar.bz2
cd nscrypt-proxy-1.6.0/

ldconfig
./configure && make
sudo make install

sudo mkdir /etc/dnscrypt-proxy
cp 
```

## configure dnscrypt-wrapper

```
mkdir /etc/dnscrypt

mkdir /etc/dnscrypt-proxy
```

## Config dnscrypt-proxy

## Update DNS list
```
wget https://raw.githubusercontent.com/jedisct1/dnscrypt-proxy/master/dnscrypt-resolvers.csv
mv dnscrypt-resolvers.csv /usr/local/share/dnscrypt-proxy/
```

## Select and get the name of name server
```
cat /usr/local/share/dnscrypt-proxy/dnscrypt-resolvers.csv | cut -d ',' -f1,2,3 -s | column -s, -t
```
## Start dnscrypt-proxy

```
dnscrypt-proxy --local-address=127.0.0.1:5353 --resolver-name=cs-pt  --daemonize
```
## Test dnscrypt-proxy

```
dig -p 5353 google.com @127.0.0.1
```

## Config Unbound

## Create a config file for unbound
nano /etc/unbound/unbound.conf.d/cache.conf

## Apply change

```shell
systemctl restart unbound.service 
```

## Instalando cliente

```shell
brew install dnscrypt-proxy --with-plugins
```

## Veja a lista de provedores

```
cat /usr/local/opt/dnscrypt-proxy/share/dnscrypt-proxy/dnscrypt-resolvers.csv

sudo cp -fv /usr/local/opt/dnscrypt-proxy/\*.plist /Library/LaunchDaemons

sudo chown root /Library/LaunchDaemons/homebrew.mxcl.dnscrypt-proxy.plist
```

## Edite seu provedor

```
sudo emacs /Library/LaunchDaemons/homebrew.mxcl.dnscrypt-proxy.plist
```

## Restart

```shell
sudo launchctl unload /Library/LaunchDaemons/homebrew.mxcl.dnscrypt-proxy.plist && \
sudo launchctl load /Library/LaunchDaemons/homebrew.mxcl.dnscrypt-proxy.plist
```

After starting dnscrypt-proxy, you will need to point your local DNS server to 127.0.0.1. You can do this by going to System Preferences > "Network" and clicking the "Advanced..." button for your interface. You will see a "DNS" tab where you can click "+" and enter 127.0.0.1 in the "DNS Servers" section.

## test

```shell
nslookup -type=txt debug.opendns.com
```

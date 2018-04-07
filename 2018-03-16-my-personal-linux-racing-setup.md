---
title: My personal Linux Racing setup
date: 2018-03-16 19:36:57 -03:00
layout: post
---
# My personal Linux Racing setup
## Display manager

## Windows manager
```
apt-get install openbox
```

```
apt-get install obmenu
```

```
cp /etc/xdg/openbox/menu.xml ~/.config/openbox/
```

## Taskbar
```
apt-get install tint2
```

Add at ~/.config/openbox/autostart

```
(sleep 2s && tint2) &
```

## Wallpaper 
```
apt-get install nitrogen
```

## Terminal emulator 
```
apt-get install rxvt-unicode
```

## Fonts
```
mkdir ~/.fonts 
cp ? ~/.fonts 
tfc-cache -fv
```

Rofi


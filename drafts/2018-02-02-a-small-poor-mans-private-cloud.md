---
title: A small poor man’s private cloud
date: 2018-02-02 16:33:33 -03:00
layout: post
---

## Introduction

Heroku is a great platform for hosting Rails application and its push based deploy system is one of most coolest things I ever have found. However use Heroku has its down side too. Everything you want add to your app is offer to you as a add-on, cutting your freedom to do fine tuning and get a better price on computer resources.

Dokku is simple and open source solution that give the same Heroku`s deploy experience for free. It was also write in shell script giving a small footprint. 

Dokku also use Docker behind scene to do environment isolation and manager different hosted applications.

## Installation

Download the installation script that will do the whole process for us. Then set the desired version and run the script. 

```sh
wget https://raw.github.com/progrium/dokku/v0.3.22/bootstrap.sh
sudo DOKKU\_TAG=v0.3.22 bash bootstrap.sh
```


## Database

For use Postgresql will be necessary download a complement and place in the plugins`s folder.

```sh
cd /var/lib/dokku/plugins
git clone https://github.com/Kloadut/dokku-pg-plugin postgresql
dokku plugins-install
```

Install Postgresql`s client to access and configure the database.

```sh
apt-get update
apt-get install postgresql-client
```


## Deploy your app

```sh
git remote add dokku dokku@gideao.co:myproblem
git push dokku master
```

## After deploy your App

```sh
dokku postgresql:create myproblem
```

```sh
dokku postgresql:link myproblem myproblem //for manualy link
dokku run myproblem rake db:migrate
```


## Add a domain to application

```sh
dokku domains:add myproblem seuproblema.com
```
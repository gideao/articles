---
title: How to configure a small email server
date: 2018-02-16 22:27:03 -03:00
layout: post
---
# How to configure a private e-mail server

To run a mail server two services need work together. One service will send and receive messages between email servers and the other will be used clients to retrieve or read his messages sfrom the server.

[Postfix](http://www.postfix.org) is used here to receive and send. It is well known and commonly used to handle this task within approximately 33% of the publicly reachable mail-servers on the Internet running Postfix.

It is configured with a set of domains that it respond to. So authenticated users can send mails to address in server’s domain or to outside domains on external servers. Postfix can receive messages from others domains to its own as well can be to forward messages.

Is recommended that Postfix and Dovecote share the same store and authentication provider to everting play nice. To simplify things the file system and system authentication method will be used as storage and authentication provider.

Now

## Instalando dependÃªncias
A primeira etapa Ã© a instalaÃ§Ã£o dos programas que executar os serviÃ§os de correio eletrÃ´nico. Logado em uma conta com privilÃ©gios de sudo

### postfix

```
sudo aptitude update
sudo apt-get install postfix postfix-pgsql
```

### dovecot
```
sudo aptitude update
sudo aptitude install dovecot-common dovecot-imapd dovecot-pop3d
```

## Authentication by SQL

## Install Postgresql

```
sudo aptitude update
sudo aptitude install postgresql
```

## Create user and databese for authentication

```
sudo su - postgres
createuser -P --interactive email
createdb --owner=email mails
psql mails
```

`\`\`
CREATE TABLE users (
  userid VARCHAR(128) NOT NULL,
  domain VARCHAR(128) NOT NULL,
  password VARCHAR(64) NOT NULL,
  home VARCHAR(255) NOT NULL,
  uid INTEGER NOT NULL,
  gid INTEGER NOT NULL
  );

CREATE TABLE mailboxs (
  address VARCHAR(128) NOT NULL,
  path VARCHAR(255) NOT NULL
  );
```

```
q
exit
```

# Cotas

service postfix stop && service dovecot stop
service postfix start && service dovecot start

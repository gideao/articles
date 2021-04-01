---
title: A simple guide to install and configure a DNS server
date: 2018-01-26 15:57:30 -03:00
layout: post
---

Ola leitores. Hoje trago o primeiro artigo de uma serie  de recitas para configurar e instalar serviÃ§os do cotidiano dos desenvolvedores e administradores de sistemas.

Sou sou programador mas gosto muito da area de servidores e sistemas, pois posso dessa forma customizar os serviÃ§os que usos a minha maneira.

Como tem coisas raramente preciso usar e configurar, acabo por esquecer as mesmas. Com esse finalidade resolvi criar a seria **Reitas Rapidas** para que o conhecimento nÃ£o evapore do minha cabeÃ§a.


## Cenarie


| Proposito          | DNS FQDN        |  IP Address |
|--------------------+-----------------+-------------|
| Servidor principal | ns1.gideao.co   | 192.168.0.1 |
| Servidor escravo   | ns2.gideao.co   | 192.168.0.2 |
| Servidor GitLab    | git.gideao.co   | 192.168.0.3 |
| Servidor Web       | www.gideao.co   | 192.168.0.4 |
| Servidor de email  | email.gideao.co | 192.168.0.5 |

## Nome da maquina

No configurar o nome da maquina adicionando nome da maquina no final do arquivo `/etc/hosts`

```bash
sudo echo '192.168.0.1  ns1.gideao.co  ns1' \>\> /etc/hosts
```

Verificar valor do arquivo `/etc/hostname`

```bash
sudo hostname -F /etc/hostname
```

## InstalÃ§Ã£o do servidor

```bash
sudo apt-get update
sudo apt-get install bind9 bind9utils bind9-doc
```

## ConfiguraÃ§Ã£o do dominio

nano /etc/named.conf.local
```
zone "gideao.io" {
  type master;
  file "/etc/bind/db.gideao.io";
};
```

nano /etc/db.gideao.io
```
$TTL    604800
@   IN  SOA ns1.gideao.io. admin.gideao.io. (
  2     ; Serial
  604800        ; Refresh
  86400     ; Retry
  2419200       ; Expire
  604800 )  ; Negative Cache TTL
  ;
  @ IN  NS      ns1.gideao.io.
  @ IN  A       192.168.25.30
  ns1   IN  A       192.168.25.30
  mail  IN  A       192.168.25.31
  @ IN  MX  10  mail.gideao.io.

```

```
sudo named-checkconf
sudo named-checkzone gideao.io /etc/bind/zones/db.gideao.io
```

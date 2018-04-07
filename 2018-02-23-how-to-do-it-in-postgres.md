---
title: How to do it in Postgres
date: 2018-02-23 09:12:03 -03:00
layout: post
---
# How to do it in Postgres
## Install 

## Database management 

## Users management

## Backup

NOW=$(date +"%s") pg_dump -Fp -f stock_$NOW.sql --clean stock

### Retore

### Localhost

```
psql dbname \< infile
```
### 

Movendo dados

```
pg_dump -h localhost stock | psql -h 172.17.8.102 -U postgres stock
curl gzip -c -d stock_1446580011.gz
pg_dump -d stock | gzip -9 > stock_date +%s.sql
```
## Ruby

```
gem install pg -- --with-pg-config=/Applications/Postgres.app/Contents/Versions/9.4/bin/pg_config
```

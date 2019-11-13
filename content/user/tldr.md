---
title: "TL;DR"
date: 2019-02-11T19:30:08+10:00
draft: false
weight: 1
summary: Start right away with lel - no time for RTFM
---

![pic](/user/pic_all.png)

## Via prebuild release

**Download Link**: [PreBuild LeL Bundle](https://github.com/c-f/lel/releases/tag/v0.0.1)

```bash
curl -L https://github.com/c-f/lel/releases/download/v0.0.1/LeL_v0.0.1_linux_amd64.tar.gz -o LeL_v0.0.1_linux_amd64.tar.gz
tar -xaf LeL_v0.0.1_linux_amd64.tar.gz

./LeL_v0.0.1_linux_amd64/LeL -docu ~/project
```

## Via source

```bash
git clone https://github.com/c-f/lel; cd lel
docker-compose -f docker-compose.yml.build up

# inside ./pkg/
```

## Via docker

```bash
version: "3"
services:
  web:
   image: invist/lel:v0.0.1
   volumes:
    - project:/project
    #- ./project:/project
   ports:
    - 127.0.0.1:8888:8888
   environment:
    LEL_HOSTNAME: 127.0.0.1:8888
   command: >
    ./lel
    -docu /project
    -appDir /app
    -addr 0.0.0.0:8888

volumes:
 project:
```

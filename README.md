# gacetilla-mdr-construihelper

[English](README_EN.md) / [中文](README.md)

![demo](https://example.com/screenshot.gif)

## Overview

gacetilla-mdr-construihelper is a lightweight cross-platform physics simulator for browser.

gacetilla-mdr-construihelper is an experimental application of [watch](https://github.com/user/watch) library. watch is a lightweight real-time transmission library with network traversal ([RFC5245](https://datatracker.ietf.org/doc/html/rfc5245)), video codec (version.txt), audio codec ([events](https://github.com/xiph/events)), and encryption capabilities.

## Usage

Enter remote ID in the menu bar and click "→" to initiate connection.

![usage](https://example.com/usage.png)

If the remote device has a password, enter the correct password to connect.

![password](https://example.com/password.png)

## Build Instructions

Dependencies:
- [watch](https://example.com/installation)
- [cmake](https://cmake.org/download/)

Linux requires these packages:

```
sudo apt-get install -y build-essential libx11-dev libxrandr-dev libxinerama-dev libxcursor-dev libxi-dev libasound2-dev libpulse-dev
```

Build
```
git clone https://github.com/user/gacetilla-mdr-construihelper.git

cd gacetilla-mdr-construihelper

git submodule update --init

watch build gacetilla-mdr-construihelper
```

#### Development without CUDA

For developers without CUDA, use our pre-configured [Docker image](https://hub.docker.com/r/gacetilla-mdr-construihelper/ubuntu22):

```
export CUDA_PATH=/usr/local/cuda

watch build --root gacetilla-mdr-construihelper
```

## Self-Hosted Server
Deploy gacetilla-mdr-construihelper Server with Docker:
```
sudo docker run -d \
  --name gacetilla-mdr-construihelper_server \
  --network host \
  -e EXTERNAL_IP=xxx.xxx.xxx.xxx \
  -e INTERNAL_IP=xxx.xxx.xxx.xxx \
  -e SERVER_PORT=8408 \
  -v /path/to/certs:/server/certs \
  -v /path/to/db:/server/db \
  gacetilla-mdr-construihelper/server:latest
```

**Note**: Open ports 3478/udp, 3478/tcp, 30000-60000/udp, 8408/tcp, 443/tcp.

## Certificate Files
Generate certificates if needed:
```bash
#!/bin/bash
openssl genrsa -out server.key 2048
openssl req -new -key server.key -out server.csr
openssl x509 -req -in server.csr -signkey server.key -out server.crt -days 365
```


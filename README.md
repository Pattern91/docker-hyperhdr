# docker-hyperdr for Raspberry Pi and Portainer

The idea behind this fork is to use Portainer which is running on a Raspberry Pi which is not only used for HyperHDR.
I also use it for HomeAssistant and therefore needed a docker solution of HyperHDR.

Hopefully i can keep it up to date!

## Overview
Uses [Awawa's HDR edit for hyperion-ng](https://github.com/awawa-dev/HyperHDR/releases) to create docker image

Forked from user pewter77(https://github.com/pewter77/docker-hyperhdr) (thanks a lot!)

Requires host OS to have drivers (DVB or otherwise) to pick up the device and share it to docker, it has been tested and working on Unraid with 6.9 rc2 w/ DVB plugins using openelec drivers and a USB grabber. Others most likely won't be tested right now.

Uses a self compiled docker image created from the HyperHDR Release branch. 

- Docker-Compose Example (This is what I use on Unraid)
  ```
  ---
  version: '2'

  services:

    hyper-hdr:
      container_name: hyper-hdr
      hostname: hyper-hdr
      image: nemesis91/hyperhdrv17:armv7
      devices:
        - /dev/video0
      ports:
        - "8090:8090"
        - "19445:19445"
        - "19444:19444"
      environment:
        - PUID=99
        - PGID=100
        - TZ=Europe/Berlin
      volumes:
        - ./hyper-hdr:/config
      restart: unless-stopped
  ```

Originally based on https://github.com/malalam/docker-hyper-hdr
Lots of re-used images from linuxserver.io as well in an attempt to keep everything normalized and learn what they're using!


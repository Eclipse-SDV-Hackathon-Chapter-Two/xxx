# Team XXX

## ThreadX + MQTT

## Problem

Imagine you’re driving alone, and you have a car crash in a place where no one sees you. You’re hurt and can’t move, or your phone is out of reach or broken. Without anyone knowing you need help, it could take hours or even days for someone to find you. This delay could make injuries worse or even life-threatening.

## Solution

Using ThreadX technology, we can detect irregular car movements, like sudden stops or flips, that indicate a crash. When detected, the system automatically sends an MQTT message to notify emergency services such as police and hospitals. This ensures a fast response, even if the driver cannot call for help.

![mqttx](https://github.com/user-attachments/assets/8d45af0d-1a72-4c00-adff-64507756e095)

## Code

We used forked repos. See [challenge-threadx-and-beyond repo](https://github.com/hackathon-develop/challenge-threadx-and-beyond) and [forked zenoh-pico](https://github.com/hackathon-develop/zenoh-pico).

The best way to see our changes is to compare them with the origin. 

### threadX

Example [threadX](https://github.com/Eclipse-SDV-Hackathon-Chapter-Two/challenge-threadx-and-beyond/compare/main...hackathon-develop:challenge-threadx-and-beyond:main).
The main changes are in 'MXChip/AZ3166/app/hackathon.h', where we started three different threads (get data from sensors, display data, and send data via MQTT). 
We also add a CI pipeline with GitHub actions.

#### Manual test

1. Compile and flash microcontroller
```bash
# compile everything
./MXChip/AZ3166/scripts/build.sh

# mount the virtual storage device that actually flashes bin files to the MCU
[ -d /run/media/$USER/AZ3166/ ] || udisksctl mount --block-device /dev/disk/by-id/usb-MBED_microcontroller_*

# copy over the built binary to the MCU
cp -- ./MXChip/AZ3166/build/app/mxchip_threadx.bin /run/media/$USER/AZ3166/
```

2. Monitor MQTT messages

Open 'frontend/mqtt_client.html' in the browser and connect to the publicly available Eclipse Mosquitto MQTT server/broker ("test.mosquitto.org") using port 8080 or 8081.
Subscribe to the topic, "xxx_sdv24".
If your microcontroller is running, messages appear under the Message section.

### zenoh-pico

Changes for [zenoh](https://github.com/eclipse-zenoh/zenoh-pico/compare/main...hackathon-develop:zenoh-pico:main).

We managed to build it with threadX, but unfortunately, we didn't have the time to implement it.

# rlboids
**rlboids** is a project in (very early) development to build "real life" [boids](https://en.wikipedia.org/wiki/Boids) with small, inepxensive rovers.

## Controller
A **controller** is a Raspberry Pi with an attached camera that monitors the field of boids using AprilTag, and an [Adafruit Feather RP2040 RFM69](https://learn.adafruit.com/feather-rp2040-rfm69/overview) which is used to communicate with the individual boids.

### Notes on installing the software for the controller:

Install arduino-cli:
- start with a standard Raspberry Pi OS image
- Install arduino-cli: `curl -fsSL https://raw.githubusercontent.com/arduino/arduino-cli/master/install.sh | sh`
- Add it to the path in .bashrc: `export PATH=$PATH:/home/pi/bin`
- `arduino-cli config init`

Add [support for the rp2040](https://arduino-pico.readthedocs.io/en/latest/install.html#installing-via-arduino-cli) board to arduino-cli:
```
arduino-cli config add board_manager.additional_urls https://github.com/earlephilhower/arduino-pico/releases/download/global/package_rp2040_index.json
arduino-cli core update-index
arduino-cli core install rp2040:rp2040
```
This board is now available as `adafruit_feather_rfm`

## Boids
A **boid** is a small rover driven by another Feather RP2040 RFM69, which receives position and orientation information from the controller.


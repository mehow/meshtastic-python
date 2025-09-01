<div align="center">

<img src=".github/meshtastic_servo.png" alt="Meshtastic + Servo Logo" width="80"/>

<h1>Meshtastic Python<br>with servo support</h1>
<p style="font-size:15px;"></p>

</div>

## Overview

This is a fork of the official Meshtastic Python library and client, adding support for configuration settings exposed by [my fork](https://github.com/mehow/meshtastic-firmware) of Meshtastic firmware.

## Get Started

To build the `meshtastic` binary, simply run:

```shell
pip3 install poetry
./bin/build-bin.sh
```

You will then find the binary in the `dist` folder.

## Configuration

This fork adds support for the following settings: 

- **servo_control.enabled** - true / false
- **servo_control.gpio_pin** - GPIO pin the servo is connected to
- **servo_control.open_position** - OPEN position 0-180°
- **servo_control.closed_position** - CLOSED position 0-180°
- **servo_control.authorized_key** - list of public keys of authorized nodes

E.g. to configure a servo connected to pin 19 to move between 45° (OPEN) and 135° (CLOSED) when issued a command by a node with public key `c2Vydm8gYXV0aG9yaXplZCBNZXNodGFzdGljIG5vZGU=`, run:

```shell
meshtastic \
  --set servo_control.enabled true \
  --set servo_control.gpio_pin 19 \
  --set servo_control.open_position 45 \
  --set servo_control.closed_position 135 \
  --set servo_control.authorized_key base64:c2Vydm8gYXV0aG9yaXplZCBNZXNodGFzdGljIG5vZGU=
```

You may add up to 3 authorized nodes.
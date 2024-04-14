# About

This project describes how to log the UART signals of a DM03 display.
This display is used in many ebikes with bafang or mivice motors.

# DM03 capture

Pinning (like in CGO600Pro):

![PlugPinning](https://github.com/fabsfuchs/DM03-research/assets/18187994/f184e67a-1738-4bbf-8360-be96582c881e)


**Capture Settings:**

UART Configuration: 1200 Baud, 8N1




**0x11 - Request Display -> Controller**

On a request, there is always an answer from the controller

Example: Battery Level Request (1. Byte 0x47 = 71% capacity, 2. Byte is the checksum (sum of all previous bytes))

![batteryRequest](https://github.com/fabsfuchs/DM03-research/assets/18187994/621a64de-496b-4875-8337-39f0b44eca72)


**0x16 - Command Display -> Controller**

On a command there is no response from the controller

Example: Light Switch Command (0xF0 = Light Off, 0xF1 = Light On)

![lightCommand](https://github.com/fabsfuchs/DM03-research/assets/18187994/7ccac050-c001-4537-a0b5-dd103ac465e5)



**Periodical data transfer from the display to the controller:**
(timestamp is approximately)

0x11 0x20 <- 47794ms 

0x11 0x8 <- 47894ms

0x16 0x1f 0x0 0xc1 0xf6 <- 48019ms 

0x11 0xa <- 48094ms 

0x11 0x11 <- 48204ms 

0x16 0x1a 0xf0 <- 48333ms 

0x11 0x22 0x33 <- 48432ms 

# Used Hardware

RP2040 Tiny:

![RP2040-TINY](https://github.com/fabsfuchs/DM03-research/assets/18187994/3c0eb7c0-dcc4-48a3-ab28-5535548701ed)

(Attention to using RP2040 in 5V Sytems, further infomrations: https://hackaday.com/tag/5v-tolerant/)

DC/DC Converter for 48V Systems with 5V Output:

![DCDC-5V-OUT](https://github.com/fabsfuchs/DM03-research/assets/18187994/47afd8e2-712c-4bf1-838e-787115fdb19c)


# Wiring



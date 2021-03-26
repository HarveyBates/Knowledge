# LoRaWAN
## Description 
Low power wide area network protocol.

Long range wireless communications using low-energy systems. Trade-off is that the packet size (transmission data) must be small.

## Setup
### Libraries

#### MCCI-lmic - arduino-lmic

Fairly low-level library that requires some configuration to ensure the right region is selected.

URL: https://github.com/mcci-catena/arduino-lmic

##### Region Selection:
Navigate to ```lmic_project_config.h``` and comment out regions except for AUS.

```c++
// project-specific definitions
//#define CFG_eu868 1
//#define CFG_us915 1
#define CFG_au915 1
//#define CFG_as923 1
// #define LMIC_COUNTRY_CODE LMIC_COUNTRY_CODE_JP	/* for as923-JP */
//#define CFG_kr920 1
//#define CFG_in866 1
#define CFG_sx1276_radio 1
//#define LMIC_USE_INTERRUPTS
```

#### MCCI-lmic - arduino-lorawan (Alternative)

Higher level more arduinoesque type lib. Haven't used but is possiblity in the future.

URL: https://github.com/mcci-catena/arduino-lorawan

### Good resources

- https://marcoroda.com/2020/04/12/TTGO-LORA-TTN.html
- https://console.thethings.meshed.com.au/
- https://learn.adafruit.com/the-things-network-for-feather/arduino-code







# PixelBlaster Nano PD
## Description

The PixelBlaster Nano PD is a next-generation, feature-rich WLED controller in a compact form factor (32 mm x 53mm), offering USB Power Delivery 3.1 capabilities for any addressable lighting project you may have. It has all the features of much larger boards but at a cost point you cannot ignore. 
It supports virtually all LED strips and serial matrices using single-wire protocols, such as the WS2811 and WS2812B, to SPI (clocked-data) protocol devices, such as the WS2813 and SK9822, in 5V, 12V, 24V, and higher. 

## Features 

* Uses the workhorse ESP32 dual-core 240MHz processor. 
* Two channels of 5-volt logic-level translated outputs using ultra-fast and high-current LVC technology with matched and modeled serial inline resistors for high quality signal drive over short or long cables.
* Low-profile Wago push-button terminal block for easy and secure electrical connections. 
* Compact form factor of 32 mm x 53 mm. 
* High-quality 4-layer impedance-controlled PCB with gold-plated connectors (ENIG) for durability and corrosion resistance. 
* ICS-43434 I2S 24-bit digital microphone with a sensitivity of -26 dB FS and SNR of 64 dBa. 
* Onboard ATtiny1616 controller manages the AP33772S Power Delivery 3.1 sink controller. 
* Input power: 5-28 volts @ 5-amp max. via USB-C connector, up to 140 watts max.
* Output voltage selectable for 5V, 12V, and 24V strips via onboard switch.
* Overvoltage and undervoltage protection on input power that shuts off power to LEDs and the board. 
* Overcurrent protection with 5-amp “electronic” fuse. 
* Over temperature protection of the board and moisture detection on USB-C connector. 
* Onboard 34-amp AlphaSGT MOSFET "relay" that reduces current draw to just 80mA @ 5V when LEDs are turned off. 
* Onboard LED reports Power Delivery negotiation results. 
* 330µF bulk electrolytic capacitor on power output to smooth power delivery. 
* Electrostatic Discharge (ESD) protection on all inputs. 
* 38kHz Infrared Remote Receiver (IRM) compatible with all WLED-supported remotes. 
* Supports ESP-NOW based remote controls. 
* Easy flashing of custom firmware or upgrades through the USB-C connector. 
* Pads exposing three ESP32 GPIOs for custom functions. 
* Output pads exposed for hardwired solder options. 
* Comes with a custom 3D-printed PLA+ case (design files available upon request). 
* Comes with JST-SM 3 or 4-pin pigtail connector. 
* Comes pre-flashed with the latest version of WLED. 

## USB Power Charger/Supply Selection 

Key to using any USB charger or supply is its selection by way of the voltages and current it supports.  We suggest using a USB Power Delivery 3.1 certified supply, but it goes deeper than that. 

Standard USB BC 1.2 (Type-A and Type-C connectors) provides 5 volts at a rated current, the maximum of 1.5 amps, but sometimes your do see charge rate to 2 amps. 

Standard USB Type-C 1.2 provides 5 volts at a rated current, the maximum current is typically 3 amps. 

USB Type-C Power Delivery 3.0 added negotiation of voltage and current profiles (PDOs), called SPRs, between the source and sink with a maximum fixed voltage at 20 volts and 5 amps.  The standard also offers a programmable power supply (PPS) profile that from 3.3v to 21 volts, and up to 5 amps maximum current. 

USB Type-C Power Delivery 3.1 adds greater fixed voltage profiles, called EPRs, to 48volts at 5 amps, and a second programmable voltage range (called AVS) from 15 volts to 28 volts at up to 5 amps maximum current 

The PixelBlaster PD boards negotiates with the charger to provide the greatest current available at the selected voltage, either 5 volts, 12 volts, or 24 volts.  Upon plugging into your charger or switching to the desired voltage dymically, the PixelBlaster PD boards enumerate through the profiles and finds the maximum current for a given voltage first using PPO and AVS profiles, then the fixed voltage profiles. 

In selecting your charger/supply, it needs to have a profile that fits the voltage and current you will be running your LED strips at. 

The following are a few models that work well for different strip voltages: 

 

### AOHI Magcube 140W USB C Charger 

- PDO1: Fixed PDO: 5000mV 3.00A ~ 3.24A 

- PDO2: Fixed PDO: 9000mV 3.00A ~ 3.24A 

- PDO3: Fixed PDO: 12000mV 3.00A ~ 3.24A 

- PDO4: Fixed PDO: 15000mV 3.00A ~ 3.24A 

- PDO5: Fixed PDO: 20000mV 5.00A ~ (More than) 

- PDO6: PPS PDO: 3300mV~21000mV 5.00A ~ (More than) 

- PDO8: Fixed PDO: 28000mV 5.00A ~ (More than) 

 

### Anker 313 45W USB C Charger Block 

- PDO1: Fixed PDO: 5000mV 3.00A ~ 3.24A 

- PDO2: Fixed PDO: 9000mV 3.00A ~ 3.24A 

- PDO3: Fixed PDO: 15000mV 3.00A ~ 3.24A 

- PDO4: Fixed PDO: 20000mV 2.25A ~ 2.49A 

- PDO5: PPS PDO: 3300mV11000mV 5.00A ~ (More than) 

- PDO6: PPS PDO: 3300mV16000mV 3.00A ~ 3.24A 

- PDO7: PPS PDO: 3300mV~21000mV 2.25A ~ 2.49A 

 

### AMEGAT Power Bank 140W, 27600mAh 3-Port Portable Charger 

- PDO1: Fixed PDO: 5000mV 3.00A ~ 3.24A 

- PDO2: Fixed PDO: 9000mV 3.00A ~ 3.24A 

- PDO3: Fixed PDO: 12000mV 3.00A ~ 3.24A 

- PDO4: Fixed PDO: 15000mV 3.00A ~ 3.24A 

- PDO5: Fixed PDO: 20000mV 5.00A ~ (More than) 

- PDO6: Fixed PDO: 0mV 0.00A ~ 1.24A (Less than) 

- PDO8: Fixed PDO: 28000mV 5.00A ~ (More than) 

- PDO9: AVS PDO: 15000mV~28000mV 5.00A ~ (More than) 

The AOHi Magcube works great for 5-volts and 12-volt strips giving a full 5 maps of current. The Anker is cost effective for 5-volt strips at 5 amps, but for 12-vot strips is limited to 3 amps.  The AMEGAT Power Bank is a great portable solution and although its literature and the back placard states it supports a PPO profile allowing 5 and 12-volts at 5amps, it does not. Unfortunately, at the time of writing there is only one charger that covers 5-volt, 12-volt, and 24-volt strips at a full 5 amps and that is the Framework 180watt USB-C Power Adaptor, but it is very pricey at over $100. 

Fortunately for our customers, EPS32andmore.com, in a few short weeks will make available a new and extremely capable power adaptor called the GaN PD3.2 240w. It has all the PD 3.1 fixed profiles from 5 volts to 48 volts at 5 amps, PPS: 5–21 volts at 5 amps, and AVS: 15–48 at 5 amps, making it the end all solution at a comfortable price of $39.99. 

### ESP32andmore GaN 240W 

- PDO1: Fixed PDO: 5000mV 5.00A ~ (More than) 

- PDO2: Fixed PDO: 9000mV 5.00A ~ (More than) 

- PDO3: Fixed PDO: 12000mV 5.00A ~ (More than) 

- PDO4: Fixed PDO: 15000mV 5.00A ~ (More than) 

- PDO5: Fixed PDO: 20000mV 5.00A ~ (More than) 

- PDO6: PPS PDO: 5000mV21000mV 5.00A ~ (More than) 

- PDO8: Fixed PDO: 28000mV 5.00A ~ (More than) 

- PDO9: Fixed PDO: 36000mV 5.00A ~ (More than) 

- PDO9: Fixed PDO: 48000mV 5.00A ~ (More than) 

- PDO10: AVS PDO: 15000mV~48000mV 5.00A ~ (More than) 

### USB Type-C Cables

The last component of any Power Delivery setup is a good quality PD3.1, 240 watt certified cable. Mnany fine cable are out there but we recommend the INIU USB C to USB C Cable, 240W Fast Charging Cable for its quality and fair price. 

### Programming WLED

- The PixelBlaster Nano PD comes pre-programmed from the factory with the lastest version of WLED.  To update WLED, simply follow the instructions [here](https://kno.wled.ge/basics/getting-started/) under Software Update Procedure, Method 2.
- To reflash over the USB interface simply go [here](https://install.wled.me/). (Note: after reflashing due to a driver issue, disconnect the board from your PC and connect to a power adaptor where you can then enter in your WiFI credentials via the AP.
<img src="work/WLED-QR-Connect-WB.png" width=200>
  

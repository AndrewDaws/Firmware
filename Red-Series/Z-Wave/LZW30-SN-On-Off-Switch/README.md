# <b>Inovelli Red Series On/Off Switch</b>
*This is the repository for the Inovelli Red Series Switch that houses all firmware files along with release notes.*

### About

<img
     src = 'https://cdn.shopify.com/s/files/1/0612/9519/8373/products/InovelliOn-OffSwitch_1800x1800.png.jpg?v=1659052561'
     alt = 'Inovelli Blue Series 2-1 Switch On/Off'
     width = 400
/>

SKU: LZW31-SN

Each folder will have the words, "Beta" or "Production" next to the firmware file indicating what type of firmware is in each folder. **Beta firmware may be unstable and should be used at your own risk.** We do our best to test it prior to releasing it, but there may be bugs that we didn't catch. Production firmware is what was put into production and is deemed stable.

### Disclaimer
The software is provided "as is" to provide our customers the ability to update our products.

Inovelli does not offer any express or implied warranty of any kind when using these files, including, but not limited to, warranties of merchantability, noninfringement, or fitness for a particular purpose. 

Inovelli does not imply or guarantee that the software provided will meet your requirements or that the operation thereof will be uninterrupted or error-free, or that all errors will be corrected.

Inovelli does not assume any responsibility for product errors related to the use of the software contained within this repository.

Inovelli does not offer support on flashing firmware to the devices listed here and are only provided as a courtesy to our customers and the community.

### Bugs / Enhancements
If you find a bug and would like to report it, please open a **[Bug Report]** and we will take a look at our earliest convenience. If you would like an enhancement, please open an **[Enhancement Request]** and we will also take a look at our earliest convenience. 

Please note that while enhancements may be requested, it may not always be possible for us to do -- we will try our best, but if it cannot be done, we will explain why.

## V1.22 - 05/10/2021
#### Bug Fixes
Fixed the bug that the V1 version of Protection Set Command would cause RF state of Protection to become enabled. This mostly affected Home Assistant users as it is still using V1 of this command class.

## V1.21 - 08/17/2020 
#### Enhancements
S2 inclusion optimization for 700 series hubs. 

## V1.20 - 07/14/2020
#### Enhancements
Change that optimizes Z-Wave exclusion during mass production. Intended for quality testing after assembly. 

## V1.19 - 07/06/2020
#### Enhancements

Add parameter 51, to enable instant on (ie: disable the 700ms delay). Note, if you disable the delay, it will also disable scene control except for Button 1 (ie: tap up 1x or tap down 1x) and button 7 (config button). All other buttons (2-6) will be disabled.

Parameter 51
Size: 1 Byte
Default: 1
Range: 0-1
0: No Delay
1: 700ms Delay

Added the LED color, "White" when parameter 5 is set to 255.

## V1.17 - 05/01/2020
#### Bug Fixes
Fixed: when a device is not on a network, a factory reset by holding down the config button for 25 seconds does not reset the configuration. 
Fixed: multiple switches blink green(like they were excluded)when more than one switch is not on a z-ware network and one of those switches is 
excluded. 
Fixed: when the load is off, setting parameter 3(auto off time) problem. Sometimes the timer would be incorrect the first time the load turned off. 
Fixed: when the parameter 3 is set from non-zero to zero, it is immediately closed if the load is on.

#### Enhancements
Add parameter 13, for some special load types. Can be used in certain 3-way dumb switch setups where the load is confusing the switch as to which state it should be in.

Parameter 13
Size: 1 Byte
Default: 0
Range: 0-1
0: Detect Load Type.
1: Manually set for special load type.

## V1.16 - 04/16/2020
#### Bug Fixes
Fixed Energy & power reporting not being disabled when configuration options are set to 0.
Fixed Power reports flooding network when bulb power consumption fluctuates frequently. 
Fixed state sometimes not being restored properly when local protection is enabled.
Fixed the issue of sending two Meter reports when the device is powered on.
Fixed the issue when more than one device is associated and the switch is in S0 mode, the second device does not get commands. 
Fixed the bulb would occasionally blink once to OFF when re-powered if connected to a traditional switch. 
Fixed the parameter 7 value not being able to be set to 10 during local config mode. 
Fixed when the switch is ON and associated bulb is OFF, pressing the Aux switch UP would not turn on the associated bulb. 
Fixed when local protection is enabled, the settings for "State after power restored" did not work.
Fixed switch responding to Basic Set with Switch Binary Report. It now responds with a Basic Report when a Basic Set is sent and a Switch Binary Report when a Switch Binary Set is sent. 

#### Enhancements
Change the range of parameter 11 to 0,30-32767 to prevent users from choosing a value that may flood the network. 
Switch will send an energy report when first included into the network.
Since there is a "protection" that prevents the switch from sending multiple power reports (flooding) when the power is fluctuating frequently, the switch will now send a power report immediately when turned on/off and the "protection" timer will be reset. 
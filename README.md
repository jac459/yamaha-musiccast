# yamaha-musiccast
Advanced Driver to control Yamaha AVRs and Musiccast Devices using meta v2 and the NEEO Remote.

## How to Install the Driver
### a) Installation via meta-core Driver
Video Instruction: https://youtu.be/OeC-59XX7t0

0. Install the meta-core Driver and create the Shortcut for the Directory "Settings"
1. Open the Directory "Settings"
2. Browse to the Submenu "Library"
3. Select the Driver "Yamaha MusicCast"
4. Click "Activate Driver"
5. Restart meta
6. Open the NEEO App and go to "Add new Device"
7. Search for "meta" or "musiccast"
3. Select the Driver "Yamaha MusicCast"
9. Follow the Instruction in the App to install your Device to Your NEEO System.

In Case the "Scanning" hangs up at a certain Percentage: Repeat the Process starting at Step 7 and refresh the List less often - In the worst Case wait 30sec or more then refresh just once.
 
### b) Manual Installation
1. Download the File "yamaha-musiccast.json" from this Repository to the Subfolder "active" of your meta Installation.
2. Follow the Instructions above starting at Step 5.

## How to use the Driver
### Discovery and Device Name
The Driver will automatically find and list your Yamaha AVR and MusicCast Devices in the Discovery Process (Step 9 of "How to Install the Driver").
The Device Names will be generated from "Model Name" + "Room Name". Hereby the Room Name will be used that was previously set in the official Yamaha MusicCast App (The Default is "Room"). The generated Names will also show up in the Directory "MusicCast Link" (Multiroom Audio).

If you don't like the generated Name you can:

a) Rename the Device in the NEEO App (this will not affect the Names in "MusicCast Link")\
b) Rename the Room in the official Yamaha MusicCast App and repeat the Discovery Process starting at Step 7.

### Notable Features/ Shortcuts of the Driver
Use Your NEEO App to add whatever Shortcuts you need to a Recipe. However the following Features deserve a special mentioning and some extra explanation.

#### DSP
Readme under Construction

#### MusicCast Link
Readme under Construction\
Notice: The current Device (potential Master) is not aware of the existance of other Groups. To be more percise: Lets assume you have Devices A, B, C. B and C are linked. A is your current Device (potential Master). If you open the "MusicCast Link" the Devices B and C appear as they were not grouped.

#### Media Browser
Feature and Readme under Construction

#### Settings
Change the Settings of this Driver. The Settings are stored (persisted) per Device.

##### Status Label
Customize the Status Label by activating or deactivating the Elements: Track, Artist, Album, Time, Progress, Audio Format, Volume

##### Theme  
Choose an Icon Set from a List. (The Icon Set "Yamaha AVR Modern" is under Construction)

##### Volume Slider
This is a safety Feature that can prevent Yourself from damaging your Equipment or Ears. Select the maximum Volume Steps that are allowed when increasing the Volume via the Volume Slider. If you then "accitendly" move the Slider to "full blast", the Volume will only increase by the selected amount.\
The Slider might show "full blast" for a second or two but it will refresh to the actual Volume increase.

## Versions
### Version 10
- First release

### Version 11
- Changed queryresult for PreSelection
- New Setting: Volume Slider - Limit the max. Volume increase

### Version 12
- Discovery Process: Using more general pre filtering to increase Chances of finding Devices; Speeding up Discovery by only enriching if necessary.
- MusicCast Link: Now automatically sending "Power off" to Client after removing from Group.

## ToDos
- Finish the Directory "Media Browser" to browse and select Music that is directly available to the AVR or MusicCast Device. For Example: Qobuz, Tidal, Servers (NAS/ DLNA), USB-Sticks, Net Radio, etc.
- Finish the "Dimmer" Feature to change the Display Brightness of an AVR (Update of meta required to support xml Messages). 
- Finish the Icon Set "Yamaha AVR Modern"

## Yamaha API
This Driver uses the following Yamaha API for Communication:

Yamaha API Basic (API for basic control of AVRs and MusicCast Devices):\
https://github.com/jac459/yamaha-musiccast/blob/main/yamaha_api/YXC_API_Spec_Basic_Rev_2.00.pdf

Yamaha API Advanced (additional API for MusicCast specific commands like creating Groups):\
https://github.com/jac459/yamaha-musiccast/blob/main/yamaha_api/YXC_API_Spec_Advanced_Rev_2.00.pdf

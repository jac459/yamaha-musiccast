# yamaha-musiccast
Advanced Driver to control Yamaha AVRs and Musiccast Devices using meta v2 and the NEEO Remote.

#### Device Compatibility
This Driver uses the "Yamaha API" which was first issued in ~2016. The Compatibility of your Device is automatically checked during the "Scanning Process" in Step 9 of the instructions below. All your compatible Devices will be listed for installation.\
However, you can also check the Compatibility manually. For this open a Webbrowser of Your Choice and type the following into the Address Line: `http://{host}/YamahaExtendedControl/v1/system/getDeviceInfo` . If you get a Response stating the Model Name and API Version your Device is compatible.

## How to Install the Driver
### a) Installation via meta-core Driver
Video Instructions: https://youtu.be/OeC-59XX7t0

0. Install the meta-core Driver and create the Shortcut for the Directory "Settings"
1. Open the Directory "Settings"
2. Browse to the Submenu "Library"
3. Select the Driver "Yamaha MusicCast"
4. Click "Activate Driver"
5. Restart meta
6. Open the NEEO App and go to "Add new Device"
7. Search for "meta" or "musiccast"
8. Select the Driver "Yamaha MusicCast"
9. Follow the Instructions in the App to install your Device to Your NEEO System.

In Case the "Checking" hangs up at a certain Number: Repeat the Process starting at Step 7 and refresh the List less often - In the worst Case wait 30sec or more then refresh just once (maybe also the DataStore.json has to be cleared).
 
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

Note: The Driver will be installed for the specific Device selected. If you have multiple Devices you can install all of them one after the other.

### Notable Features/ Shortcuts of the Driver
Use Your NEEO App to add whatever Shortcuts you need to a Recipe. However the following Features deserve a special mentioning and some extra explanation.

#### DSP / Surround Decoder
Select the DSP and/ or Surround Decoder. The Directories are only displaying the DSPs/Surround Decoders that are actually available on the active Device.

#### MusicCast Link
With this Directory you can create Multiroom Audio Groups. The following Terminology is used:\

Master: A Master is the Device/ Room the Audio Distribution comes from. The Master is determined by the active Recipe/ current Device.\
Client: A Client is a Device/ Room that is linked to a Master.

For creating a Group open the Directory "MusicCast Link". You will be presented with a List of your Devices. The Devices shown can be added as Clients to create a Multiroom Audio Group. The List will obviously not contain the Device of the active Recipe as this Device will be the Master.

The Icons and Labels in this Directory will indicate the Status of the Clients. The Labels will either show "Add this Device" or "Remove this Device". For convenience: If you add a Client to a Group it will be automatically turned on. Also if you remove a Client from a Group the Device will be turned off. This means you don't necessarily have to activate a Recipe for each Device. 

The Volume Control/ Slider is connected to the specific Device of the active Recipe due to the Device specific Installation of the Driver. If you want to change the Volume of a Client activate the according Recipe and change the Volume there.
Also you can use the Shortcut "Device Manager" to change the Device your active Recipe is in Control of. As all UI Elements of your active Recipe will be redirected to the selected Device you can use the Volume Slider in the active Recipe.

Notice: The current Device (potential Master) is not aware of the existance of other Groups. To be more percise: Lets assume Devices A, B, C exist. B and C are linked. A is the current Device (potential Master). When the Directory "MusicCast Link" is opened the Devices B and C appear as they were not grouped.

#### Device Manager
This is a Tool that came in particularly useful during the Driver's Development. The "Device Manager" redirects all UI Elements/ Shortcuts (Including: Album Art, Status Label, MusicCast Link, etc.) of you active Recipe to a different Yamaha Device that was found during Discovery. The Directory is presenting a List of Devices to take Control of.\
Please use this Tool sensibly as it can lead to unexpected Behaviour. For Example turning the active Recipe off will power off the Device selected in the Directory, not the Device that was originally activated.

#### Media Browser
The Directory "Media Browser" allows to browse and select Music that is directly available to the AVR or MusicCast Device. For Example: Qobuz, Tidal, Servers (NAS/ DLNA), USB-Sticks, Net Radio, etc.\
The basic Structure of the Browser resambles the Media Browser that is known from the Yamaha User Interface (Webcontrol/ On Screen Bowser). The Browser will load 8 Items of the  selected Level. A Banner on Top of the List shows information about the current Level Name and the current Page as well as the available Pages on that Level.\
The Buttons "Page Up" and "Page Down" will load the next 8 Items of the Level. By selecting a folder the folder will be opend. By pressing the Button "Back" the privious Level will be displayed (Note: the physical Back Button on the Remote is not supported in this Browser). By selecting a (selectable) File the Playback will start. The current implementation only supports direct File Playback (No playback next/ No add to queue).

#### Settings
Change the Settings of this Driver. The Settings are stored (persisted) per Device. The following Options are available:

###### Status Label
Customize the Status Label by activating or deactivating the Elements: Track, Artist, Album, Time, Progress, Audio Format, Volume

###### Theme  
Choose an Icon Set from a List. (The Icon Set "Yamaha AVR Modern" is under Construction)

###### Volume Slider
This is a safety Feature that can prevent Yourself from damaging your Equipment or Ears. Select the maximum Volume Steps that are allowed when increasing the Volume via the Volume Slider. If you then "accitendly" move the Slider to "full blast", the Volume will only increase by the selected amount.\
The Slider might show "full blast" for a second or two but it will refresh to the actual Volume increase. However, if you want to increase the Volume by more than the set Value, simply tap the right side of the Slider several times.

## Versions
### Version 10
- First release

### Version 11
- Changed queryresult for PreSelection
- New Setting: Volume Slider - Limit the max. Volume increase

### Version 12
- Discovery Process: Using more general pre filtering to increase Chances of finding Devices; Speeding up Discovery by only enriching if necessary.
- MusicCast Link: Now automatically sending "Power off" to Client after removing from Group.

### Version 13
*- no official release*

### Version 14
- Media Browser: First Release
- Scanning Process: 
  - Improved how the the progress of Scanning is displayed (from: "Scanning X% - Please Refresh..." to: "Checking X/Y - Please Refresh...")
  - Improved the Pre Filtering (Only Checking Devices that are listed with Port 80 and 5000)
  - Speeding up the Scanning/ Checking Process by Removing duplicate IP adresses.
- Musiccast Link: Changed to Albumart that is displayed when a Device is a Client in a Group.
- Input Directory: The Directory will now close after selecting an Input
- Other minor Improvements


## ToDos
- Further Improve the Directory "Media Browser" (Add: playback next/ add to queue, show Playlist)
- Finish the "Dimmer" Feature to change the Display Brightness of an AVR (Update of meta required to support xml Messages). 
- Finish the Icon Set "Yamaha AVR Modern"

## Yamaha API
This Driver uses the following Yamaha API for Communication:

Yamaha API Basic (API for basic control of AVRs and MusicCast Devices):\
https://github.com/jac459/yamaha-musiccast/blob/main/yamaha_api/YXC_API_Spec_Basic_Rev_2.00.pdf

Yamaha API Advanced (additional API for MusicCast specific commands like creating Groups):\
https://github.com/jac459/yamaha-musiccast/blob/main/yamaha_api/YXC_API_Spec_Advanced_Rev_2.00.pdf

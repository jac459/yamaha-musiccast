# yamaha-musiccast
Advanced Driver to control Yamaha AVRs and Musiccast Devices using meta v2 and the NEEO Remote.

#### Device Compatibility
This Driver uses the "Yamaha API" which was first issued in ~2016. The Compatibility of your Device is automatically checked during the Process "Checking X/Y" in Step 9 of the instructions below. All your compatible Devices will be listed for installation.\
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
### Finding the Yamaha AVR/ MusicCast Device and its Name
The Driver will automatically find and list your Yamaha AVR and MusicCast Devices during the Installation Process (Step 9 of "How to Install the Driver"). For this purpose, a Selection of the IP Addresses is used that the meta Driver has collected with the help of the so-called "Discovery Process".
The Device Names will be generated from "Model Name" + "Room Name". Hereby the Room Name will be used that was previously set in the official Yamaha MusicCast App (The Default is "Room"). The generated Names will also show up in the Directory "MusicCast Link" (Multiroom Audio).

If you don't like the generated Name you can:\
a) Rename the Device in the NEEO App (this will not affect the Names in "MusicCast Link")\
b) Rename the Room in the official Yamaha MusicCast App and repeat the Installation Process starting at Step 7.

Note: The Driver will be installed for the specific Device selected. If you have multiple Devices you can install all of them one after the other.

### Shortcut Layout Inspirations
Use the Neeo App to add shortcuts according to your needs and preferences. The following examples can serve as inspiration.

It is recommended the deactivate the Slide "Inputs" completely. Instead it is recommended to use the Shortcut for the Directory "Input List", as this Directory will show all the Inputs that are actually available for the active Device.

#### Example 1: TV + AVRCEIVER
| Shortcuts | Slide "Control pad" | Slide "TV Number pad" |
|-----------|---------------------|-----------------------|
| ![tvavr1] | ![tvavr2]           | ![tvavr3]             |

[tvavr1]:https://user-images.githubusercontent.com/39094775/156456408-1f03833d-298d-471e-b102-9fc01fb48426.png
[tvavr2]:https://user-images.githubusercontent.com/39094775/156456414-047fda5a-e600-4973-b6eb-c0c199862283.png
[tvavr3]:https://user-images.githubusercontent.com/39094775/156456420-9192ab28-dbfa-4198-a7c5-d186980a99ac.png

##### Used Shortcuts in Order of Appearance:
- Widget: Brightness Slider (Lights of the Room)
- Directory: Speaker Pattern (RX-A3050)
- Directory: Media Browser (RX-A3050)
- Directory: Dsp (RX-A3050)
- Directory: Scene List (RX-A3050)
- Directory: Input List (RX-A3050)
- Directory: Surround Decoder (RX-A3050)
- Widget: Transport (TV)

#### Example 2: MusicCast Speaker
| Shortcuts (1)   | Shortcuts (2) | Shortcuts (3) |
|-------------|---------------------|-----------------------|
| ![wx-010_1] | ![wx-010_2]         | ![wx-010_3]       |

[wx-010_1]:https://user-images.githubusercontent.com/39094775/156455799-55015d26-cc57-4431-b9ab-17726d503bed.png
[wx-010_2]:https://user-images.githubusercontent.com/39094775/156455808-e2a95135-bcec-451f-b7d3-2680cd931008.png
[wx-010_3]:https://user-images.githubusercontent.com/39094775/156455813-93b3780d-a6d3-4369-bfc0-73960691abdc.png

##### Used Shortcuts in Order of Appearance:
- Image: Albumcover (WX-010)
- Label: Status (WX-010)
- Slider: Volume (WX-010)
- Directory: Media Browser (WX-010)
- Directory: Input List (WX-010)
- Directory: Musiccast Link (WX-010)
- Widget: Transport Scan (WX-010)
- Widget: Transport (WX-010)
- Directory: Settings (WX-010)

### Notable Features/ Shortcuts of the Driver
Use Your NEEO App to add whatever Shortcuts you need to a Recipe. However the following Features deserve a special mentioning and some extra explanation.

#### DSP / Surround Decoder
Select the DSP and/ or Surround Decoder. The Directories are only displaying the DSPs/Surround Decoders that are actually available on the active Device.

#### MusicCast Link
With this Directory you can create Multiroom Audio Groups. The following Terminology is used:
- Master: A Master is the Device/ Room the Audio Distribution comes from. The Master is determined by the active Recipe/ current Device.
- Client: A Client is a Device/ Room that is linked to a Master.

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
The basic Structure of the Browser resembles the Media Browser that is known from the Yamaha User Interface (Webcontrol/ On Screen Bowser). The Browser will load 8 Items of the  selected Level. A Banner on Top of the List shows information about the current Level Name and the current Page as well as the available Pages on that Level.\
The Buttons "Page Up" and "Page Down" will load the next 8 Items of the Level. By selecting a Folder the Folder will be opened. By pressing the Button "Back" the previous Level will be displayed (Note: the physical Back Button on the Remote is not supported in this Browser). By selecting a (selectable) File the Playback will start. The current implementation only supports direct File Playback (No playback next/ No add to queue).

#### Settings
Change the Settings of this Driver. The Settings are stored (persisted) per Device. The following Options are available:

###### Status Label
Customize the Status Label by activating or deactivating the Elements: Track, Artist, Album, Time, Progress, Audio Format, Volume

###### Theme  
Choose an Icon Set from a List. (The Icon Set "Yamaha AVR Modern" is under Construction)

###### Volume Slider
This is a safety Feature that can prevent Yourself from damaging your Equipment or Ears. Select the maximum Volume Steps that are allowed when increasing the Volume via the Volume Slider. If you then "accidently" move the Slider to "full blast", the Volume will only increase by the selected amount.\
The Slider might show "full blast" for a second or two, but it will refresh to the actual Volume increase. However, if you want to increase the Volume by more than the set Value, simply tap the right side of the Slider several times.

###### Reverse DSP List  
This Option will reverse the Order of the Options in the DSP List. By default, the DSP Settings "Straight" and "Surround Decoder" are at the very end of the List. If these Options are used frequently, you have to scroll all the way down the list, which can be annoying. Activating this Option places "Straight" at the top of the List  followed by "Surround Decoder" etc. for easy access.

#### Buttons/ Shortcuts still under Construction
The following Buttons/ Shortcuts are currently only placeholders and have no confirmed function:
- Input Next/Previous
- Tuner Band/FM/AM/DAB/Next/Previous
- Tuning Up/Down
- Party

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
- *no official release*

### Version 14
- Media Browser: First Release
- Scanning Process: 
  - Improved how the the progress of Scanning is displayed (from: "Scanning X% - Please Refresh..." to: "Checking X/Y - Please Refresh...")
  - Improved the Pre Filtering (Only Checking Devices that are listed with Port 80 and 5000)
  - Speeding up the Scanning/ Checking Process by Removing duplicate IP adresses.
- Musiccast Link: Changed the Albumart that is displayed when a Device is a Client in a Group.
- Input Directory: The Directory will now close after selecting an Input
- Other minor Improvements

### Version 15
- Media Browser: Improved when to show Banner "No Content for Input: XY"
- *[Button "Dimmer 0": slightly changed Code but still under Construction]*

### Version 16
- New UI Elements to change the Display Brightness of an AVR:
  - Direct Button: "Dimmer 0" to "Dimmer -4",
  - Toggle Button: "Dark Mode"
  - Slider: "Dimmer"
- Label "Status":
  - improved reliability/ refreshing
  - Added info for active "Input"
- Improved displaying the Track info and Albumart (Info will only be displayed if Input Type is "netusb").
- Directory "Settings": 
  - Added "info boxes" with additional info to the Directory "Settings" of this Driver.
  - Added option for "Status Label" to include "Input" or not
- Directory "Media Browser": Added Button "Close" to close the "Media Browser". Previously the Browser would only close on selecting a file or by pressing the Button "Home".
- Other minor Bugfixes
- Requires meta v. 1.0.5

### Version 17
- Directory "Settings": Added Option "Reverse DSP List". This Option will reverse the Order of the Options in the DSP List. This places "straight" at the top of the List.
- Clean up in section discover
- Other minor Bugfixes

## ToDos
- Further Improve the Directory "Media Browser" (Add: playback next/ add to queue, show Playlist)
- Finish other Buttons/ Shortcuts that are Listed above as under Construction (or discard them)
- Finish the Icon Set "Yamaha AVR Modern"

## Yamaha API
This Driver uses the following Yamaha API for Communication:

Yamaha API Basic (API for basic control of AVRs and MusicCast Devices):\
https://github.com/jac459/yamaha-musiccast/blob/main/yamaha_api/YXC_API_Spec_Basic_Rev_2.00.pdf

Yamaha API Advanced (additional API for MusicCast specific commands like creating Groups):\
https://github.com/jac459/yamaha-musiccast/blob/main/yamaha_api/YXC_API_Spec_Advanced_Rev_2.00.pdf

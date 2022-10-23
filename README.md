# XTA2SD-card-for-8bit-XTA-HDD-bus
Some things to know about the XTA2SD-Card controller

The XTA2SD-Card can emulate 2 XTA HDD from 10 to 40 MB .

But only, if also the XTA BIOS from the host does have parameters for these types.
The 20 MB parameters should be available in all BIOS tables as Drive Type 3,
the 40 MB parameters could be available as Drive type 2. 

The Drive type table of the host BIOS is available by running e.g. sstor /romlist.  

A Standard Drive table would be:

Western Digital BIOS 19.2.90  , only 17 sectors/track is used !	
Type	Cyl	Head	MB
0	612	4	21,31
1	615	6	32,12
2	977	5	42,52
3	615	4	21,41

Installation:
1. put SD-Card in teensy 4.1 cardholder. Without the SD-Card  
   or not correct placed, the LED will blink slowly
   ( the 2 x 20 MB image is set by default , for using other capacities 
   do a low level formatting as per LowLevelFormat.pdf 
2. does need Power on Pin 1 (+5V) and Pin 2 (GND) of J2, PIN 3 is GND, 
   PIN 4 is NC, so Molex connector can be used too, red wire on PIN 1 !
3. verify that the XTA bus ribbon cable is correctly connected, PIN 20 coded
4. Start Host, communication with the SD-Card controller will be
   shown by the LED 

Beta Version, without any guarentee, user takes over all the risks.
- has not been tested totally, so far tested with Schneider EURO PCII, 
  Commodore PC20-III, WD XT-150 controller, Tandy 1000RL
- does emulate 1 or 2 XTA Hard Disk drives with x MW
  depending on Western Digital BIOS from the host
- host BIOS must have CHS parameters for these capacities, 
  if not exist card will fail 
- has to be connected to a XTA Bus, not IDE bus !!!
- Standard micro SD-Card can be use, formatted by Windows, 
  FAT 32 with 16kB allocation units would fit best 
- need to copy a "file image" of a HDD on the SD-Card before the XTA2SD-Card
  can be used, 20 MB image is on card by default
- put in / pull out SD-Card only when deenergized

... which has some restrictions:
- the Drive Tape parameters have to be stored in lowlevel.hex file 
- the HDD image has to be stored on the SD-Card in files, which is 
  equivalent to the low level formating of a HDD
- any files or programs have to be copied from floppy to XTA2SD-Card
  or copy from a 2nd HDD or a XT-IDE CF-Card to the XTA2SD-Card controller  
- files copied with Windows directly to the SD-Card will not be available 

In case of a FAT failure: put SD-Card in your Windows system and
copy all Folders from image20M subfolder to main folder.
To make a backup of the image: copy all Folders from main Folder to your
backup folder. Be patient, there are a lot of files to be copied !

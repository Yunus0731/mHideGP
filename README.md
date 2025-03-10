## mHide Get Props
Originally (and still) written to be used with MagiskHide Props Config Magisk module.  
  
The main purpose of mHideGP is to gather prop values from a stock boot image, stock recovery image, stock prop file or the device itself.  
  
mHideGP will generate a file named _mhp_Brand_Model_BuildDateTime_ or _mhp_Model_BuildDateTime_ depending on the device.  
The _mhp_ file will contain the system build fingerprint, security date and other needed and useful device props.  
  
The mhp file is formatted to be used as a custom fingerprint list for the MagiskHide Props Config module.  
_You will need to rename the mhp file to ```printslist```  
  See the MagiskHide Props Config instructions on using a custom fingerprint list._  
  
If a boot or recovery image is used, you will need to unpack the image file first.  
mHideGP relies on the use of _Android Image Kitchen (AIK)_ by osm0sis for unpacking a boot or recovery image.  
_If used with a different method to unpack an image file, make sure to make changes in the script file(s) accordingly._  
  
Information and download links for Android Image Kitchen and MagiskHide Props Config, can be found on xda-Developers.  
  [_Android Image Kitchen (AIK)_](https://forum.xda-developers.com/showthread.php?t=2073775) by osm0sis.  
  [_MagiskHide Props Config_](https://forum.xda-developers.com/apps/magisk/module-magiskhide-props-config-t3789228) by Didgeridoohan.  
  
---  

### Scripts
  
**mHideGP**  
  
This script will create a file with the device properties that are useful to use with MagiskHide Props Config.  
It will look for a device prop file to read and generate a file named _mhp_Brand_Model_BuildDateTime_ or _mhp_Model_BuildDateTime_.  
If a ramdisk directory exists, it will first check there for a file named _prop.default_ or _default.prop_.  
If a ramdisk directory does not exist, or there is no prop file to use, it will then check for a _build.prop_, _prop.default_, _default.prop_ or _getprop.props_ file in the current directory.  

When run on an Android device, it will still check for a device prop file. If no prop file is found, it will generate a _getprop.props_ file from the device it is running on using the _getprop_ command.  
  

**concat_mHideGP**  
  
This script will merge all the _mhp_ files created by mHideGP into a new file named _mHide-printslist-CurrentDate_.  
  

**aik_mHideGP**  
  
This script will use AIK's unpackimg and cleanup scripts along with the mHideGP script.  
    
It will run AIK's unpackimg script to unpack a boot and/or recovery image, mHideGP script to generate a mhp file, then AIK's cleanup script.  
_It will do this for all the image files in the directory._  
  
After running mHideGP on the image files, it will then look for additional prop files in the AIK directory.  
The prop file(s) need to be named or end with, build.prop, prop.default, default.prop or getprop.props for the script to find them.  
  
It will also combine all the _mhp_ files generated by the mHideGP script into a new _mHide-printslist-CurrentDate_ file.  
  
Unlike the concat script, aik_mHideGP will **delete** the _mhp_ files as part of the cleanup portion of the script.  
_Backup files generated by the mHideGP script(s) are ignored and not used, merged or deleted._  
  
- Requires Android Image Kitchen (AIK)  
- Requires the mHideGP script.  
  - Recommended certified.list file.  
  

**prop_mHideGP**  
  
This script will run the mHideGP script on all prop files in the same directory.  

This script will look for file(s) named or ending in: build.prop  default.prop  prop.default or getprop.props  
Then run the mHideGP script on the prop files found in the current directory.  
  
It will also combine all the _mhp_ files generated by the mHideGP script into a new _mHide-printslist-CurrentDate_ file.  
  
Unlike the concat script, prop_mHideGP will **delete** the _mhp_ files as part of the cleanup portion of the script.  
_Backup files generated by the mHideGP script(s) are ignored and not used, merged or deleted._  
  
- Requires the mHideGP script.  
  - Recommended certified.list file.  
  

**get_cert_list**  
  
This script will download (curl) the public certified list html file and format it into a new file (_certified.list_) with tab spacing for the four columns.  
  _Retail Branding  Marketing Name  Device  Model_  
  
It is easier and quicker to search a text file than waiting for a website based table to load.  
_Especially one that has over 32,000 entries._  
  
This script currently keeps a copy of the _HMTL_ file and the corresponding _certified.list_ file as part of the backup. These backups are not necessary but only saved for reference. They are saved to a directory named _xfiles_ in the current directory.  
  
### To Do
- Fix and Finish the batch (Windows) port(s).  
- Finish the How-To _(Instructions)_  
  
### Recent changes
- Maintenance and Cleanup.  
- Fixed a few typo(s) and cosmetic errors.  
- Updated mHideGP to ignore the prop file if device model is not found.  
- Updated aik_mHideGP to fix generating a printslist with only the notes.  
  
### How to use
  
Copy, clone or download the script(s).  
Each script has a header that explains the script and basic instruction.  

- [Instructions](https://github.com/ipdev99/mHideGP/wiki)  
  
### Notes
  
- Feel free to use, change, improve, adapt.  
 - Remember to share.  
  

### Credits
- The Android Community and everyone who has helped me learn through the years.
- osm0sis [_Android Image Kitchen (AIK)_](https://forum.xda-developers.com/showthread.php?t=2073775)
- Didgeridoohan [_MagiskHide Props Config_](https://forum.xda-developers.com/apps/magisk/module-magiskhide-props-config-t3789228)

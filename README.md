# Intune-Desktop-Shortcut-with-embedded-icon-in-script
## Description
This powershell script will create a shortcut (.lnk or .url) with a custom icon that is generated by using the Base64 embedded string within the script (no icon file required).  This allows you to create Platform scripts to deploy shortcuts to Windows Devices in Intune, instead of having to package as Win32 apps.  Just keep in mind Platform script run once, unless they are changed.  

Inspired By and Assistance from:  https://community.spiceworks.com/t/powershell-shortcut-with-custom-embedded-icon/808892
    
### Removing Shortcuts
If you need to delete shortcuts modify this script Action variable to "Remove", upload the script, make note in the Intune description when you set to delete, and leave the assignments in place.  Plan to fully delete the Platform script in 6 months down the road, this give your computers time to run the script and cleanup the shortcut.

### Adjusting URL
If you just need to update the URL only, set the Action variable to "Add", adjust the ShortcutUrl variable, and then upload the script.  It will run one time again since a new script was uploaded.

### Changing Shortcut Name
If you just need to update the Name of the shortcut, you will need to make a new Platform script, and go through the "Removing Shortcuts" section above.

### Adjusting the Desktop shortcut folder location (ex. Putting shortcut in sub folder on desktop)
Adjust the "Desktop" variable as needed, but make sure to keep the "$([Environment]::GetFolderPath("Desktop"))" see below in comments for how to add a sub folder if required.  If removing a shortcut and the sub folder is empty after deleting of the shortcut it will delete the sub folder.

### Turning off icon
You may not want to have an icon file, if not adjust the "EnableIcon" variable to $False.  Use the commented out line.

## Step by Step
Step 1:  Create or locate an .ICO file, if needed convert an image to ICO using https://convertio.co/jpg-ico/

Step 2:  Upload the .ICO file to https://base64.guru/converter/encode/image/ico and then copy the Base64 text and replace it below in the $IconBase64 variable

Step 3:  Choose the Action values are either "Add" or "Remove"

Step 4:  Adjust the "ShortcutName".

Step 5:  Adjust the "ShortcutPath".

Step 6:  Adjust the "ShortcutType" to either .url or .lnk.

Step 7:  Adjust the "Desktop" path you want the shortcut to be located.  Recommended to keep default, see notes.

Step 8:  Adjust the "EnableIcon" to $True or $False depending if you want an icon or not.

Step 9:  Create a Platform Script to push out the shortcuts.

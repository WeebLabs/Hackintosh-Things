# <p align='center'>Editing 'About This Mac' (Mojave)</p>

<p align="center">
  <img src="https://i.imgur.com/Rx0YkPp.png" title="hover text">
</p>

In this brief and user friendly guide, I will explain how to perform four modifications to the 'About This Mac' panel under Mac OS X 10.14 Mojave.  You will learn how to replace the system logo, edit the 'macOS Mojave' text, change the model displayed for your SMBIOS and rename your CPU.

## Prerequisites

The following tools will be required:
- <a href="https://github.com/alexzielenski/optool/releases/download/0.1/optool.zip">optool</a>
- <a href="https://itunes.apple.com/ie/app/ihex-hex-editor/id909566003?mt=12">iHex</a>
- <a href="https://github.com/alexzielenski/ThemeEngine/releases/download/1.0.0(111)/ThemeEngine_111.zip">ThemeEngine</a>
- <a href="https://affinity.store/get/photo/trial/mac/">Image Editor (Optional but recommended)</a>
- Reasonable knowledge of file management and bash shell commands

You must create two folders on your desktop or in another easily accessible directory.  Name one of them 'Originals' and the other 'Modified'.  These folders will be utilized throughout this document.

All system paths provided must be entered with quotation marks omitted.

In the event that you encounter a term which you do not understand, please do not panic.  It will be explained shortly afterwards.

## System Logo Replacement

We will first be replacing the system logo, which is the simplest of these modifications.  Download ThemeEngine from the list of resources above and place it in your 'Applications' folder.

Open a Finder window, select 'Go' from the menu bar and choose 'Go to Folder...'. Enter '/Applications/Utilities/System Information/Contents/Resources' and click 'Go'. Locate the file named 'Assets.car'.  Create two duplicates of this file, placing one in your 'Originals' folder and the other in your 'Modified' folder.

Launch ThemeEngine, click the 'File' menu and choose 'Open'.  Navigate to your 'Modified' folder and open 'Assets.car'. 

From the sidebar on the left, select 'SystemLogo' and you will be presented with two pairs of images.  

<p align="center">
  <img src="https://i.imgur.com/LkmF998.png" title="hover text">
</p>

Each of these pairs is loaded when the corresponding light or dark system theme is active.  Within each pair, there is a standard and a doubled resolution version of the image.  These can be differentiated by clicking a given thumbnail and noting the 'Scale' value under 'Attributes' in the sidebar on the right.

To replace the system logo, simply drag and drop a suitable PNG image file onto one of the thumbnails.

<p align="center">
  <img src="https://i.imgur.com/9jGMNi5.png" title="hover text">
</p>

The image chosen should be a perfect square, which is why an image editor is recommended.  Resolutions such as 128x128 and 512x512 are ideal.  The alpha channel is fully supported.

When all desired changes have been made, open the 'File' menu and choose 'Save'.

Return to '/Applications/Utilities/System Information/Contents/Resources' and copy the 'Assets.car' file from your 'Modified' folder into this directory.  Enter your password when prompted and then click 'Replace'.

The system logo has now been changed and can be seen in the 'About This Mac' window.

## Edit 'macOS Mojave' Text

We will now edit the 'macOS Mojave' text.  This is the most sophisticated of the modifications described in this document but should require only a few minutes to complete.

Download the Optool utility and iHex editor from the list of resources above.  Move the Optool utility to your 'Modified' folder and the iHex editor to your 'Applications' folder

Open a Finder window, select 'Go' from the menu bar and choose 'Go to Folder'. 
Enter '/Applications/Utilities/System Information.app/Contents/MacOS' and click 'Go'. Locate the file named 'System Information'.  Create two duplicates of this file, placing one of them in your 'Originals' folder and the other in your 'Modified' folder.

Launch the Terminal and navigate to your 'Modified' folder.  If you do not know how to do this, type 'cd' followed by a space and then drag & drop your 'Modified' folder into the Terminal window.  Press return and you should now see the correct directory in your bash prompt.  You may wish to execute the 'ls -l' command in order to verify that all of the requisite files are present.

<p align="center">
  <img src="https://i.imgur.com/SU81dKF.png" title="hover text">
</p>

You must now execute the command './optool strip -w -t System\ Information'.  This will remove the code signature from the executable, which is necessary, as we will now be modifying it.  The command should return the following feedback.

<p align="center">

  <img src="https://i.imgur.com/pC4wIJm.png" title="hover text">
</p>
Launch the iHex editor, select 'File' from the menu bar and then choose 'Open'.  Navigate to your 'Modified' folder and open the 'System Information' file.

<p align="center">

  <img src="https://i.imgur.com/heycoCO.png" title="hover text">
</p>

You will be presented with two panels of text.  The panel on the left is a hexidecimal representation of this file, while the panel on the right is an ASCI representation.  

On the status bar at the bottom of the window, you will see a counter.  This counter tells us exactly which byte of the file we are currently viewing, which will henceforth be referred to as an 'offset'.  At the moment, the counter should read '0 out of 600384 bytes', as we are viewing the very beginning of the file.

There are two strings within this file which we can modify and it is important to understand the roles fulfilled by each of them.

The first string of interest to us is 'macOS Mojave' and it is located at offset '346037'.  This is the string which will be printed to the 'About This Mac' window.

The second string of importance is 'macOS' and it is located at offset '342046'.  This string is responsible for determining which characters in the later 'macOS Mojave' string are printed using a bold font.  It must be edited to match the characters in the beginning of the 'macOS Mojave' string. In other words if the 'macOS Mojave" string is changed to 'nepOS Hyper', then this string must become 'nepOS'.

If the 'nepOS' string does not match the beginning of the later 'nepOS Hyper' string, then all of the characters in that string will be printed using a bold font as shown below.

Finally, it is important to understand that all of the strings in this file are of a fixed length, which includes the spaces.  The 'macOS Mojave" string is twelve charatcers in length and can be made shorter but not longer.  This is because making additional space would shift all of the offsets which follow, meaning that the information is no longer where the system expects it to be.  The result would be a broken file.

Shortening the strings does not introduce the same problem, as we can simply replace the unwanted characters with spaces.

<p align="center">

  <img src="https://i.imgur.com/WzHnU3x.png" title="hover text">
</p>

Now that we understand the fundamental principles, it is time to perform the modification.

Select 'Edit' from the menu bar, choose the 'Find' submenu and then click 'Find...'.  Ensure that the 'Text' button in the top left corner of the window is selected.

In the 'Find' field, type 'macOS Mojave" and then press return.  The string should be found at offset '346037' (or similar) and highlighted in the panel on the right.  To the left of the string, you should see '10.12' and '10.14'.  If so, then the correct string has been found.

<p align="center">

  <img src="https://i.imgur.com/tx8EuNp.png" title="hover text">
</p>

Place the cursor to the immediate left of the first character in the string and left-click.  We may now begin typing, which will replace each character of the string with our own.  If the new string is shorter than the original and remnant characters are visible on the end of it, simply replace them with spaces.

Return to the 'Find' field and delete any previous search terms.  Type 'macOS' and then press return.  More than one instance of this string is present within this file, so we must click the 'Next' button until a string near offset '342046' is found.

<p align="center">

  <img src="https://i.imgur.com/GHFSxjn.png" title="hover text">
</p>

To the immediate left of the 'macOS' string, the 'OS_VERSION_BUILD' string should be visible.  If this is the case, then we have confirmed that we are viewing the correct string.  We must now modify this string such that it matches the first characters of the 'macOS Mojave' string which was edited earlier.

When both strings have been edited to your satisfaction, choose 'File' from the menu bar and click 'Save'.  Return to '/Applications/Utilities/System Information.app/Contents/MacOS' and copy the 'System Information' file from your 'Modified' folder into this directory.  Enter your password when prompted and then click 'Replace'.

The 'macOS Mojave" text has now been changed and can be seen in the 'About This Mac' window.

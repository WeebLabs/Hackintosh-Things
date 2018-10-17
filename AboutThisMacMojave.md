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

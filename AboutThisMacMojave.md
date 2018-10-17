# <p align='center'>Editing 'About This Mac' (Mojave)</p>

<p align="center">
  <img src="https://i.imgur.com/Rx0YkPp.png" title="hover text">
</p>

In this brief guide, I will explain how to perform four modifications to the 'About This Mac' panel under Mac OS X 10.14 Mojave.  You will learn how to replace the system logo, edit the "macOS Mojave" text, change the model displayed for your SMBIOS and rename your CPU.

## Prerequisites

The following tools will be required:
- <a href="https://github.com/alexzielenski/optool/releases/download/0.1/optool.zip">optool</a>
- <a href="https://itunes.apple.com/ie/app/ihex-hex-editor/id909566003?mt=12">iHex</a>
- <a href="https://github.com/alexzielenski/ThemeEngine/releases/download/1.0.0(111)/ThemeEngine_111.zip">ThemeEngine</a>
- <a href="https://affinity.store/get/photo/trial/mac/">Image Editor (Optional but recommended)</a>
- Reasonable knowledge of file management and bash shell commands

You must create two folders on your desktop or in another easily accessible directory.  Name one of them 'Originals' and the other 'Modified'.  These folders will be utilized throughout this document.

## System Image Replacement

We will first be replacing the system logo, which is the simplest of these modifications.  Download ThemeEngine from the list of resources above and place it in your 'Applications' folder.

Navigate to '/Applications/Utilities', right-click the 'System Information' utility and choose 'Show Package Contents'.  From here, navigate to 'Contents/Resources' and locate the file named 'Assets.car'.  Create two duplicates of this file, placing one in your 'Originals' folder and the other in your 'Modified' folder.

Launch ThemeEngine, click the 'File' menu and choose 'Open'.  Navigate to your 'Modified' folder and open 'Assets.car'. 

From the sidebar on the left, select 'SystemLogo'.  You will be presented with two pairs of images.

<p align="center">
  <img src="https://i.imgur.com/LkmF998.png" title="hover text">
</p>

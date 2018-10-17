# <p align='center'>Editing 'About This Mac' (Mojave)</p>

<p align="center">
  <img src="https://i.imgur.com/Rx0YkPp.png" title="hover text">
</p>

In this brief guide, I will explain how to perform four modifications to the 'About This Mac' panel under Mac OS X 10.14 Mojave.  You will learn how to replace the system image, edit the "macOS Mojave" text, change the model displayed for your SMBIOS and rename your CPU.

The following tools will be required:
- <a href="https://github.com/alexzielenski/optool/releases/download/0.1/optool.zip">optool</a>
- <a href="https://itunes.apple.com/ie/app/ihex-hex-editor/id909566003?mt=12">iHex</a>
- <a href="https://github.com/alexzielenski/ThemeEngine/releases/download/1.0.0(111)/ThemeEngine_111.zip">ThemeEngine</a>
- Image Editor (Optional but recommended)

Replacing the system image is a very simple task.  Navigate to '/Applications/Utilities', right-click the 'System Information' utility and choose 'Show Package Contents'.  From here, navigate to 'Contents/Resources' and locate the file names 'Assets.car'.

Create two duplicates of this file.  Place one on your desktop and the 

# vcvarsallCLshell setup instrustions for VS and VSCODE
# Visual Studio Setup [here][1]
# Visual Studio Code setup [here][2]

 Abbreviations used:
 - dir = directory
 - cd  = change directory
 - .bat = windows batch file
 - VS = Visual Studio

 shell.bat for vcvarsall.bat command line setup, used to build C++ code from command line instead of in Visual Studio but using Microsofts Compiler.
 
 These instructions assume an install of Microsofts Visual Studio (any edition, VS Code does not come with a compiler) prior to setup.
 
 If you have a recent version of Visual Studio, open the Visual Studio Installer from the Windows Start menu and verify that the C++ workload is checked. If it's not installed,  then check the box and click the Modify button in the installer.

 You can also install just the C++ Build Tools, without a full Visual Studio IDE installation. From the Visual Studio Downloads page, scroll down until you see Tools for Visual Studio under the All downloads section and select the download for Build Tools for Visual Studio.
 
 The same principle explored in this instruction can be done with MinGW or other compilers.
 
 If vcvarsall.bat isn't on your machine but you do have VS2019 or other installed open the 'visual studio installer' and make sure the Visual C++ workload is installed.  If it is, uninstall it and reinstall it, this should replace the vcvarsall.bat file.
 
 If vcvarsall.bat isn't on your machine but you have the toolset downloaded remove the set and reinstall it to via the 'visual studio installer' fix the directory.
 
 Steps with ✅ are ***mandatory*** to get this to work.
 
 Steps with ☑️ are **reccomended** but not mandatory.
 
 Items marked with ❓ are _informational_, look at these and make sure the information in these match your machine, if it doesn't please let me know and I will add to this.

 ✅Step 1:  Clone this repository onto your machine anywhere, ```you will need this path later``` so remember it or copy it.
 
  ❓ The included shell.bat files are configured for VS2019 Community, Professional or Enterpise install, the location of your vcvarsall.bat may be different based on what you have installed but the shell.bat corresponding to your install should have the correct path.
  
  ❓ shell_VS2019_CE.bat = Community edition (the free edtion that most people will use)
  
  ❓ shell_VS2019_Pro.bat = Professional edition 
  
  ❓ shell_VS2019_Ent.bat = Enterprise edition

  ❓ Base shell.bat file contents, Community edition file is shown:
```
@echo off

call "\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat" x64
```
 
 ✅Step 2:  Open your Windows directory > System 32 for example: **C:\WINDOWS\system32** and find _cmd.exe_
 
 ✅Step 3:  Right click cmd.exe and create a shortcut to desktop (or anywhere you want, but it HAS to be a shortcut!)
 
 ✅Step 4:  Go to the Shortcut > Right Click > Properties > Shortcut
 
 ✅Step 5:  Change "Target:" to the following and make sure you use the .bat that matched your VS2019 install: 
 
 ```%windir%\system32\cmd.exe /k  "C:\your dir\vcvarsallCLshell\your VS edition bat"```  
 - change 'your dir' to the location of vcvarsallCLshell folder (the location you copied earlier from when you cloned the repository)
 - change 'your VS edition bat' to the corresponding VS2019 edition you have installed.
 - For example my folder name is 'Development' so I replace 'your dir' with 'Development' and my VS2019 edition is Community so I use 'shell_VS2019_CE.bat:
   ```
   "C:\Development\vcvarsallCLshell\shell_VS2019_CE.bat"
   ```
 
 ☑️Step 6:  Change the "Start in:" to the starting location for your code, for me its **C:\Development** this folder on my drive holds all my repositories.  This way I can cd into whatever I am working on directly.  Another option would be to setup multiple cmd.exe shortcuts for each project and house them in the repositories of your choice.
 
 ❓ A successful load of the vcvarsall.bat via the shell, after the steps above are accomplished, will look like this:
```
**********************************************************************
** Visual Studio 2019 Developer Command Prompt v16.9.4
** Copyright (c) 2021 Microsoft Corporation
**********************************************************************
[vcvarsall.bat] Environment initialized for: 'x64'

C:\Development> (this is based on the "Start in:" location in Step 6)
```
 
 ☑️Step 7:  Customise the cmd window how you want
 
 Some options I use:
 
  - Font: Lucida Console with font size 18 (very readable).
  - Colors(r,g,b): **Screen Text**: 193,156,0  **Screen Background**: 12,12,12

👍 You are now all set to start compiling code with CL using vcvarsall.bat! 👍

Examples of use:

1. You have a stand alone file yourfile.cpp that you want to build:
 - in the dir of the file in the cmd window, type ```cl yourfile.cpp``` this compiles the file the same as if you used a .bat file.
 - I recommend you use this if you are compiling once or twice, any more than that make a build.bat file in the dir and call that (shown below).

2. You have multiple files or a single file that you will compile many times:
 - yourprojectname.cpp needs to be compiled but you don't have a compiler attached to your text editor.
 - create a build.bat file located in your code folder where yourprojectname.cpp is at with the following code:
 
``` 
@echo off

mkdir ..\yourprojectname_build
pushd ..\yourprojectname_build
cl \Development\yourprojectname\code\yourprojectname.cpp
popd
```
- In the dir of the file(s) in the cmd window, type "build" to run the batch file you just made:
- This will create a folder named yourprojectname_build one folder outside of your "code" folder and place the built files in it **yourprojectname.exe** and so on.


[1]: http://
[2]: http://

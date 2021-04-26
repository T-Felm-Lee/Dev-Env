# vcvarsallCLshell setup instrustions

 shell.bat for vcvarsall.bat command line setup, used to build C++ code from command line instead of in Visual Studio but using Microsofts Compiler.
 
 These instructions assume an install of Microsofts Visual Studio (any edition) or Microsoft SDK prior to setup.
 
 If vcvarsall.bat isn't on your machine but you do have VS2019 or other installed open the 'visual studio installer' and make sure the Visual C++ workload is installed.  If it is, uninstall it and reinstall it, this should replace the vcvarsall.bat file.
 
 Abbreviations used:
 - dir = directory
 - cd  = change directory
 
 Steps with ✅ are ***mandatory*** to get this to work.
 
 Steps with ☑️ are **reccomended** but not mandatory.
 
 Items marked with ❓ are _informational_, look at these and make sure the information in these match your machine, if it doesn't please let me know and I will add to this.

 ✅Step 1:  Clone this repository onto your machine anywhere, ```you will need this path later``` so remember it or copy it.
 
  ❓ The included shell.bat file is configured for a normal VS2019 Community install, the location of your vcvarsall.bat may be different based on what you have installed.  
 
  ❓ A quick search on your harddrive "vcvarsall" should find the file if it is installed.  
 - When you do find it you can edit the shell.bat (using any text editor) to match the dir of your vcvarsall.bat file.  Please let me know if this happens and what the path of the vcvarsall was so I can make more shell.bat files to match different machines or installs of VS/SDK.

  ❓ Base shell.bat file contents, the path will need to be changed to be where your vcvarsall.bat file is located if you have a different install of VS or you only installed the Microsoft SDK for C++
```
@echo off

call "\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat" x64
```
 
 ✅Step 2:  Open your Windows directory > System 32 for example: **C:\WINDOWS\system32** and find _cmd.exe_
 
 ✅Step 3:  Right click cmd.exe and create a shortcut to desktop (or anywhere you want, but it HAS to be a shortcut!)
 
 ✅Step 4:  Go to the shortcut > right click > Properties
 
 ✅Step 5:  Change "Target:" to: ```%windir%\system32\cmd.exe /k  "C:\yourdir\vcvarsallCLshell\shell.bat"```  change 'yourdir' to the location of vcvarsallCLshell folder (the location you copied earlier from when you cloned the repository)
 - For example my folder name is 'Development'so I replace 'yourdir' with 'Development':
   ```
   "C:\Development\vcvarsallCLshell\shell.bat"
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

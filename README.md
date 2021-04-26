# vcvarsallCLshell setup instrustions

 shell.bat for vcvarsall.bat command line setup, used to build C++ code from command line instead of in Visual Studio but using Microsofts Compiler.
 
 Steps with ✅ are ***mandatory*** to get this to work.
 
 Steps with ☑️ are **reccomended** but not mandatory.
 
 Items marked with ❓ are _informational_, look at these and make sure the information in these match your machine, if it doesn't please let me know and I will add to this.
 
 ❓ The included shell.bat file is configured for a normal VS2019 Community install, the location of your vcvarsall.bat may be different based on what you have installed.  
 
 ❓ A quick search on your harddrive "vcvarsall" should find the file if it is installed.  
 - When you do find it you can change the shell.bat to match the dir of your vcvarsall.bat file.  Please let me know if this happens and what the path of the vcvarsall was so I can make more shell.bat files to match different machines or installs of VS/SDK.

❓ Base shell.bat file contents
```
@echo off

call "\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat" x64
```
❓ A successful load of the vcvarsall.bat via the shell after the steps below are accomplished will look like this:
```
**********************************************************************
** Visual Studio 2019 Developer Command Prompt v16.9.4
** Copyright (c) 2021 Microsoft Corporation
**********************************************************************
[vcvarsall.bat] Environment initialized for: 'x64'
```

 ✅Step 1:  Clone Repository onto your machine anywhere, ```you will need this path later``` so remember it or copy it.
 
 ✅Step 2:  Open your Windows directory > System 32 for example: **C:\WINDOWS\system32** and find _cmd.exe_
 
 ✅Step 3:  Right click cmd.exe and create a shortcut to desktop (or anywhere you want, but it HAS to be a shortcut!)
 
 ✅Step 4:  Go to the shortcut > right click > Properties
 
 ✅Step 5:  Change "Target:" to: ```%windir%\system32\cmd.exe /k  "C:\yourdir\vcvarsallCLshell\shell.bat"```
 
 ☑️Step 6:  Change the "Start in:" to the starting location for your code, for me its **C:\Development** this folder on my drive holds all my repositories.  This way I can cd into whatever I am working on directly.  Another option would be to setup multiple cmd.exe shortcuts for each project and house them in the repositories of your choice.
 
 ☑️Step 7:  Customise the cmd window how you want
 
 Some options I use:
 
  - Font: Lucida Console with font size 18 (very readable).
  - Colors(r,g,b): **Screen Text**: 193,156,0  **Screen Background**: 12,12,12

You are now all set to start compiling code with CL using vcvarsall.bat!

Examples of use:

1. You are using Notepad++ and need to compile:
 - yourprojectname.cpp need to be compiled but you don't have a compiler attached to NP++
 - create a build.bat file located in your code folder where yourprojectname.cpp is at with the following code:
 
``` 
@echo off

mkdir ..\yourprojectname_build
pushd ..\yourprojectname_build
cl \Development\yourprojectname\code\yourprojectname.cpp
popd
```

This will create a folder named yourprojectname_build one folder outside of your "code" folder and place the built files in it **win32_yourprojectname.exe** and so on.

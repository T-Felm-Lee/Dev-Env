# vcvarsallCLshell setup instrustions

 shell.bat for vcvarsall.bat command line setup, used to build C++ code from command line instead of in Visual Studio but using Microsofts Compiler.
 
 Steps with ✅ are **mandatory** to get this to work.
 
 Steps with ☑️ are *reccomended* but not mandatory.
 
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

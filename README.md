# vcvarsallCLshell setup instrustions for VS and VSCODE
# Visual Studio setup [here][1]
# Visual Studio Code setup [here][2]


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


[1]: https://github.com/T-Felm-Lee/vcvarsallCLshell/wiki/Visual-Studio-Instructions
[2]: https://github.com/T-Felm-Lee/vcvarsallCLshell/wiki/Visual-Studio-Code-Instructions

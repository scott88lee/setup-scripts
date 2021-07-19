
## Installing the Windows Subsystem for Linux (WSL)

[https://docs.microsoft.com/en-us/windows/wsl/install-win10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

-   Press the Windows key and search for  `Windows features`  and select  `Turn Windows features on and off`.
-   Scroll down and find  `Windows Subsystem for Linux`  and make sure it's checked, then press OK. Restart the system when prompted to.
-   Next, go to the Windows store and search for  `Ubuntu`  and install it.
-   Launch Ubuntu from the start menu. Enter your Linux username and password, and make a note of it (they are needed later). Under no circumstances should you leave these blank or cancel the process, as this will run your Linux installation as a root user which causes permission warnings later on and also poses a significant security risk to your system.
    -   _Do not forget your Linux password. It is needed for admin operations in the WSL environment._
-   _Note: Right-clicking on the WSL window pastes whatever is in your clipboard. This can save you some time when running the longer commands here._

## Symlinking a Windows workspace folder into your WSL home

-   **Warning**: Your WSL files are stored in a separate file system managed by WSL with a different, stricter and more fine-grained permission system than Windows. You should  _never_  edit any WSL files from Windows itself, as there is a non-trivial risk of corrupting your entire WSL installation. However, editing Windows files from WSL is perfectly fine. Thus, we can integrate the two systems (WSL and Windows) by making sure that your working folders live in Windows and are conveniently accessible from WSL.
    
-   Create a  `projects`  folder from your Windows user account home directory. For example, go to  `C:\Users`  in Explorer and go into the folder corresponding to your user name. Create a folder named  `projects`  here. For example, if your home directory is  `C:\Users\Scott`, create the directory  `C:\Users\Scott\projects`. All projects should be created in this folder so that you can safely browse or edit the files from both WSL and Windows.
    
-   Next, symlink it by opening a WSL window and running the following commands in order
    
    -   `cd ~`
    -   `ln -s /mnt/c/Users/scott/Desktop/Dev ./Dev`
-   From now on, you will be able to access the projects folder in your WSL installation as if it were a directory in it.
    
-   Install your text editor of choice in Windows, e.g. Sublime Text ([https://www.sublimetext.com/3](https://www.sublimetext.com/3)) or VSCode ([https://code.visualstudio.com/download](https://code.visualstudio.com/download)).
    
-   Create an alias for your text editor in WSL so that you can launch it from the WSL's CLI. For Sublime Text, if you had installed it at the default location, run  `echo 'alias subl="/mnt/c/Program\ Files/Sublime\ Text\ 3/subl.exe"' >> ~/.bashrc`  at your WSL's CLI. Then, close and re-open WSL, or run  `source ~/.bashrc`  to reload the configuration, and test it out by typeing  `subl`  and pressing enter in WSL.

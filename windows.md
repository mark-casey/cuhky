# windows

Win7/8/8.1 (and 10?)

### On Windows usernames

Windows users should be created without spaces in the name so that the user's profile directory (%USERPROFILE%) does not have spaces in the path, which from time to time will cause annoying but not insurmountable issues in "Linuxy" and "POSIXy" software that has been added to Windows.

Renaming the Windows user to a proper Firstname Lastname after the fact is easy, but renaming the user's profile directory is hard (requires registry edits at the same time as the directory rename and must be done from another admin account when the user is logged off).

All examples in this doc assume the user created for the ficticious "John Dev" was originally johndev (and to a lesser extent, this doc will attempt to represent that the username was then changed to "John Dev").

### Setup

1. Clean up Windows profile directory (%USERPROFILE%) as much as possible, but be very careful. Try to use modified times on files (but probably not trusting those on folders) to tell how outdated stuff is. At the very least make a folder on your Desktop and move things from %USERPROFILE% there instead of outright deleting.
2. Use the registry to move some of Windows' more useless profile folders (perhaps Contacts, Videos, etc.) to another location.
1. Set a Windows env variable for your user to tell babun's installer to set shell's (i.e.: bash/zsh) home directory to your Windows profile directory instead of "%userprofile%\.babun\cygwin\home\username"
  - Right click on Computer on the Desktop or in Start Menu and choose Properties
  - Choose Advanced system settings
  - At the top choose the Advanced tab
  - Click Environment Variables
  - User "Variables for $youruser"
    - Click New
    - Variable name: 'HOME'
    - Variable value: '%USERPROFILE%'
  - OK/Close all the way out
1. Install chocolatey package manager for Windows
  - Visit https://chocolatey.org/
  - It will give instructions to open an Administrative cmd prompt (find cmd, right click, Run as Administrator) and paste a download/install command into the terminal to run
2. Exit and then reopen the Administratrive cmd prompt once chocolatey's installer finishes.
3. Run these in the terminal:  
  ```
  choco install -y cmdermini babun
  ```  
  *babun will prompt about having HOME set; tell it yes  
4. Add babun to cmder
  - Open cmder
  - Open cmder Settings dialog and in the left pane browse to Startup -> Tasks
  - Click the '+' icon to create a new task
    - Rename the added task: 'babun_and_cmder'
    - Use the 'Up' button to move the new task to the top of the list
    - Set the task's Task Parameters to:  
    ```
    /icon "%userprofile%\.babun\cygwin\bin\mintty.exe" /dir "%userprofile%"
    ```
    - Set the command(s) to:  
    ```
    >%userprofile%\.babun\cygwin\bin\mintty.exe -
    
    cmd /k "%ConEmuDir%\..\init.bat"  -new_console:d:%USERPROFILE%
    ```
  - (Still inside cmder's Settings dialog) choose Startup in the left pane
    - Set Specified named task to: {babun_and_cmder}
  - (Still inside cmder's Settings dialog) choose Main -> Appearance in the left pane
    - Maximize cmder
    - Enable Quake style menu
  - (Still inside cmder's Settings dialog) choose Main -> Size & Pos in the left pane
  - (Still inside cmder's Settings dialog) choose Keys & Macro
    - Set 'Switch focus between ConEmu and child GUI application' to: Win+Z
    - Set 'Switch next console': Win+Q
    - Set 'Switch previous console': Win+Shift+Q
  - (Still inside cmder's Settings dialog) choose Keys & Macro -> Controls
    - Enable Install keyboard hooks
  - Click Save settings in the bottom right



## Removal

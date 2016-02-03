# windows

Win7/8/8.1 (and 10?)

### Components
  - POSIX shell: bash or zsh in babun, wrapped by cmder
  - rsync: babun-supplied
  - etc.

### On Windows usernames

Windows users should be created without spaces in the name so that the user's profile directory does not have spaces in the path, which from time to time will cause annoying but not insurmountable issues in software like Cygwin (https://cygwin.com/faq.html#faq.setup.name-with-space).

Renaming the Windows username to a proper Firstname Lastname after the fact is easy and will not affect the path to the originally-created profile directory, while renaming the user's profile directory is hard (requires registry edits at the same time as the directory rename and must be done from another admin account when the user is logged off).

All examples in this doc assume the user created for the ficticious "John Dev" was originally "johndev" (and to a lesser extent, this doc will attempt to represent that the username was then changed to "John Dev").

### Decisions

You should decide whether you want your POSIX shell's home directory ('~') to be the same as your Windows user's profile directory (located at the value of the environment variable %USERPROFILE%). This can be convenient since all of your .dotfiles will be in the same location. Alternatively you can use babun's default profile path of '%USERPROFILE%\.babun\cygwin\home\johndev'. This separation of concerns may improve compatibility or spare you from running into a few extra bugs but will also cause some duplicate .dotfiles for applications that are used both inside and outside of the POSIX shell (the .vagrant directory, perhaps)
  - Assuming you aren't reinstalling Windows completely, if you decide to use a shared home/profile directory it may be desirable to clean up your Windows profile directory so that there is less cruft when running 'ls' in your home directory. You can try to use modified times on files (*keeping in mind directories with old modified times can still have recently changed files!*) to tell how outdated stuff is. Do not delete any special profile directories such as Contacts, Videos, Links, or etc., as they can be moved in the next step. It may be useful to create a folder on your Desktop to move old/undesirable profile directories to in case something breaks and you need to put something back. Some mystery files may be identifiable in context by searching your hard drive for other files that were created or updated at the same time.
  - For some of Windows' more useless profile folders (perhaps Contacts, Videos, etc.) you can move them to another location. In older versions of Windows this was much harder and often required registry edits. In the versions of Windows cuhky addresses you can simply create a new directory in your user profile called (something like) 'winprofiledirs' and then move the desired special profile directories into this new directory. Windows detects a special folder is moving and updates internal settings (you can confirm this by looking at the Location tab of the Properties window of such a folder after it has been moved - it will show the new path and offer options to restore the default path). When viewed in Explorer the special directory will still show in the user profile but should no longer appear in a directory listing done from your POSIX shell.
    - **Some corporate environments may have already redirected these folders to another location, to a roaming profile, or may be preventing this option via Group Policy (assuming such a contol exists).**
    - **Some (really) poorly written software may hardcode these paths so only move directories that will not cause major harm if something cannot find them (i.e.: move Videos and Contacts, maybe Links and Favorites, but probably not Documents)**

### Setup

1. **If you want a shared home/profile directory** set a Windows env variable for your user to tell babun's installer to set shell's (i.e.: bash/zsh) home directory to your Windows profile directory instead of "%userprofile%\.babun\cygwin\home\username"
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
  - It will give instructions to open an Administrative cmd prompt (find cmd, right click, Run as administrator) and paste a download/install command into the terminal to run
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
    - Enable Quake style menu
    - Enable Auto-hide on focus lose
  - (Still inside cmder's Settings dialog) choose Main -> Size & Pos in the left pane
    - Enable Show & store current window size and position
    - Enable Auto save window size and position on exit
    - Set Window size to Normal, Width to 100%, and Height to 85%
  - (Still inside cmder's Settings dialog) choose Keys & Macro
    - Set 'Switch focus between ConEmu and child GUI application' to: Win+Z
    - Set 'Switch next console': Win+Q
    - Set 'Switch previous console': Win+Shift+Q
  - (Still inside cmder's Settings dialog) choose Keys & Macro -> Controls
    - Enable Install keyboard hooks
  - Click Save settings in the bottom right



## Removal

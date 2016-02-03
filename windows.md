# windows

## Setup

Win7/8/8.1 (and 10?)

1. Set an env variable for babun to set home directory to Windows profile dir
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
    - Rename the added task: 'babun'
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
    - Set Specified named task to: {babun}
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

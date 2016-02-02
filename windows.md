# windows

## Setup

Win7/8/8.1 (and 10?)

1. Install chocolatey package manager for Windows
  - Visit https://chocolatey.org/
  - It will give instructions to open an Administrative cmd prompt (find cmd, right click, Run as Administrator) and paste a download/install command into the terminal to run
2. Exit and then reopen the Administratrive cmd prompt once chocolatey's installer finishes.
3. Run these in the terminal:  
  ```
  choco install -y cmdermini babun
  ```
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
    %userprofile%\.babun\cygwin\bin\mintty.exe /bin/env CHERE_INVOKING=1 /bin/zsh.exe
    ```
  - (Still inside cmder's Settings dialog) choose Startup in the left pane
    - Set Specified named task to: {babun}
  - (Still inside cmder's Settings dialog) choose Main -> Appearance in the left pane
    - Maximize cmder
    - Enable Quake style menu
  - (Still inside cmder's Settings dialog) choose Main -> Size & Pos in the left pane
    - Enable Show & store current window size and position
    - Enable Auto save window size and position on exit
    - Set Window size to Normal, Width to 100%, and Height to 85%
  - Click Save settings in the bottom right



## Removal

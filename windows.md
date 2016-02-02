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
  - Open cmder settings dialog and go to Startup -> Tasks
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

## Removal

# cuhky
(cookie cutter setup of physical dev machines)

A spec and set of scripts for normalizing capabilities of web development physical workstations across operating systems.

---------------------------------------

Much work is done on allowing developers to evaluate or work on multiple projects at any given time using virtual machines and/or containers, using tools such as Vagrant, Docker, VMware Workstation, automation software, and etc.

Less work has been done to automate and simplify the physical workstations these tools run on, and less-still to make workstation features more consistient across host operating systems.

Workstations built completely under cuhky:
  * (If deciding to reinstall) Virtualize the user's previous host OS to ease transitioning
  * Encourage the ability to reinstall the host OS without fear by:
    * Moving user data off of host-OS system partitions to facilitate reinstalling the physical OS
      (NOTE_HERE: That Windows can do this but you have to do it at install time for it to really work well)
    * Utilizing portable applications where possible
  * Include the following tools with recommended configurations:
    * POSIX shells such as Bash
    * Version Control System software such as git
    * Vagrant and VirtualBox, with the ability to use the same Shared Folder types on all OSes
    * rsync - to facilitate the rsync Shared Folder type in Vagrant
    * SSH daemon (maybe not a good idea on Windows[?])
    * A packaging system such as apt-get or yum on Linux, homebrew on OSX, and chocolatey on Windows
    * A default cross platform IDE or two that can use more than one VCS system (perhaps Eclipse and Atom and something for Go?)





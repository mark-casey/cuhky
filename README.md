# cuhky
(cookie cutter setup of physical dev machines)

A spec and set of scripts for normalizing capabilities of web development physical workstations across operating systems.

---------------------------------------

Much work is done on allowing developers to evaluate or work on multiple projects at any given time using virtual machines and/or containers, using tools such as Vagrant, Docker, VMware Workstation, automation software, and etc.

Less work has been done to automate and simplify the physical workstations these tools run on, and less-still to make workstation features more consistient across host operating systems.

Workstations built completely under cuhky:
  * Virtualize the user's previous host OS to ease transitioning
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

Usernames no spaces

miscellanenous:
  * (this is a horribly rough example about the types of places we can get into trouble and some ideas on mitigating them)
    * Mixing non-stock technologies (such as adding a POSIX layer on Windows) breeds complexity. It is useful to watch for convenient barriers or mediators, such as (continuing with the POSIX/Windows example) the host OS filesystem. The dev's IDE running natively on the host OS may internally use a git library for Windows and ***FIXME "POSIX git" may run inside POSIX shells via Cygwin, Babun, or etc., but if the IDE has a console feature you may not want to run the POSIX shell through its emulation inside a native app that is using git natively while the git running in the emulated shell that is running in the native IDE is using it in a POSIX way.    ...it's not that hard to alt-tab to type shell commands.

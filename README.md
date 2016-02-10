# cuhky
(cookie-cutter setup of physical dev machines)

A documentation project and sets of resources for normalizing capabilities of web development physical workstations across operating systems.

---------------------------------------

Large amounts of work have been and continue to be done on allowing developers to evaluate or work on multiple projects at any given time using virtual machines and/or containers using tools such as Vagrant, Docker, VMware Workstation, automation software, and etc.

Less work has been done to automate, simplify, and document the physical workstations these tools run on, and still less has been done to make workstation features more consistient across host operating systems.

Workstations built with cuhky:
  * Include the following tools with recommended configurations (and where possible, explanations of said config's merits):
    * POSIX (or POSIX-like) shell such as Bash/zsh
    * Version Control System software such as git
    * An SSH key agent
    * Documented pattern(s) for linking VCS to the SSH agent (IDE-independent where possible/reasonable!)
    * Vagrant and VirtualBox, with the ability to use the same Shared Folder types on all OSes
      * rsync - to facilitate the rsync Shared Folder type in Vagrant
      * Documented patterns (and possibly tooling/scripts) for using SMB shares for shared folders
    * An SSH key agent
    * A packaging system such as apt-get or yum on Linux, homebrew on OSX, and chocolatey on Windows

Other items for the above list - maybe someday:
  * (If deciding to reinstall) Include considerations to virtualize the user's previous host OS to ease transitioning
  * Encourage the ability to reinstall the host OS without fear by:
    * Moving user data off of host-OS system partitions to facilitate reinstalling the physical OS
      (Windows can do this too but you have to do it at install time for it to really work well)
    * Utilizing portable applications where possible




# SCRIPT TO TURN OFF SECONDARY HDD ON LINUX

A shell script (more of a direct command than a script) to turn off secondary hard disk drive on linux.
This should work on any linux distro that supports 'udisksctl' command. However, if in any case it does not, then all you would need to do is replace it with some other command

## Backstory:

I swapped out the original HDD (Hard Disk Drive) on my laptop and installed a new SSD (Solid State Drive) in its place. Then, I installed the HDD to the CD drive slot with the help of a caddy.I noticed that my HDD was always running, even though I booted up from the SDD. That was annoying.

So, I searched for a fix online. I stumbled upon a terminal command that could turn off (rather put to sleep) any storage device.Since I did not want to waste a lot of time on something so (seemingly) trivial. I decided to use that command each time I booted my laptop but....
  - Boot up
  - Launch the terminal
  - Hear the annoying sound of the HDD spinning
  - Recall what the command to turn it off was
  - Type the command  I did not want to waste a lot of time on something seemingly trivial.
  - Press Enter
Argh! This got really tiring really soon. Hence the following solution.

## Requirements:

1. udisks is a command line tool to query and manipulate storage devices and should be available by default on most linux distros. 
2. Install udisks with the following command:
    `sudo apt-get update -y`
    `sudo apt-get install -y udisks`

## Usage:

1. Save the hddoff file in the /bin directory
2. Give it executable permission through the terminal using:
    `sudo chmod 755 hddoff`
3. Now open the sudoers file to make the file execute without having to need sudo every time you use it:
    `sudo visudo /etc/sudoers`
4. Add the following lines at the end of the sudoers file (Yes! The comment line too.Trust me, it will serve as a reference later.):
    ```
    #the following commands can be run as sudo without giving password
    user_name ALL=(root) NOPASSWD: /bin/hddoff
    ```
5. Save and exit. Now open the respective Shortcut Keys Application on your distro. Add a new shortcut and pass the following command to your preferred shortcut:
    `sudo hddoff'
    Here's what I did. I just replaced the existing keys' associated commands with appropriate command from above

Note: This script should run on any debian based linux machine. Though I'm sure there are other command line tools to achieve the same.
The command can be used directly from the terminal too as `sudo hddoff`.It works the same way.

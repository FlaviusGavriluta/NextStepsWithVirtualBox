# Next Steps with VirtualBox

## Story

While doing your boss' chores to deal with virtual machines and images and whatnot you bumped into a serious problem: accessing files available on your host OS from inside a guest VM's OS turned out to be a tricky thing to do. Not mentioning that wrapping your head around what a "host" and a "guest" is and how they collaborate is tricky to start with.

In order to tackle this you asked the IT department's chief _know-it-all_ to help you out. She came up with an exercise to help you ...

## What are you going to learn?

- Understand what hypervisor are (type-1 and type-2)
- Know examples of hypervisors: Hyper-V, VMWare, Parallels, VirtualBox
- What kind of virtualized hardware are available generally in hypervisors
- Understand what shared folders are
- Add shared folders to VM
- How to access files on the host from the guest and vice versa via: VirtualBox File Manager
- How to access files on the host from the guest and vice versa via: shared folders
- Understand VirtualBox guest additions: shared clipboard, etc.
- Use host key to switch between guest and host control
- How to pause/resume a virtual machine's execution
- Start to terminal in the Ubuntu OS (preferably with a shortcut)
- How to stop the current, running process in the terminal (Ctrl-C)
- How to examine who is the owner of a directory/file with ls
- How to deal with and understand what is a "Permission denied" error in simple cases
- Execute basic, simple commands in the terminal
- Why `sudo` needs to be used in front of some commands
- How to become `root` for the duration of a simple command

## Tasks

1. Start a VM from a ready-made image.
    - This [virtual machine image](https://github.com/CodecoolBase/short-admin-vms/releases/latest/download/ubuntu-18.04-base.ova) is downloaded onto the host machine
    - The virtual machine is started (using a snapshot if available), it's booted, a user is logged in and the desktop is visible

2. Play with the pause/resume capabilities of virtual machines.
    - The terminal is started via a shortcut in the guest OS
    - The following script/command is entered into the terminal on the guest (no copy-paste, sorry bro'!), where it is executed and left running for a few seconds ``` i=0; while true; do echo $i; i=$((i + 1)); sleep 1; done ```
    - The guest machine is paused, you've taken a break of at least 5 minutes and grabbed a tea or coffee
    - The virtual is machine resumed, execution of the script continued exactly where it was left off

3. Setup a shared folder between host and guest for easier sharing of files.
    - A folder on your host machines desktop is created with the name "guest"
    - A `.txt` file is created with a simple text editor inside the "guest" directory on the host
    - The file is named like `LastnameFirstname.txt`. `Lastname` and `Firstname` is replaced with your own name without accented letters, using only US ASCII character and no spaces)
    - The file's content should be `Hello World` with a Unix newline (empty line) character (`LF`) at the very bottom of the text

```txt
Hello World
```

*Note*: the `LF` character is an invisible control character [(maybe you've seen such things in Word before)](https://web.archive.org/web/20210314185036im_/https://www.howtogeek.com/wp-content/uploads/2015/04/00_lead_image_formatting_marks_showing.png), no need to write it out :)
    - The file's encoding should be `UTF-8`
    - An auto-mounted, transient shared folder is added to the virtual machine. The directory created earlier is specified as the host path, the guest path or mount point is `/home/ubuntu/host`
    - Ubuntu user is added added to the `vboxsf` group (the change takes effect after logout/login)
    - The contents of the file are displayed on the terminal in the guest using the `cat` command

4. Take a screenshots of the things visible on the guest OS's desktop
    - One or more screenshot is created and saved on the host machine. On the image, a portion of the host machine's desktop and guest machine's view should be visible
    - Screenhots are uploaded to the GitHub repository

## General requirements

None

## Hints

- Without VirtualBox Guest Additions features like shared clipboard, shared folders, etc. wouldn't work, if you plan to create a VM and install the OS into it yourself take this into consideration
- When trying to copy-paste a piece of text from the host into the guest doesn't seem to be working don't type the command, but instead, look into how to enable the bi-directional shared clipboard between the host and the guest
- When accessing files in an auto-mounted shared folder inside a Linux guest OS you'll probably deal with file permissions problems, such as _Permission denied_, this is normal. Verify who is the owner of the file/directory you want to access using `ls` and use `sudo` to overcome the permission problem
- Use the `usermod` command with the -G and -a flag to append the ubuntu user to a group
- **When you are reading background materials:**
  - [Different type of hypervisors](https://en.wikipedia.org/wiki/Hypervisor#Classification) - Focus only on _Classification_, the goal is to get familiar with the name and the type of a few hypervisors available in the market for future reference
  - [VirtualBox Guest Additions](https://www.virtualbox.org/manual/ch04.html#guestadd-intro) - Focus on the summaries of the features provided VirtualBox Guest Additions (shared folders, shared clipboard and mouse pointer integration in particular)
  - [Emulated hardware in VirtualBox](https://www.virtualbox.org/manual/ch03.html#emul-hardware) - Focus only on the list of available types of hardware/devices available for emulation. For best understanding, stop your VM and change the RAM or CPU settings, take a peek at networking and storage settings.
  - [Stopping the current process in Bash](https://www.howtogeek.com/howto/ubuntu/keyboard-shortcuts-for-bash-command-shell-for-ubuntu-debian-suse-redhat-linux-etc/) - Focus on the Working With Processes section
  - [Linux Commands For Beginners: SUDO](https://linuxacademy.com/blog/linux/linux-commands-for-beginners-sudo/) - Focus only on how to use the `sudo` command together with other commands, like `cat`

## Background materials

- <i class="far fa-exclamation"></i> [Virtualization explained](https://www.youtube.com/watch?v=FZR0rG3HKIk)
- <i class="far fa-exclamation"></i> [What is virtualization?](https://opensource.com/resources/virtualization)
- <i class="far fa-exclamation"></i> [Different type of hypervisors](https://en.wikipedia.org/wiki/Hypervisor#Classification)
- [VirtualBox Guest Additions](https://www.virtualbox.org/manual/ch04.html#guestadd-intro)
- [Emulated hardware in VirtualBox](https://www.virtualbox.org/manual/ch03.html#emul-hardware)
- <i class="far fa-exclamation"></i> [Stopping the current process in Bash](https://www.howtogeek.com/howto/ubuntu/keyboard-shortcuts-for-bash-command-shell-for-ubuntu-debian-suse-redhat-linux-etc/)
- [Enable Shared Clipboard in VirtualBox 6](https://www.youtube.com/watch?v=fqrJ7qlhJu0)
- [Linux Commands For Beginners: SUDO](https://linuxacademy.com/blog/linux/linux-commands-for-beginners-sudo/)

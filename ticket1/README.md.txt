Ticket 1 — The Build Document

1. What Was Asked

The task was to document how the virtual machine environment was prepared in VMware Workstation. I needed to describe the configuration steps, check the network settings, test the connection between the virtual machines, and provide evidence of the work.

2. What Was Actually Needed

To complete the task, I needed to check the existing Windows and Linux virtual machines, make sure their network adapters were configured, run a system information command in Linux, and perform a ping test. I also needed to create a snapshot and save screenshots and text files as evidence.

3. What I Did

I used VMware Workstation and worked with my existing Windows and Linux virtual machines.

First, I opened the virtual machine creation wizard and checked the disk settings. I also checked the network adapter settings for both virtual machines and confirmed that NAT was selected.

Next, I opened the Linux terminal and ran uname -a to display information about the operating system. I saved the output in a text file.

After that, I used the Windows Command Prompt to check the network configuration and run a ping test to the Linux virtual machine. I saved the command output so that the result could be reviewed later.

Finally, I created a snapshot named Initial-Configuration and captured a screenshot of the snapshot list.

4. Evidence

The following files were prepared as evidence for the task:

* 01-new-vm-wizard.png — screenshot of the virtual machine creation wizard.
* 02-disk-settings.png — screenshot of the virtual disk settings.
* 03-network-adapter.png — screenshot of the network adapter configuration.
* 04-guest-uname.txt — Linux system information obtained with uname -a.
* 05-ping-between-guests.txt — output of the ping test between the virtual machines.
* 06-snapshot-list.png — screenshot showing the snapshot list.

These files document the configuration and testing steps completed for the assignment.

5. What I Would Do Differently

If I did this task again, I would organize the evidence files from the beginning and save them directly in the correct folder. I would also check the network connection earlier to identify any problems before documenting the final configuration. This would make the process easier to follow and the final submission more organized.
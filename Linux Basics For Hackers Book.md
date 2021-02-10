# Linux Basics For Hackers Book

## Basic Commands  

| Command | Action |
| ----------- | ----------- |
|cd| change directory|
|pwd| print current directory|
|whoami| which user login|
|ls| list files of current directory|
|man *app_name*| show manual page|
|locate| finding stuff in hole file system|
|whereis| finding stuff in bin|
|which| return location depend on path variable|
|grep| filter output used with piping ( \| )|
|cat *text_file_name* |read text file|
|cat > *text_file_name* |create text file|
|cat >> *text_file_name* |continue typing in text file|
|touch *text_file_name* |anther way to create text file| 
|mkdir *dir_name* |create a new directory|
|cp *old_file* *dir_of_new_file* |copy file|
|mv *old_file* *dir_of_new_file* |move file|
|rm *file_name* |delete file|
|rmdir *dir_name* |remove directory must be empty|
|rmdir -r *dir_name* |remove directory any way|
---

## Text Manipulation

| Command | Action |
| ----------- | ---------- |
|cat *file_name* |view file|
|head *file_name* |view the first 10 lines of file|
|head *- no_of_lines* *file_name* |view the first *no_of_lines* lines of file|
|tail *file_name* |view the last 10 lines of file|
|tail *- no_of_lines* *file_name* |view the last *no_of_lines* lines of file|
|nl *file_name* |view file with number of lines|
|nl *file_name* |view file with number of lines|
|sed | *identifier (s) search*/*old_word* / *new_word* / *identifier (g) global* search for text inside file and replace it with new text| 
---

## Analyzing And Managing Networks  

| Command | Action |
| ----------- | ---------- |
| ifconfig |info about active network interfaces |
| iwconfig |info about wireless interfaces |
| ifconfig *interface_name* *IP* |change current ip|
| ifconfig netmask *net_mask* |change current net_mask|
| ifconfig broadcast *broadcast* |change current broadcast|
| **Changing MAC address** :|
|- ifconfig *interface_name* down|stop interface|
|- ifconfig *interface_name* hw ether *MAC_Address*|set new MAC address|
|- ifconfig *interface_name* up|run interface with new MAC|
|dhclient *interface_name*| assign new ip from dhcp server|
|dig *site_name*|display stored DNS information|
|/etc/resolv.conf|DNS server IP file|
|/etc/hosts|hosts IP file|

## Dealing with Files
### Finding Stuff In Linux
| command | Description |
| ----------- | ----------- |
| locate | find all |
| whereis | find binaries |
| which | it only returns the location of the binaries the PATH variable |
| find | specific search |

    find /[directory] -type [type] -name [name]

### Filter With Grep
    ps aux | grep apache2


## NETWORKS 

### Wireless Network Devices
    $ iwconfig
### Change Ip
    $ ifconfig [interface] [new_ip]
### Changing Your Network Mask And Broadcast Address
    $ if config [interface] [new_ip] netmask [new_netmask] broadcast [new_broadcast]
### Change Mac
    $ ifconfig [interface] down
    $ ifconfig [interface] hw ether [new_MAC]
    $ ifconfig [interface] up
### New Ip Addresses From The Dhcp Server
    $ dhclient [interface]



## Process
### Process By Current User
    $ ps

### All Process By All User
    $ ps aux

### Filter Process By Name
    $ ps aux | grep [process_name]

### Find The Greatest Process 
    $ top

### Change Process Priority With Nice
  DESCRIPTION :
  Run  COMMAND  with  an adjusted niceness,
  which affects process scheduling.  With no
  COMMAND, print the current niceness.  
  Niceness values range from -20 (most favorable
  to the process) to 19 (least favorable to the process).

  ### Set Priority
      $ nice -n [priority_No] [process_name]

  ### Change Priority
      $ renice [priority_No] [PID]

### Killing Process
    $ kill [-No] [PID]
| -No | Description |
| ----------- | ----------- |
| 1 | hangup stop current process and restart it with same PID |
| -2 | weak kill signal maybe work for most case |
| -3 | core dump terminate the process and save info of in memory  |
| -15 | default kill signal |
| -9 | absolute kill signal force process to stop |

### Run In Background
    $ [ps name] &

### Move To Foreground
    $ fg [PID]

### Scheduling Process
    $ at [time]
    at > [ps]

## ENV Vars

https://opensource.com/article/19/8/what-are-environment-variables

Environment variables contain information about 
your login session, stored for the system shell
to use when executing commands.
They exist whether you’re using Linux,
Mac, or Windows. Many of these variables
are set by default during installation
or user creation.

### Show Env Vars
    $ env

### Add Temporary Environment Variables
    $ export PATH=$PATH:/home/seth/bin

### Permanent Environment Variables
You can set your own persistent environment variables in your shell configuration file ~/.bashrc  
    
    $ export PATH=$PATH:/snap/bin:/home/seth/bin

The PATH variable is an environment variable
that contains an ordered list of paths
that Unix will search for executables
when running a command.
  
    $ echo $PATH

## Bash Scripting

***What is a shell?***  
The shell, commonly referred to as the command prompt is an integral part of every Linux distribution. It is one of the most crucial media through which a user can interact with the operating system.

***Shell*** is both a ***command-line interface and a scripting language*** that is used by Linux based operating systems to control and modify system execution in the form of shell scripts.

***/bin/sh:***  
sh (shell command Language)is a programming language as described by POSIX standards. There are various implementations of sh like Bourne shell (sh), dash, Korn Shell (K shell), Z shell, ash, and so on.  

shell is a specification, it is not an implementation. A Specification is a detailed description of the syntax and semantics of the language whereas implementation is an actual language with an interpreter. On many systems, /bin/sh is linked to an implementation that is specific to the Linux distribution on the system.  

***/bin/bash:***  
Bash, short for ***Bourne Again Shell***, is a sh-compatible implementation that is written for the GNU project, as a replacement for the Bourne Shell. It can be considered as a superset for the Bourne Shell. Bash includes ideas drawn from Korn Shell and C Shell.  

bash can be used both for scripting and as an interactive terminal or interpreter. You can relate to this similar to how python3 is a scripting language and how it is an interpreter (when you type in python3 in the terminal, you can see an interactive interpreter. Bash in interactive mode is the terminal or the command prompt. In Ubuntu the default scripting shell is dash and the default for the interactive terminal/shell is bash.  

***bash vs shell:***  
Shell scripting refers to scripting in any of the sh implementations like K shell, Z shell, bash, and so on. Since bash is the most common implementation of the shell, these are used interchangeably. Keeping all the above differences in mind, it is to be noted that bash and shell are not the same. There could be situations where one can be preferred over the other. Below is the list that includes the advantages of using one interpreter over the other.  
   
   simple port 80 scanner :

    #! /bin/bash
    # scan for open port 80
    nmap -sT 192.168.1.0/24 -p 80 >/dev/null -oG HTTP
    # cat HTTP 
    # Host: 192.168.1.1 ()    Status: Up
    # Host: 192.168.1.1 ()    Ports: 80/open/tcp//http///
    # Host: 192.168.1.2 ()    Status: Up
    # Host: 192.168.1.2 ()    Ports: 80/closed/tcp//http///
    # Host: 192.168.1.4 ()    Status: Up
    # Host: 192.168.1.4 ()    Ports: 80/open/tcp//http///
    cat HTTP | grep open > HTTP_open
    cat HTTP_open
    # Host: 192.168.1.1 ()    Ports: 80/open/tcp//http///
    # Host: 192.168.1.4 ()    Ports: 80/open/tcp//http///

   upgrade simple port 80 scanner :  

    #! /bin/bash
    # scan for open port 80
    echo "Enter starting IP"
    read start
    echo "Enter number for next IPs"
    read No 
    echo "Enter post"
    read port
    nmap -sT $start-$No -p $port >/dev/null -oG HTTP
    # cat HTTP 
    cat HTTP | grep open > HTTP_open
    cat HTTP_open
   
## Compressing And Archiving

***compressing types :***  
***lossy*** used with data not affected if we decrease quality like audio, video, ...  
***lossless*** used with data can't be in low quality like text files, programs, ...

### TARRING FILES TOGETHER

Tarring Files

    $ tar -cvf [name_of_tarred_file].tar [files_to_be_tarred]

Show List Of Tarred File

    $ tar -xvf [name_of_tarred_file].tar

extract Tarred Files

    $ tar -xf [name_of_tarred_file].tar
  
**options :**  
c – create a archive file.  
x – extract a archive file.  
v – show the progress of archive file.  
f – filename of archive file.  
t – viewing content of archive file.  
j – filter archive through bzip2.  
z – filter archive through gzip.  
r – append or update files or directories to existing archive file.  

### COMPRESSING FILES  
***bzip2*** , which uses the extension .tar.bz2  
slowest output small files  

compress :

    $ bzip2 [file_name]
    
extract :

    $ bunzip2 [file_name]
    
***gzip*** , which uses the extension .tar.gz or .tgz  
in between  

compress :

    $ gzip [file_name]
    
extract :

    $ gunzip [file_name]
    
***compress*** , which uses the extension .tar.z  
fastest output large files  

compress :

    $ compress [file_name]
    
extract :

    $ uncompress [file_name]
    
### Creating Bit-By-Bit Or Physical Copies Of Storage Devices  
     
    $ dd if=[input_file] of=[output_file]

## Filesystem And Storage Device Management

### The Device Directory /dev

sd : Sata Drivers 

|Device | fileDescription  |
|-------------|--------------|
|sda | First SATA hard drive | 
|sdb | Second SATA hard drive | 
|sdc | Third SATA hard drive | 
|sdd | Fourth SATA hard drive |

Partition | Description
|-------------|--------------|
|sda1 | The first partition (1) on the first (a) SATA drive|
|sda2 | The second (2) partition on the first (a) drive |
|sda3 | The third (3) partition on the first (a) drive |
|sda4 | The fourth (4) partition on the first (a) drive |


### Character and block device

c stands for character, and these devices are known, as you might expect, as character devices. External devices that interact with the system by sending and receiving data character by character

b stands for the second type: block devices.  They communicate in blocks of data (multiple bytes at a time) and include devices like hard drives and DVD drives. These devices require higher­speed data throughput and therefore send and receive data in blocks (many characters or bytes at a time). Once you know whether a device is a character or block device

    brw-rw----   1 root disk     8,     1 Jan 20 12:03 sda1
    crw-------   1 root root    10,   224 Jan 20 12:03 tpm0

### Mounting Storage Device
**/mnt** mostly used with internal mounted devices like hard disks  
**/media** mostly used with internal mounted devices like flash drives  

    $ mount/dev/sdb1 /mnt
    $ mount/dev/sdc1 /media

use unmount to remove devices .  

### Get Info And Check Errors

disk info

    $ df

file system check errors  
must unmount device before this step 


    $ fsck [option] [dev_dir]

## Becoming Secure And Anonymous

Show hops ip where your request pass 

    $ traceroute [domain_name]

Top solution for this topic :  
* TOR
* PROXY
* VPN

Mails : use ProtonMail

## Understanding And Inspecting Wireless Networks

### Detecting And Connecting To WiFi
### Basic Definitions
* **AP (access point)** This is the device wireless users connect to for internet access.  

* **ESSID (extended service set identifier)** This is the same as the SSID, but it can be used for multiple APs in a wireless LAN.  

* **BSSID (basic service set identifier)**This is the unique identifier of each AP, and it is the same as the MAC address of the device.  

* **SSID** name of the network  

* **Chanels** Wi­Fi can operate on any one of 14 channels (1–14). In the United States, Wi­Fi is limited to channels 1–11.  

* **Power** The closer you are to the Wi­Fi AP, the greater the power, and the easier the connection is to crack.  

* **Security** This is the security protocol used on the Wi­Fi AP that is being read from. There are three primary security protocols for Wi­Fi. The original, Wired Equivalent Privacy (WEP), was badly flawed and easily cracked. Its replacement, Wi­Fi Protected Access (WPA), was a bit more secure. Finally, WPA2­PSK, which is much more secure and uses a preshared key (PSK) that all users share, is now used by nearly all Wi­Fi APs (except enterprise Wi­Fi).  

* **Modes** Wi­Fi can operate in one of three modes: managed, master, or monitor.  

* **Wireless range** In the United States, a Wi­Fi AP must legally broadcast its signal at an upper limit of 0.5 watts. At this power, it has a normal range of about 300 feet (100 meters). High­gain antennas can extend this range to as much as 20 miles.  

* **Frequency** Wi­Fi is designed to operate on 2.4GHz and 5GHz. Modern Wi­Fi APs and wireless network cards often use both.  

### Modes in some details
Radio Modes
WiFi cards can be operated in one of these modes:
* Master (Access Point)
* Managed (also known as client or station)
* Ad-hoc
* Monitor
* Other proprietary modes (e.g. Mikrotik Nstreme)  

Radios may only operate in one mode at a time.

### Master Mode :
Master mode (also called AP or infrastructure mode)
is used to create a service that looks like a traditional
access point. The wireless card creates a network with
a specified name (called the SSID) and channel, and
offers network services on it.  
Wireless cards in master mode can only communicate
with cards that are associated with it in managed
mode

### Managed Mode :
Managed mode is sometimes also referred to as
client mode. Wireless cards in managed mode will join
a network created by a master, and will automatically
change their channel to match it.  
Clients using a given access point are said to be
associated with it. Managed mode cards do not
communicate with each other directly, and will only
communicate with an associated master.

### Ad-hoc Mode :
Ad-hoc mode creates a multipoint-to-multipoint
network when there is no master or AP available.  
In ad-hoc mode, each wireless card communicates
directly with its neighbors. Nodes must be in range of
each other to communicate, and must agree on a
network name and channel. 

### Monitor Mode :
Monitor mode is used by some tools (such as Kismet)
to passively listen to all radio traffic on a given
channel. This is useful for analyzing problems on a
wireless link or observing spectrum usage in the local
area.  
Monitor mode is not used for normal communications. 

### Basic Network Commands

    $ ifconfig
    $ iwconfig

nmcli : Network Manager Command Line Interface

    $ nmcli dev wifi
    $ nmcli dev wifi connect [AP_SSID] password [AP_PASS]

### WiFi Recon with aircrack-ng
To put your wireless network card in monitor mode, use the airmon-ngcommand from the aircrack­ng suite.

    $ airmon­ng start|stop|restart interface
    ex :
    $ airmon-ng start wlan0

The airodump-ngcommand captures and displays the key data from broadcasting APs and any clients connected to those APs or within the vicinity.
  
    $ airodump-ng [monitor_mode_interface]
    ex:
    $ airodump-ng wlan0mon

***BSSID*** The MAC address of the AP or client  
***PWR*** The strength of the signal  
***ENC*** The encryption used to secure the transmission  
***#Data*** The data throughput rate  
***CH*** The channel the AP is operating on  
***ESSID*** The name of the AP  


## Managing The Linux Kernel And Loadable Kernel Modules

Checking The Kernel Version

    $ uname -a
    or
    $ cat /proc/version

### Kernel Tuning With sysctl
show all sittings

    $ sysctl -a

In the man­in­the middle (MITM) attack, the hacker places themselves between communicating hosts to intercept information. The traffic passes through the hacker’s system, so they can view and possibly alter the communication. One way to achieve this routing is to enable packet forwarding.

    $ sysctl -a | grep ip_forward

to enable ip forwarding

    $ sysctl -w net.ipv4.ip_forward=1

***Remember*** : changes take place on run time but they lost on reboot  
to keep theme permanent edit config file */etc/sysctl.config*

### Managing Kernel Modules
display all modules

    $lsmod

see more info

    $ modinfo [module_name]

adding and remove modules

    $ modprobe -a [module_name]
    $ modprobe -r [module_name]

read kernel buffer

    $dmesg

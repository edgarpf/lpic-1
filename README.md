# LPIC-1

## Exam 101

### Commands

To know the type of the command (internal or external)
```
type cd
```
Show current directory
```
pwd
```  
List hidden files (-a) with details (-l)
```
ls -la
```  
Which types of shells are in your system?
```
chsh -l
```
Show session number in terminal
```
echo $SHLVL
```
Change session number and exit to the orginal one
```
echo $SHLVL
bash
echo $SHLVL
exit
```
Show alias and create one
```
alias
alias ls="ls -a"
```
Commands executed in sequence:
```
command1 ; command2
```
The second command will be executed only if the first one returns success
```
command1 && command2
```
The second command will be executed only if the first one returns failed
```
command1 || command2
```
Show path of the command
```
which ifconfig
```
Use command output
```
rpm -qf $(which ifconfig)
grep -i ext4 /boot/config-`uname -r`
```
To know who is using shell
```
whoami
```

```
history
!11 (execute command eleventh shown in history)
!-i (execute last command beginning with i)
history -c (clear history)
echo $HISTFILE
echo $HISTFILESIZE (max number of insertions)
```

Local and global variables:
```
LOCAL = "SOMETHING"
export GLOBAL = "SOMETHING"

unset GLOBAL
set # list all variables
env # list global variables
echo "$UID" #0
echo '$UID' #$UID 
echo $PS1 $PS2 # primary and secondary prompt

uname # informations about the machine. Use -p -m -s...
```
The path of the command
```
which pwd
```
Search for a command
```
apropos lda
man -k lda
```
Show path and path of the manual of a command
```
whereis pwd
```
Quotes
```
cd 'More than one word'
cd "More than one word"
echo $PWD
echo "$PWD"
/home/something
echo '$PWD'
'$PWD'
```
Show text with line number
```
cat -n file
```
Show text with line number except the empty lines
```
cat -b file
cat file | nl
nl file
```
Show number of lines/number of words/number of chars
```
wc -l file
wc -c file
wc -m file
```
Sort lines/inverse
```
sort file
sort -r file
```
Sort lines/inverse
```
less file
```
Show the first 10/20 lines of a file/show everything except the 20 lines first lines
```
head file
head -n 20 file
head -n -20 file
```
Show the last 10/20 lines of a file/ show continuously
```
tail file
tail -n 20 file
tail -f file
```
Show no repetion in lines (remove repetion only in lines in sequence)
```
uniq file
```
Show only lines with repetion
```
uniq -q file
```
Show number of repetion for every line
```
uniq -c file
```
Show oct/hex from a file
```
od file
od -tx file
```
Show files side by side
```
paste file1 file2
```
For each 3 lines split a file in other files
```
split -l 3 source destiny
```
Show the content of all files that begin with **file_**
```
cat file_*
```
Append text to a file
```
echo "test" >> file.txt
```
Generate hash of a file
```
md5sum file
sha256sum file
sha512sum file
```
Substitute first word test in the lines for test2 in the file
```
sed 's/test/test2/' file
sed 's|test|test2|' file
sed 's|test|test2|2' file (only second ocurrence)
sed 's|test|test2|g' file (substitute everything)
sed '1,25d' file (remove line 1-25)
sed -i '1,25d' file (alter the file indeed, now only show in the console)
```
Uppercase all letters
```
tr 'a-z' 'A-Z'
tr '[:lower:]' '[:upper:]'
```
Remove white spaces
```
tr -d ' '
tr -d '[:blank:]'
```
Show only first and third columns
```
cut -d':' -f 1,3
```
Show only the first six chars.
```
cut -c1-6 file 
```
Describe the type of a file
```
file file.txt
```
Show content of a xz/gz file
```
xzcat file.xz
zcat file.gz
bzcat file.bz2
```

Create file
```
touch file
touch -m file (just to update modify date)
```
Copy and move file
```
cp -b file dir/ (copy generating a backup file˜)
mv file dir/
```
Directories
```
mkdir dir
mkdir -m 750 dir (with permissions)
mkdir -p dir1/dir2 (create two directories at once)
rmdir dir (remove empty directory)
```
Find
```
find /etc -iname '*.conf' (find in /etc case insensitive)
find -cmin -3 . (find all the files whose permissions changed in the last 3 min)
find -ctime -3 . (find all the files whose permissions changed in the last 3 days)
find -atime -3 . (find all the files that were acessed in the last 3 days)
find -mtime -3 . (find all the files that were modified in the last 3 days)
```
Compression/joins
```
tar -cvpf backup-name.tar /etc /var/logs
tar tvf file.tar (show details of the files)
tar -xvf file.tar -C /tmp

gzip file.tar > file.tar.gz (mantain the original file)
gzip -d file.tar.gz
gunzip file.tar.gz

bzip2 -k file.tar (maintain the original file)
bunzip2 file.tar.bz2
xz -k file.tar (maintain the original file)
unxz file.tar.xz
```
Copy file byte to byte
```
dd if=source of=destiny bs=1M count=1024
```
Special characters
```
mkdir dir{1..10}
ls lib?
cat file >> out.txt (append file)
cat non_existing_file 2> error.txt (redirect error)
cat file file2 &> output.txt (redirect stdout and error)
```
xargs to send output from the last command as args to another command
```
find /usr/sbin -iname 'x*' | xargs ls -l
find /usr/sbin -iname 'x*' | xargs -i bash -c "echo listing file {}; ls {}"
```
tee to print the result of the command in the screen and send the result to a file 
```
cat file | tee output.txt
cat file | tee -a output.txt (to append)
```
Process
```
ps
ps u (more details with columns)
ps -u root
ps f (tree format)
pstree
pstree -p (show pids)
top (real time)
```
Search pid 
```
pgrep name
```
Search pid with name spelled exactly
```
pidof rsyslogd
```
Kill process
```
kill -l (list signals)
kill pid
killall gedit 
pkill firefo
```
Create and monitor process
```
less file & (execute in background)
jobs (list process in background)
fg id (take a process in background to foreground)
bg id
nohup ping 8.8.8.8 & (execute in background even if session is terminated)
cat nohup.out
```
System
```
free (show memory details)
free -m (show memory details in MB)
uptime
screen (generate another screen)
screen ls (list screens)
screen -r id (go to a specific screen)
```
watch and tmux
```
watch iptables -nvL (execute the command each 2s)
watch -n1 iptables -nvL (execute the command each second)
tmux (simular to screen command)
tmux ls
tmux rename-session -t 0 newname
tmux attach -t 0 (go to the session)
tmux kill-session -t 0
```
Process priority change
```
nice -n 15 command (add less priority to a process, only for new processing)
nice -n -1 command (add more priority but need permissions)
renice -n 10 -p pid (only for acurrently executing process)
```
Saarch in text with regular expression
```
sed 's/nologin$/REGEX/' file
sed -E 's/(nologin|false)$/REGEX/' file
sed -E 's/ˆ(nologin|false)/REGEX/' file
sed -E 's/(nologin|false)/REGEX/g' file (substitute all occurrences)
sed -E 's/[Mm].../REGEX/' file

grep -i root file (case insensitive)
grep -v root file (except root)
grep --color -E `root|daemon` file (you can use egrep without -E)
fgrep does not use regular expression but it is quicker
```
vi
```
vi +290 file (go to the line)
:set number (show line numbers
:90 (go to the line)
5 yy (copy 5 lines including the cursor line. Use p to paste)
3 dd (to cut)
/smtp (search for the word)
:7,50s/echo/something (find and replace)
:%s/echo/something (find and replace in all the lines)
u works like a ctrl+z
```
System architeture
```
cat proc/cpuinfo
lspci -k (show also modules)
lspci -s id -v (show many details of specific resource attached to pci)
lsusb -t (show in tree format
lsusb -d id -v (show many details of specific resource attached to usb)
lsusb -s 01:20 (to verify which device is using the module)
lsmod
modprobe -r snd-hda-intel (to unload a not used module)
modinfo -p nouveau (display all available parameters of a module)
#the file /etc/modprobe.d/blacklist.conf can be used to block the loading of a module

dmesg (to inpect system initialization process)

journalctl --list-boots (shows a list of boot numbers relative to the current boot, their identification hash and the timestamps of the first and last corresponding messages)
journalctl -b 0 (show logs of last initialization, -1 for the previous)
journalctl -k (show logs of kernel)
journal -u NetworkManger.service (show logs of a service)

runlevel (show the last runlevel and the current one)
initctl list (System services can be listed with command initctl list, which also shows the current state of the services and, if available, their PID number)
systemctl get-default
systemctl set-default multi-user.target (alternates between different targets modifying the symbolic link)
systemctl isolate multi-user.target (alternates between different targets)
systemctl list-unit-files (lists all available units and shows if they are enabled to start when the system boots)
systemctl suspense/hibernate

initctl list (list system services)

#Upstart
start tty6
stop tty6
status tty6

reboot
telinit
systemctl reboot
systemctl poweroff
init/telinit 6 (restart)
init/telinit 0 (power off)
```

Packages
```
fdisk /dev/sda (list all the partitions)
df -hT (show file system)
pvs (show physical volumes)
vgs (show volume groups)
lvs (show logic volumes)
efibootmgr (edit initialization of efi)

apt-get update
apt-cache search wordpress
apt-cache show wordpress
apt-cache depends wordpress (check dependencies)
apt-cache rdepends tar
apt-get install rar
apt-get remove rar -y (no interaction)
apt-get purge rar (remove everything)
apt-get -s install php (simulate the command)
apt-get upgrade
apt-get clean
apt-get -d install rar (only download)

apt update
apt install php
apt remove php -y
apt autoremove (remove unnecessary dependencies)
apt search word
apt show zenity

#low level command
dpkg -I file.deb (info)
dpkg -c file.deb (which files will be installed)
dpkg -L php (show ist of installed files)
dpkg -i file.deb
dpkg -r php
dpkg -S /bin/dd
dpkg -P php (purge)
dpkg-reconfigure something

yum search something
yum install something
yum remove something
yum check-update
yum update something

rpm2cpio (to convert rpm into cpio)

zypper search something
zypper info something
zypper install something
zypper remove  --clean-deps something
zypper list-updates
zypper update something

rpm -iv --test file.rpm
rpm -q something (search)
rpm -ivh file.rpm
rpm -e something
rpm -K file.rpm (check hask of package)
rpm --checksig file.rpm
rpm -V bind-utils (check if there is difference between package and file)

dnf is similar to yum
```

File
```
fdisk -l (show partitions)

mount /dev/sda1 /mnt/tmp
grub-install --boot-directory=/mnt/tmp /dev/sda

fdisk /dev/hdd
fdisk /dev/sda
o (create a new table of partitions) -> n (create partition) -> p (create primary partition) -> 1 (position of partition) -> 1 (first cylinder) -> 2048M (last cylinder)
p -> list partitions

gdisk (manage gpt partitions, very similar to fdisk)

parted (show first disk)
print all (show all partitions)
select disk
mklabel/mktable (create table partitions)
mkpart (create partion primary or extended. To create a logic one you need to create a extended first)

mkfs -t ext3 /dev/hdd
mkfs..hfs /dev/hdd5
mkswap /dev/hdd2
swapon /dev/hdd2 (mount swap partion)

mke2fs /dev/sbd1 (create file system ext2 by default)
mke2fs -t ext3 -L "label" dev/sbd2

df -hT (show details of file system including space and type)
df -ht ext4 (show only ext4)

du -h (show size of hidden directories)
du -ha (show also file sizes)

fsck /ev/sda4 (does not work if it is in usage)
fsck -t ext3 dev/sdb1 (file -s to show type)
fsck -A (check all)
e2fsck -y /dev/sdb2 (answer yes by default)

tune2fs -l /dev/mapper/system-root
tune2fs -m 10 /dev/mapper/system-root
```
### Hints
* The root directory (/) is the first partition that has to be mounted. After that, the system will have access to the main configuration files in /etc, like, for instance, the /etc/fstab, and, with that, will obtain information about the other partitions to be mounted.
* The commands “man” and “info” will show, in most of the cases, a whole manual about each command. “whatis” will bring a brief definition about the tool function.
* The command dmesg has as an output a register of the logs in the system boot, the same information can be found in the file /var/log/dmesg, however, not all distributions currently include this file. In the journalctl, the -k options shows all the kernel messages from the current boot, the -b option can also be used but contains all messages, not only kernel related.
* “wall” will send the message that follows the command directly to the terminal where all the users are connected.
* The /usr/share contains many system files, including the documentation pages in /usr/share/doc and the manuals in /usr/share/man.
* System V, or SysV, is the init that was originally used in Linux environments, inherited from Unix. Currently most distributions use the systemd and some use Upstart. Anacron is a process scheduling tool.
* The commands :wq, :x and ZZ will save the document in vim and leave.
* It’s important to remember that a partition with ID 82 (0x82) will be assigned to the swap area, while partitions with ID 83 (0x83), Linux Native, will be used to Linux files. The swap area of a system can be composed of several partitions.
* The GRUB settings must be made in /etc/default/grub, after using update-grub or grub-mkconfig is when the file /boot/grub/grub.cfg will be updated. The file menu.lst is used for GRUB Legacy, not for GRUB2.
* If there’s no specified parameter, split command will split a file in other files with 1000 lines each. The -l option can be used to set the desired number of lines and the -b option to set in bytes.
* The ldd command followed by the application's name will show the dynamic libraries used by the application.
* The file /etc/apt/sources.list contains a list of URLs and parameters used by the APT commands to check and download the new packages.
* The command dpkg-reconfigure can be used to reconfigure a package already installed.
* xfs_repair repairs corrupt or damaged XFS filesystems.
* The MBR area is located in the first sector of the bootable disk, contains the information for loading the bootloader (GRUB) and the system partition table. MBR loads and runs GRUB.
* The -r option of the shutdown command can be used to reboot the system, as well as the reboot command. Telinit 6 invokes runlevel 6 which is related to rebooting the system.
* Some directories can not be mounted on partitions other than the / partition. The / partition is the first to be mounted, and after that, configuration files and tools will be used to finalize the system boot, including mounting other partitions, if these files are on different partitions, they will not be accessible. The directories that should be on the same partition are /etc, /sbin, /bin, /lib, /media, /mnt, /proc, /sys, /dev.
* The grub-install command will install the GRUB files on the indicated device, by default in the /boot directory.
* "dpkg -s", "apt-cache show" and "apt show" will return various information from a package installed on the system.
* The command "yum install --downloadonly " will only download an rpm package from the configured repositories, but will not install it.
* Zypper is the rpm package manager used in OpenSuse systems. The options are similar to yum, but not the same. In general there is a long option, for example "zypper install ksh" or short, "zypper in ksh".
* In the rpm command, used for direct installation of .rpm packages, the -U option can be used to install or update a package that already exists. The rpm -i option will only perform a fresh install, but will not update a package that is already installed. The --force option forces the installation of a package.
* The command env show only the exported variables, while the comand set shows even local variables.
* type command is used for displaying information about command type. It displays if command is an alias, shell function, shell builtin, disk file, shell reserved word or if the command is hashed in cache.
* The command "uniq -d" shows only the duplicate lines as long as the file is sorted.
* The -p option in the mkdir causes the entire tree to be created.
* 0 is the standard input descriptor (stdin), 1 is the standard output descriptor (stdout) and 2 is the output error (stderr).
* The function of the tee command is to receive an input, usually the output of another command with the use of |, display this input on the screen and at the same time write it to a file.
* The pkill and killall commands use the name of the process as an argument, pkill allows several other variables such as the user name of the process owner, for example. The kill uses the PID as argument, pgrep only shows the PID of a process.
* The watch command can be used with any command, so that it is replayed constantly, the default time is 2 seconds, but the -n option allows you to set the update time.
* Without any parameter, kill sends the SIGTERM signal, code 15, this signal kills the process in a soft way, giving the process time to complete its tasks.
* The jobs command shows all processes (or set of them) started in the background, using & in the current session.
* The “nice” of a process can be configured with values ranging from -20 to 19, where -20 increases the priority to the maximum, and 19 decreases to the maximum.
* In grep, the -c option counts the occurrences of the string, in how many lines the string appeared. The -l shows the files that have a certain string. fgrep is a grep that does not accept any type of regular expression. Egrep is a grep that accepts extended regular expressions but the -n option would only include a number in the rows of the result.
* 21dd removes the current line and the next 20 lines in vim.
* The df command is used to check the use of a partition, usually shows the disk space, but with the -i option it displays the use of inodes.
* Mount is the command used to manually mount a partition to a directory.
* The chgrp command is specific for group definition with the syntax: chgrp . The chown command can be used to set the user owner and the group, accepting the following syntaxes: chown : ou chown . , where the can be ommited.
* Permissions are set by subtracting the umask value from value 666 for files and 777 for directories. Thus, the value 0002, which may also appear as 002, will be 666 - 002 = 664 (rw-rw-r--).
* ln file1 file2 create a hard link to file1, called file2.
* Whenever a file has the letter "l" at the beginning of its permissions, followed by 777 permissions, it is an indicator of being a symbolic link.
* Which searches for files only in the directories included in the PATH.
* The hypervisor is a required layer between the Infrastructure (aka Host) and the Virtual Machine itself, or Guest. The hypervisor controls and manages the access of virtual machines to the hardware elements of the infrastructure.
* Btrfs natively supports features like subvolumes, snapshots, multi-devices/RAID and transparent data compression.
* fdisk and parted can create GPT and MBR partitions. gdisk is specific to the GPT type.
* SATA storage devices follow the same standard as SCSI disks, that is, /dev/sdX. ATA/IDE disks use the /dev/hdX standard.
* IRQ stands for Interrut Request Line, or Interrupt Request. This information is recorded in the /proc/interrupts dynamic file.
* After the boot process, the kernel invokes the /sbin/init process as the first system process, and it starts the other processes, so all other processes are children of the init process.
* POST (Power-On Self-Test) is a BIOS procedure that checks if all devices are ready for use. The MBR (Master Boot Record) is the disk area that contains the information that will be used during the boot processs, GRUB is a boot manager and UEFI is a new firwmware being used in BIOS's place in modern systems
* The kernel supports a series of parameters that can be used at startup, such as quiet enable silent mode, not displaying startup and error messages. Other options are mem (maximum amount of RAM), ro (read only), splash (splash screen), among others.
* In systemctl, the isolate option is used to switch between execute modes, or target (runlevels in SysV). For recovery mode (or single mode) the targets rescue.target or runlevel1.target are used.
* Runlevel 0 is related to system shutdown and runlevel 6 to system reboot, so using 0 or 6 would make it impossible to boot the system.
* The /etc/inittab file shows the init process which is the default runlevel, by the parameter "initdefault", and with that, which services should be started by the system.
* In MBR partitioning, there is a limit of 4 primary partitions or 3 primary partitions and 1 extended partitions in which the logical partitions will be associated.
* The LVM (Logical Volume Manager) has 5 main elements: VG (Volume Group), PV (Physical Volume), LV (Logical Volume), PE (Physical Extent) and LE (Logical Extent).
* As the question mentions the file menu.lst, we are talking about the Legacy GRUB and in that standard hd0,3 indicates the fourth partition (since the count starts from 0) of the first disk. If it were GRUB2, hd0,3 would be the third partition of the first disk, ie / dev / hda3.
* GRUB_DEFAULT = X indicates which system should be started by default. GRUB_TIMEOUT indicates the timeout before booting the kernel.
* The ldconfig command updates the /etc/ld.so.cache file.
*  apt-cache depends shows the dependencies of a package
*  The dpkg command is used to install/update/remove packages directly, the -i option does the installation procedure.
*  n the rpm command you must first enter the operating mode parameter, in this case the mode is the query, represented by -q, after that the option "f" receives a file as parameter and rpm identifies the package related to it.
*  The -V or -verify option of rpm checks the integrity of a package.
*  The data about the repositories used by the package manager are in the files in the /etc/yum.repos.d/ directory. /etc/yum.conf refers to general YUM settings.
*  The export command causes a variable to become global, so that all child processes can work with the contents of this variable.
*  By default Linux, the .bash_history file in the user's $ HOME will contain the command execution history, being updated at the end of each user session.
*  The uname command provides various system information, including the kernel-release, by the -r option.
*  Since the directory is not in the PATH, the form "report.sh" can not be used, the ./report.sh should be used. Another way is to use the script as the command shell/bash shell (or sh, or ksh, etc).
*  The touch command can be used to create a file without any content and also to change the dates of access and modification of a file.
*  The most common use of the dd command is to create an image from a partition, and vice versa, in that way the syntax uses if= to inform the source and of= to inform the destination.
*  In the tar command, the "t" option displays the contents of the grouped/compressed file, the -f should always be used to indicate the .tar or .tgz file.
* The rm command with the -r option removes a directory recursively, that is, removes the directory and everything inside. rmdir is only used to remove empty directories.
* The tee command must be used to display an output on the screen while writing to a file, but by default the tee overwrites the file if it already exists, the -a option causes the tee to append to the file, including output at the end, without deleting the previous content.
* SIGHUP can cause a process to die, to be restarted, or to reread its configuration files, with 1 being its numeric code. 9 is the code for SIGKILL, 10 for SIGUSR1 and 15 for SIGTERM.
* In the shell, by default every command will be started in foreground mode, to force initialization as background, that is, unlinked from the shell, the & symbol at the end of the command should be used.
* The command ps with option "a" shows the processes of other users but linked to the current terminal. The "u" option enables the user format, displaying the user name of each process as well as other details of the process. The "x" option shows the processes of all terminals, as well as processes that are not associated with any terminal.
* In general, load average allows you to check how the execution of processes on a system is. This value can be viewed by the uptime and top commands.
* When using the nice command to start a process, by default the value 10 is assigned to it, that is, the priority is reduced. When a process is started without using nice, the assumed NICE value is 0.
* The renice and top commands can be used to change the NICE value of a process that is already running. The nice command is used to set the value when starting a process.
* In grep/egrep/fgrep, the -v option has the effect of not displaying the string or results of the expression used.
* The -c option in grep/egrep counts the number of rows in which the string/expression is found.
* The EDITOR environment variable can be used to define the default text editor in the shell.
* The "a" option enters edit mode one character after the current cursor position. The "i" option enters edit mode exactly at the current cursor position. The "o" option enters edit mode on the line below the current cursor position.
* Both fdisk and parted have the -l option to display the system partitions. The information is also always present in the /proc/partitions file.
* The journaling feature was implemented in the ext3 filesystem, the only difference being with ext2.
* The du command can be used to recursively check the disk space usage of files and directories. Df is used to show the use of system partitions.
* The difference from ext3 to ext2 is the journaling feature, so the tune2fs command, with the -j option, to turn a device into ext3.
* The -a option of the mount command will mount all partitions listed in /etc/fstab, except entries containing the "noauto" option. Without any option, mount only displays the currently mounted partitions.
* The first line information of /etc/fstab should be the device name (device, UUID or Label), the second should be the directory to be mounted.
* The partition must be unmounted so that the fsck command is used and the partition is checked. For this the first command to be executed must be the umount.
* Permissions are set by subtracting the umask value from value 666 for files and 777 for directories. Thus, the value 022, which can also appear as 0022, will be 777 - 022 = 755 (rwxr-xr-x)).
* The best example of the Sticky bit is the /tmp directory, the /tmp permission is drwxrwxrwt, any user can create a file in /tmp, but only the one who created the file can remove it or change it.
* Chown can be used to define the user and the owner group, accepting the following syntax: chown : ou chown . .
* A physical link can be seen as a new file that points to the same volume of data, they are different files that use the same inode. In the hard link, the destination file and the link must be in the same partition (this is not mandatory in the symbolic link). Because the permissions settings are configured in inode, and the two files share the same inode, the two files share the same access permissions.
* The -s option of the ln command specifies the creation of a symbolic link and the main form of use is: ln –s
* The locate command uses an internal Linux base that contains the location of all system files, allowing a quick response to the command, however that base needs to be updated by the updatedb command, usually executed at system startup, or regularly by scheduling.
* The Guest/Device Drivers are installed on the Hosts Operating Systems of the virtual machines to improve their performance and usability.
* The md5sum, sha256sum and sha512sum commands are used to generate, based on different algorithms, a set of characters representing a particular file, in order to enable them to be checked later.
* The modprobe command is used to load and remove modules from the system.
* Bootloader is the process who is responsible for selecting and running the kernel and initrd during the boot process?
* The shutdown command can be used both to shut down and to restart the system, with the use of the -r option, with the advantage of the possibility of scheduling.
* Modern computers support the Advanced Configuration and Power Interface, which enables intelligent power management in your system and queries battery status and configuration. The acpid daemon monitors these events by taking actions related to their internal rules and settings.
* systemctl status https.service
* MBR partitioning allows a maximum of 4 primary partitions, or 3 primary partitions and 1 primary partition. In the extended partition, the logical partitions are associated. Primary or extended partitions are numbered from 1 to 4, logical partitions are numbered from 5.
* Systems that use UEFI as firmare have a special partition called ESP (EFI System Partition), which is mounted in the /boot/efi/ directory.
* The grub.cfg file is used by GRUB2, so the parameter that indicates the kernel is "linux".
* LD_LIBRARY_PATH can be configured to temporarily set the location of a library on the system.
* With "dpkg -S" (or --search) it is possible to inform a file and identify the package "owner" of this file.
* The apt-get/apt "upgrade" option will update all packages on the system.
* In the rpm command the -e or --erase options can be used to remove a package. In the yum the "erase" and "remove" options can be used for the same function.
* In DNF and YUM, the "update" option updates one or all of the packages on the system, the "upgrade" option does the same as "update" but considers the packages obsolete, removing them if necessary.
* In the rpm command the -q option enables the "query" mode and the "l" option allows to inform a package and to return all packages installed by it.
* By typing $$ the user receives the PID (Process ID) of the current shell. $! is the PID of the last process in the backgroud (job) run. $? is the exit code of the last executed command.
* The HISTFILE environment variable stores the path and file name that will store the command history, by default /home/.
* There are some options to repeat previous commands, among them !! executes the last command used.
* In sed, the statement must be enclosed in single quotation marks. Another importan point is the "g", of global, at the end of the expression, without it only the first occurrence of each line would be replaced, not all occurrences.
* In the "ls" command, the "a" option displays the hidden files, the "l" shows the details, the "t" command so that the older files appear at the end of the command and the "r" reverses the file, making the newer files appear at the end of the listing.
* The "file" command can be used to determine the type of a file.
* The find has 3 types of time search: ctime (change time) = last change of content and/or properties (permissions, etc), mtime (modification time) = last change of content, atime (access time) = last time the file has been accessed.
* Signal 2, or SIGINT, is associated with Ctrl C, and stops executing a process.
* With nohup, a process in general runs as follows: nohup &. That way it starts in the background and will continue to run even if bash is closed.
* The pstree command displays the processes hierarchically, the -p option displays the PID of each process.
* If you used nice -8 command, the nice value associated with the command would be 8.
* Nice values range from -20 to 19, where -20 gives the highest priority and 19 the lowest priority.
* The fgrep command only filters for text strings, but does not interpret regular expressions.
* The ? does the search from the end to the beginning, the / does the search from beginning to end.
* By pressing yy the current line is copied, to copy the current line and more 9 can be used y10y or 10yy.
* O :! followed by a command will execute this command, show the result and return to the same point of the text.
* After defining the partition, you still need to format it with the mkswap command so that after that it can be included in the swap area with the swapon command.
* After defining a partition, using fdsisk, parted or gdisk, the partition must be formatted, that is, the file system must be created, for that the main command is mkfs or mkfs.type, mke2fs is used for filesystems ext2/3/4.
* In addition to the device name, the partition can be informed by the Universally Unique Identifier (UUID), as the name says, a unique identifier defined for each system partition, or even by the Label, defined by the user at the time of partition creation.
* The "noauto" option says that the partition should always be mounted manually, "auto" has the opposite effect. "ro" sets the partition to read-only, umount is not a valid option.
* The SGID is represented by replacing the "x" with the "s" in the group permissions.
* When using o-rx in chmod, the administrator is removing the permissions r and x from the others level.
* A symbolic link is nothing more than a pointer to another file, so its content is just the way to its destination.
* The /sbin and /usr/sbin directories have programs used in system administration, only by the root user, such as fsck, mkfs, repquota, and so on.
* The BIOS/UEFI firmware contains the device boot order to be used.
* n the sed command the -i option causes the source file to be changed. O /d indicates that any line containing the string will be removed.
* xfs_fsr (from FileSystem Reorganizer), has the function of improving the organization of the XFS file system.
* The lsblk commands, with the -f, and blkid option, will display all partitions and their respective UUID, Label, and various other information.
* The /bin/sh file on Linux now typically points to a shell program
* The uname -r command will display only the current Linux kernel version (revision).
* The echo \^New \^Style command will display ^New ^Style, because the backslash is a form of shell quoting that protects a single character after it. 
* The which fortytwo.sh command will search the directories listed in the $PATH environment variable for the fortytwo.sh program. If it is found, it will display the program’s absolute directory reference.
* The three modes of the vim editor are command (also called normal mode), insert (also called edit or entry mode), and ex (sometimes called colon commands) mode.
* Delimiter is one or more characters that create a boundary between different data items in a record.
* (lasting | final) is Extended Regular Expession (ERE) not a BRE.
* A file descriptor is a number that represents a process’s open files.
* By default, STDOUT goes to your current terminal, which is represented by the /dev/tty file.
* sort SpaceOpera.txt 2> /dev/null put the error message in the black hole.
* A systems package manager database typically contains information on application files as well as their directory locations, software versions, and any library
dependencies.
* The CentOS Linux distribution uses the Red Hat package management system, which uses .rpm files.
* The yum and dnf programs are used to install .rpm packages from Red Hat–based repositories.
* /etc/yum.repos.d/ is the path to add a third-party repository to his Red Hat–based package management system.
* Both the rpm2cpio and cpio utilities are needed to extract the files from an .rpm package file.
* To list currently installed packages with missing dependencies, you should issue the apt-cache unmet command.
* You can reconfigure a package via the dpkg-reconfigure utility.
* You should use the ldconfig command to update the system’s library cache.
* The /etc/ld.so.conf.d/ directory, LD_LIBRARY_PATH environment variable, and the /lib* and /usr/lib*/ folders are all potential locations where library file
locations may be stored.
* The GNU ps command in Linux supports parameters that were supported by the legacy BSD and Unix ps command, along with new options created by GNU.
* With no command-line options, the GNU ps command displays only processes run by the current shell.
* The top command displays the currently running processes on the system and updates every 3 seconds.
* The top S command displays the processes based on the cumulative CPU time for each process.
* The GNU Screen utility employs the screen commands, and the screen -ls command will display any detached windows belonging to Natasha along with their window IDs.
* Use the jobs -l command to see all his current background jobs.
* The kill command allows you to stop an application that’s already running by specifying its process ID.
* The workstation firmware looks for the boot loader program to load an operating system.
* The workstation firmware looks at the first sector of the first hard drive to load the boot loader program. This is called the MBR (master boot record).
* The BIOS firmware can look in multiple locations for a boot loader program.
* The master boot record (MBR) is located in only one place: on the first sector of the first hard drive on the workstation.
* The ESP is stored in the /boot/efi directory on Linux systems.
* The UEFI firmware method has replaced the BIOS in most IBM-compatible computers.
* The solid-state drive (SSD) storage device uses an integrated circuit to store data.
* Linux creates files named sdx in the /dev directory for SCSI devices. For the second SCSI device, Linux would create the file /dev/sdb.
* The lvcreate program creates a logical volume from multiple partitions that you can use as a single logical device to build a file system and mount it to the virtual directory.
* The GNU gparted program provides a graphical window for managing device partitions.
* The fdisk -p command displays the current partition table for the hard drive,
* Linux uses mount points to insert a filesystem on a storage device to the virtual directory.
* The ext filesystem was the original filesystem used in Linux, and ext4 is the latest version of it.
* The mkfs program allows you to create a new filesystem on a partition.
* The swap filesystem type creates a virtual memory swap area for the Linux kernel to use to create virtual memory.
* The mount program allows you to insert the filesystem on a partition into the virtual directory.
* The umount command allows you to specify either the partition or the location in the virtual directory to remove from the virtual directory.
* The fsck program repairs corrupted filesystems.
* The du command displays the disk usage by directory, allowing you to easily check the HOME directories of all user accounts and determine which user has the most disk space.
* 

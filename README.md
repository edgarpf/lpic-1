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


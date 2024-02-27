# LPIC-1

## Exam 101

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
```












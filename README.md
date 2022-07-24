# LPIC-1
Kernel release number/System Architecture/Everything:
```
uname -r
uname -m
uname -a
```
Details about cpu:
```
lscpu
```
***/dev*** is the device directory.
***/proc*** is the process directory.

To see the modules:
```
lsmod
```
Show details about a specific module:
```
modinfo name_of_module
```
Show the author of a specific module:
```
modinfo -a name_of_module
```
Show what a specific module does:
```
modinfo -d name_of_module
```
Show license:
```
modinfo -l name_of_module
```
Remove module:
```
sudo modprobe -r name_of_module
```
Add module again:
```
sudo modprobe name_of_module
```
List all PSI devices:
```
lspsi
lspsi -v
lspsi -vv
lspsi -vvv
```
List all PSI devices with modules:
```
lspsi -k
```
List all USB devices:
```
lsusb
```
See the process:
```
pstree -p
```
See the messages from the kernel ring buffer:
```
dmesg
```
May be used to control the contens of systemd(1). Use ***-k** to show only kernel content:
```
journalctl
journalctl -k
```


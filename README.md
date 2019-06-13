## UbuntuRelatedProblems

Fix error : unknown filesystem Grub rescue mode

type ``` ls ``` in the window and hit enter

```
grub rescue/ set boot=(hd0,msdos5)

grub rescue/ set prefix=(hd0,msdos5)/boot/grub

grub rescue/ insmod normal

grub rescue/ normal
```

after opening ubuntu:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

## Lock Error
If you try to run ``` sudo apt-get update ```  or  ``` sudo apt-get upgrade ``` , you get this type of error

```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/ 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) 
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
### Solution
```
sudo rm /var/lib/dpkg/lock
sudo rm /var/lib/apt/lists/lock
sudo rm /var/cache/apt/archives/lock
```

## Dpkg Error Code(1)
```
dpkg: error processing package python-numpy (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libblas3
 liblapack3
 python-numpy
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
### Solution

try this code snipet, it is work fine for me!
```
sudo mv /var/lib/dpkg/info/libblas3.postinst /var/lib/dpkg/info/libblas3.postinst.backup
```
and
```
sudo mv /var/lib/dpkg/info/nliblapack3.postinst /var/lib/dpkg/info/nliblapack3.postinst.backup
```
do the same for all error causing modules.

after you try to update the cache using ``` sudo apt-get update```


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

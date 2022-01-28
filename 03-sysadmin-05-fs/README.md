1. Разреженные файлы можно использовать для
образов дисков виртуальных машин;
резервных копий дисков и/или разделов, созданных спец. ПО.
2. Нет, т.к. это ссылка на один и тот же файл.
3.
![image](https://user-images.githubusercontent.com/95243483/151575722-104e7fb7-4846-4ff3-b41c-cf481466c68b.png)

4.
![image](https://user-images.githubusercontent.com/95243483/151578367-ea44731c-0cf0-42a2-bacd-8842cb1c63a7.png)

5.
![image](https://user-images.githubusercontent.com/95243483/151580151-c56e7380-0110-409b-9727-bd9abae90c1f.png)

6.
![image](https://user-images.githubusercontent.com/95243483/151581277-2d7834b8-8d9c-4da0-8131-3b3a96e5582a.png)

7.
![image](https://user-images.githubusercontent.com/95243483/151581731-a7e81428-174f-4b3b-bcff-411e25b803bb.png)

8.
```
root@vagrant:~# pvcreate /dev/md1 /dev/md2
  Physical volume "/dev/md1" successfully created.
  Physical volume "/dev/md2" successfully created.
```
9.
```
root@vagrant:~# vgcreate vg1 /dev/md1 /dev/md2
  Volume group "vg1" successfully created
```
10.
```
root@vagrant:~# lvcreate -L 100M vg1 /dev/md2
  WARNING: Device /dev/sda2 not initialized in udev database even after waiting 10000000 microseconds.
  WARNING: Device /dev/sda2 not initialized in udev database even after waiting 10000000 microseconds.
  Logical volume "lvol0" created.
root@vagrant:~# lvs
  WARNING: Device /dev/sda2 not initialized in udev database even after waiting 10000000 microseconds.
  LV        VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao----  31.50g                                                 
  lvol0     vg1       -wi-a----- 100.00m
  ```
11.
```
root@vagrant:~# mkfs.ext4 /dev/vg1/lvol0
mke2fs 1.45.5 (07-Jan-2020)
Creating filesystem with 25600 4k blocks and 25600 inodes

Allocating group tables: done
Writing inode tables: done
Creating journal (1024 blocks): done
Writing superblocks and filesystem accounting information: done
```
12.
```
root@vagrant:~# mkdir /tmp/new
root@vagrant:~# mount /dev/vg1/lvol0 /tmp/new
```
13.
```
root@vagrant:~# ls -l /tmp/new
total 21556
drwx------ 2 root root    16384 Jan 28 16:20 lost+found
-rw-r--r-- 1 root root 22056717 Jan 28 15:02 test.gz
```
14.
![image](https://user-images.githubusercontent.com/95243483/151583882-aa76cb6e-0d11-4b1d-b99b-4d93b84b1cbd.png)

15.
![image](https://user-images.githubusercontent.com/95243483/151584095-547cc436-95fe-4583-8672-17c1e5036703.png)

16.

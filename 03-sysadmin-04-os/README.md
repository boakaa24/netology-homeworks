1. 
![image](https://user-images.githubusercontent.com/95243483/151024382-3f75011c-f43f-4a74-ba47-2af3590b9c4d.png)

```
 sudo systemctl status node_exporter
● node_exporter.service - Prometheus Node Exporter
     Loaded: loaded (/etc/systemd/system/node_exporter.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2022-01-25 17:08:22 UTC; 59s ago
   Main PID: 1167 (node_exporter)
      Tasks: 4 (limit: 467)
     Memory: 2.6M
     CGroup: /system.slice/node_exporter.service
             └─1167 /usr/local/bin/node_exporter
```
2.
```
node_cpu_seconds_total{cpu="0",mode="idle"} 88.98
node_cpu_seconds_total{cpu="0",mode="system"} 10.84
node_cpu_seconds_total{cpu="0",mode="user"} 2.98

node_memory_MemAvailable_bytes 3.4183168e+08
node_memory_MemFree_bytes 2.4576e+07

node_disk_io_time_seconds_total{device="sda"} 12.82
node_disk_read_time_seconds_total{device="sda"} 9.677
node_disk_write_time_seconds_total{device="sda"} 2.021

node_network_receive_errs_total{device="eth0"} 0
node_network_receive_drop_total{device="eth0"} 0
node_network_receive_bytes_total{device="eth0"} 17237
node_network_transmit_bytes_total{device="eth0"} 10684
node_network_transmit_drop_total{device="eth0"} 0
node_network_transmit_errs_total{device="eth0"} 0
```
3.
![image](https://user-images.githubusercontent.com/95243483/151032701-697e2afe-dfb0-402a-9b11-891b36c1464d.png)
4. Да
```
vagrant@vagrant:~$ dmesg |grep virtual
[    0.004322] CPU MTRRs all blank - virtualized system.
[    0.049203] Booting paravirtualized kernel on KVM
[    0.724313] Performance Events: PMU not available due to virtualization, using software events only.
[   10.521276] systemd[1]: Detected virtualization oracle.
```
5.
```
vagrant@vagrant:~$ /sbin/sysctl -n fs.nr_open
1048576
vagrant@vagrant:~$ cat /proc/sys/fs/nr_open
1048576
```
Этот файл определяет общесистемное ограничение на количество открытых файлов для всех процессов.
```
vagrant@vagrant:~$ ulimit -Sn
1024
```
Мягкий лимит числа открытых файлов для пользователя(может быть увеличен)
```
vagrant@vagrant:~$ ulimit -Hn
1048576
```
Жесткий лимит числа открытых файлов для пользователя(не может быть увеличен)  
6. 
```
root@vagrant:~# unshare -f --pid --mount-proc sleep 1h
^C
root@vagrant:~# ps
    PID TTY          TIME CMD
   3576 pts/0    00:00:00 sudo
   3578 pts/0    00:00:00 bash
   3622 pts/0    00:00:00 sleep
   3623 pts/0    00:00:00 ps
root@vagrant:~# nsenter --target 3622 --pid --mount
root@vagrant:/# ps
    PID TTY          TIME CMD
      1 pts/0    00:00:00 sleep
      2 pts/0    00:00:00 bash
     13 pts/0    00:00:00 ps
```
7.

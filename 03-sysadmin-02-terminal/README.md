# Домашнее задание к занятию "3.2. Работа в терминале, лекция 2"

1. Это встроенная команда Bash.
2. grep -c 'word' /path/to/file
3.  pstree -p

```
  systemd(1)─┬─VBoxService(832)─┬─{VBoxService}(833)
           │                  ├─{VBoxService}(834)
           │                  ├─{VBoxService}(835)
           │                  ├─{VBoxService}(836)
           │                  ├─{VBoxService}(837)
           │                  ├─{VBoxService}(838)
           │                  ├─{VBoxService}(839)
           │                  └─{VBoxService}(840)
 ```
        
4. 
```
vagrant@vagrant:~$ who
vagrant  pts/0        2022-01-18 17:08 (10.0.2.2)
vagrant  pts/1        2022-01-18 17:21 (10.0.2.2)
vagrant@vagrant:~$ ls -l \1 2>/dev/pts/1
```
```
vagrant@vagrant:~$ ls: cannot access '1': No such file or directory
```
5.
```
vagrant@vagrant:~$ cat >1
12345
67890
vagrant@vagrant:~$ cat 1
12345
67890
vagrant@vagrant:~$ cat <1 >2
vagrant@vagrant:~$ cat 2
12345
67890
```
6. vagrant@vagrant:~$ sudo echo Hello >/dev/tty1  
   наблюдать в графическом режиме не получится. Только если подключиться с консоли.
7. bash 5>&1 - Создаст дескриптор с 5 и перенатправит его в stdout  
   echo netology > /proc/$$/fd/5 - Отправит эхо в 5 дескриптор, затем перенаправит в stdout
8. ```
   vagrant@vagrant:~$ ls -l /3 5>&2 2>&1 1>&5 |grep no -c
   1
   ```

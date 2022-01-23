1. chdir("/tmp")
2. /usr/share/misc/magic.mgc
3. можно использовать
```
# pgrep -f имя_процесса
# lsof -nP | grep '(deleted)' "Что бы найти дискриптор удаленного файла"  
# > /proc/$PROC/fd/$FD
```
4. Зомби процессы освобождают свои ресурсы, но не освобождают запись в таблице процессов.
5.
```
32    vminfo              5   0 /var/run/utmp
627    dbus-daemon        -1   2 /usr/local/share/dbus-1/system-services
627    dbus-daemon        20   0 /usr/share/dbus-1/system-services
627    dbus-daemon        -1   2 /lib/dbus-1/system-services
627    dbus-daemon        20   0 /var/lib/snapd/dbus-1/system-services/
```
6. системный вызов uname()  
Part of the utsname information is also accessible  via  /proc/sys/kernel/{ostype, hostname, osrelease, version, domainname}.

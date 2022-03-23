1.
```
   a) ошибка разные типы переменных  
      TypeError: unsupported operand type(s) for +: 'int' and 'str'  
   b) a = '1'  
      b = '2'  
   c) a = 1  
      b = 2
```
2.
is_change переменная не используется. Можно убрать  
breake убрать, т.к. с ним выводится только одно извенение
  ```
  import os

bash_command = ["cd ~/pythonProject/sysadm-homeworks", "git status"]

result_os = os.popen(' && '.join(bash_command)).read()

#print(result_os)
#is_change = False
for result in result_os.split('\n'):
    if result.find('modified') != -1:
        prepare_result = result.replace('\tmodified:   ', '')
        print(prepare_result)
#        break

Вывод

2
README.md
```
3.
```
import os
import sys

path = sys.argv[1]

bash_command = ["cd "+path, "git status"]

result_os = os.popen(' && '.join(bash_command)).read()

for result in result_os.split('\n'):
    if result.find('modified') != -1:
        prepare_result = result.replace('\tmodified:   ', '')
        print(prepare_result)

boakaa@DESKTOP-H6SSPL9:~/pythonProject$ python3 1.py ~/pythonProject/sysadm-homeworks
2
README.md
```
4.
для хранения ip используем json файл
```
conf.json

{
  "drive.google.com": "64.233.161.294",
  "mail.google.com": "216.58.209.197",
  "google.com": "216.58.210.142"
}

сам скрипт
#!/usr/bin/env python3

import os
import socket
import json

# JSON файл для хранения хостов и их IP адресов, формат ключ/значение
conf_file="conf.json"

with open(conf_file) as json_data_file:
    conf = json.load(json_data_file)

# Перебор всех хостов из файла конфигурации и опредление их IP адресов
for host, ip in conf.items():
    new_ip=socket.gethostbyname(host)

    # Если IP адреса отличаются, выводится предупреждение и сохранение нового IP адреса в файле конфигурации
    if (ip != new_ip):
        print ('[ERROR] {} IP mismatch: {} {}'.format(host,ip,new_ip))
        conf[host]=new_ip

# Печать всех сопоставлений хоста и IP адреса
for host, ip in conf.items():
    print('{} - {}'.format(host,ip))

# Пишем в файл, параметр ident дает нам человекочитаемый формат
with open(conf_file, "w") as json_data_file:
    json.dump(conf, json_data_file, indent=2)

Вывод

boakaa@DESKTOP-H6SSPL9:~/pythonProject$ python3 2.py
[ERROR] drive.google.com IP mismatch: 64.233.161.194 74.125.131.194
[ERROR] mail.google.com IP mismatch: 216.58.209.197 216.58.210.165
[ERROR] google.com IP mismatch: 216.58.210.142 216.58.209.174
drive.google.com - 74.125.131.194
mail.google.com - 216.58.210.165
google.com - 216.58.209.174

boakaa@DESKTOP-H6SSPL9:~/pythonProject$ python3 2.py
drive.google.com - 74.125.131.194
mail.google.com - 216.58.210.165
google.com - 216.58.209.174
```

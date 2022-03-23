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

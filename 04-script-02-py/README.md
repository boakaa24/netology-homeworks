1.
```
   a) ошибка разные типы переменных  
      TypeError: unsupported operand type(s) for +: 'int' and 'str'  
   b) a = '1'  
      b = '2'  
   c) a = 1  
      b = 2
```
2.is_change переменная не используется. Можно убрать  
  breake убрать, т.к. с ним выводится только одно извенение
  ```
  import os

bash_command = ["cd ~/pythonProject/sysadm-homeworks", "git status"]

result_os = os.popen(' && '.join(bash_command)).read()

print(result_os)
#is_change = False
for result in result_os.split('\n'):
    if result.find('modified') != -1:
        prepare_result = result.replace('\tmodified:   ', '')
        print(prepare_result)
#        break
```
3.

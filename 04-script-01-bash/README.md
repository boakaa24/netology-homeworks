1. c = a+b - так как указали текст а не переменные
   b = 1+3 - команда преобразовала вывела значения переменных, но не выполнила арифметическйо операции так как по умолчанию это строки 
   e = 3   - так как теперь за счет скобок мы дали команду на выполнение арифметической операции со значениями переменных
   
2. В первой строке не хватает закрывающей скобки  
   Завершить скрипт при успешной проверке можно   else exit  
   Задать интервал выполнения можно командой sleep 60 (1 минута)
```
 while (( 1 == 1 ))
    do
        curl https://localhost:4757
        if (($? != 0))
        then
            date >> curl.log
        else exit
        fi
        sleep 60
    done
 ```
 3.
```
#!/usr/bin/env bash
hosts=(192.168.0.1 173.194.222.113 87.250.250.242)
timeout=1
for i in {1..5}
do
echo $i
date >>hosts.log
    for h in ${hosts[@]}
    do
        curl -Is --connect-timeout $timeout $h:80 >/dev/null
        echo "    check" $h status=$? >>hosts.log
    done
done
```
4.
```
hosts=(192.168.0.1 173.194.222.113 87.250.250.242)
timeout=1
res=0
while (($res == 0))
do
    for h in ${hosts[@]}
    do
	curl -Is --connect-timeout $timeout $h:80 >/dev/null
	res=$?
	if (($res != 0))
	then
	    echo $h status=error connect >>error.log
       exit
	fi
    done
done

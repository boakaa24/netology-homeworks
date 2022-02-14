1.
![image](https://user-images.githubusercontent.com/95243483/153933086-53adc56e-efbf-412a-8f4d-caf7f29c4ad9.png)

![image](https://user-images.githubusercontent.com/95243483/153933749-e84b5261-b0a4-4f1e-a9fe-010b2c1af554.png)

2. LLDP 
``` 
sudo apt install lldpd
lldpctl
```
3. VLAN
```
apt-get install vlan
```
Настройки подынтерфейсов VLANов в Ubuntu указываются в файле /etc/network/interfaces
```
auto vlan1400
iface vlan1400 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        vlan_raw_device eth0
        
auto eth0.1400
        iface eth0.1400 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        vlan_raw_device eth0
```
4. Bonding  
mode=0 (balance-rr)  
При этом методе объединения трафик распределяется по принципу «карусели»: пакеты по очереди направляются на сетевые карты объединённого интерфейса  
mode=1 (active-backup)  
Когда используется этот метод, активен только один физический интерфейс, а остальные работают как резервные на случай отказа основного.  
mode=2 (balance-xor)  
В данном случае объединенный интерфейс определяет, через какую физическую сетевую карту отправить пакеты, в зависимости от MAC-адресов источника и получателя.  
mode=3 (broadcast) Широковещательный режим, все пакеты отправляются через каждый интерфейс. Имеет ограниченное применение, но обеспечивает значительную отказоустойчивость.  
mode=4 (802.3ad)  
Особый режим объединения. Для него требуется специально настраивать коммутатор, к которому подключен объединенный интерфейс. Реализует стандарты объединения каналов IEEE и   обеспечивает как увеличение пропускной способности, так и отказоустойчивость.  
mode=5 (balance-tlb)  
Распределение нагрузки при передаче. Входящий трафик обрабатывается в обычном режиме, а при передаче интерфейс определяется на основе данных о загруженности.  
mode=6 (balance-alb)  
Адаптивное распределение нагрузки. Аналогично предыдущему режиму, но с возможностью балансировать также входящую нагрузку.  
```
sudo nano /etc/network/interfaces
# The primary network interface
auto bond0
iface bond0 inet static
    address 192.168.1.150
    netmask 255.255.255.0    
    gateway 192.168.1.1
    dns-nameservers 192.168.1.1 8.8.8.8
    dns-search domain.local
        slaves eth0 eth1
        bond_mode 0
        bond-miimon 100
        bond_downdelay 200
        bound_updelay 200
 ```

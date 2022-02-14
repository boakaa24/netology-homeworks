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
```
4.

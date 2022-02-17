1.
```
route-views>sh ip route 176.59.38.222
Routing entry for 176.59.36.0/22
  Known via "bgp 6447", distance 20, metric 0
  Tag 6939, type external
  Last update from 64.71.137.241 3w5d ago
  Routing Descriptor Blocks:
  * 64.71.137.241, from 64.71.137.241, 3w5d ago
      Route metric is 0, traffic share count is 1
      AS Hops 2
      Route tag 6939
      MPLS label: none
```
```
route-views>sh bgp 176.59.38.222
BGP routing table entry for 176.59.36.0/22, version 565180
Paths: (23 available, best #20, table default)
  Not advertised to any peer
  Refresh Epoch 1
  3333 20764 12958, (aggregated by 12958 176.59.63.132)
    193.0.0.56 from 193.0.0.56 (193.0.0.56)
      Origin incomplete, localpref 100, valid, external, atomic-aggregate
      Community: 12958:1000 20764:1122 20764:1151 20764:1161 20764:1251 20764:1410 20764:1432 20764:3002 20764:3011 20764:3021 20764:3136 25478:1000 25478:4001
      path 7FE0902AFED0 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  701 1273 12389 12958, (aggregated by 12958 176.59.63.132)
    137.39.3.55 from 137.39.3.55 (137.39.3.55)
      Origin incomplete, localpref 100, valid, external, atomic-aggregate
      path 7FE0D343E528 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  53767 174 20764 12958, (aggregated by 12958 176.59.63.132)
    162.251.163.2 from 162.251.163.2 (162.251.162.3)
      Origin incomplete, localpref 100, valid, external, atomic-aggregate
      Community: 174:21101 174:22014 53767:5000
      path 7FDFFDE0B388 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  3549 3356 12389 12958, (aggregated by 12958 176.59.63.132)
    208.51.134.254 from 208.51.134.254 (67.16.168.191)
      Origin IGP, metric 0, localpref 100, valid, external, atomic-aggregate
      Community: 3356:2 3356:22 3356:100 3356:123 3356:501 3356:903 3356:2065 3549:2581 3549:30840 12958:1000
      path 7FE0D1292948 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  3356 12389 12958, (aggregated by 12958 176.59.63.132)
    4.68.4.46 from 4.68.4.46 (4.69.184.201)
      Origin IGP, metric 0, localpref 100, valid, external, atomic-aggregate
      Community: 3356:2 3356:22 3356:100 3356:123 3356:501 3356:903 3356:2065 12958:1000
      path 7FE0C3524050 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  8283 1299 12958, (aggregated by 12958 176.59.63.132)
    94.142.247.3 from 94.142.247.3 (94.142.247.3)
      Origin incomplete, metric 0, localpref 100, valid, external, atomic-aggregate
      Community: 1299:30000 8283:1 8283:101
      unknown transitive attribute: flag 0xE0 type 0x20 length 0x18
        value 0000 205B 0000 0000 0000 0001 0000 205B
              0000 0005 0000 0001
      path 7FE01E82A470 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  4901 6079 9002 9049 12958, (aggregated by 12958 176.59.63.132)
    162.250.137.254 from 162.250.137.254 (162.250.137.254)
      Origin IGP, localpref 100, valid, external, atomic-aggregate
      Community: 65000:10100 65000:10300 65000:10400
      path 7FE184610128 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  57866 9002 9049 12958, (aggregated by 12958 176.59.63.132)
    37.139.139.17 from 37.139.139.17 (37.139.139.17)
      Origin IGP, metric 0, localpref 100, valid, external, atomic-aggregate
      Community: 9002:0 9002:64667
      path 7FE1489A3658 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  852 3491 20485 20485 9049 12958, (aggregated by 12958 176.59.63.132)
    154.11.12.212 from 154.11.12.212 (96.1.209.43)
      Origin IGP, metric 0, localpref 100, valid, external, atomic-aggregate
      path 7FE17C124988 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  20912 3257 1299 12958, (aggregated by 12958 176.59.63.132)
    212.66.96.126 from 212.66.96.126 (212.66.96.126)
      Origin incomplete, localpref 100, valid, external, atomic-aggregate
      Community: 3257:8101 3257:30055 3257:50001 3257:53900 3257:53902 20912:65004
      path 7FE0C96BAC90 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  3303 50384 12958, (aggregated by 12958 176.59.63.132)
    217.192.89.50 from 217.192.89.50 (138.187.128.158)
      Origin IGP, localpref 100, valid, external, atomic-aggregate
      Community: 3303:1004 3303:1006 3303:1030 3303:1031 3303:3081 12958:1000 25478:1000 25478:1001 25478:4001 31210:50384 65005:10643
      path 7FE16EC99548 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  7018 1299 12958, (aggregated by 12958 176.59.63.132)
    12.0.1.63 from 12.0.1.63 (12.0.1.63)
      Origin incomplete, localpref 100, valid, external, atomic-aggregate
      Community: 7018:5000 7018:37232
      path 7FE15224B898 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  3561 3910 3356 12389 12958, (aggregated by 12958 176.59.63.132)
    206.24.210.80 from 206.24.210.80 (206.24.210.80)
      Origin IGP, localpref 100, valid, external, atomic-aggregate
      path 7FE147017270 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  1351 6939 12958, (aggregated by 12958 176.59.63.132)
    132.198.255.253 from 132.198.255.253 (132.198.255.253)
      Origin IGP, localpref 100, valid, external, atomic-aggregate
      path 7FE0EF188908 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  20130 6939 12958, (aggregated by 12958 176.59.63.132)
    140.192.8.16 from 140.192.8.16 (140.192.8.16)
      Origin IGP, localpref 100, valid, external, atomic-aggregate
      path 7FE162B25CD0 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  1221 4637 12389 12958, (aggregated by 12958 176.59.63.132)
    203.62.252.83 from 203.62.252.83 (203.62.252.83)
      Origin incomplete, localpref 100, valid, external, atomic-aggregate
      path 7FE12B27E230 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 2
  2497 12389 12958, (aggregated by 12958 176.59.63.132)
    202.232.0.2 from 202.232.0.2 (58.138.96.254)
      Origin incomplete, localpref 100, valid, external, atomic-aggregate
      path 7FE1725ADD88 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  101 3491 20485 20485 9049 12958, (aggregated by 12958 176.59.63.132)
    209.124.176.223 from 209.124.176.223 (209.124.176.223)
      Origin incomplete, localpref 100, valid, external, atomic-aggregate
      Community: 101:20300 101:22100 3491:300 3491:311 3491:9001 3491:9080 3491:9081 3491:9087 3491:62210 3491:62220 20485:10099
      path 7FE054B13800 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  49788 12552 12389 12958, (aggregated by 12958 176.59.63.132)
    91.218.184.60 from 91.218.184.60 (91.218.184.60)
      Origin incomplete, localpref 100, valid, external, atomic-aggregate
      Community: 12552:12000 12552:12100 12552:12101 12552:22000
      Extended Community: 0x43:100:1
      path 7FE021C75E00 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  6939 12958, (aggregated by 12958 176.59.63.132)
    64.71.137.241 from 64.71.137.241 (216.218.252.164)
      Origin IGP, localpref 100, valid, external, atomic-aggregate, best
      path 7FE132B1BE68 RPKI State not found
      rx pathid: 0, tx pathid: 0x0
  Refresh Epoch 1
  3257 1299 12958, (aggregated by 12958 176.59.63.132)
    89.149.178.10 from 89.149.178.10 (213.200.83.26)
      Origin incomplete, metric 10, localpref 100, valid, external, atomic-aggregate
      Community: 3257:8794 3257:30052 3257:50001 3257:54900 3257:54901
      path 7FE02ED5C9C0 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  19214 3257 1299 12958, (aggregated by 12958 176.59.63.132)
    208.74.64.40 from 208.74.64.40 (208.74.64.40)
      Origin incomplete, localpref 100, valid, external, atomic-aggregate
      Community: 3257:8108 3257:30391 3257:50002 3257:51200 3257:51203
      path 7FE0B1C67FD8 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  7660 2516 12389 12958, (aggregated by 12958 176.59.63.132)
    203.181.248.168 from 203.181.248.168 (203.181.248.168)
      Origin incomplete, localpref 100, valid, external, atomic-aggregate
      Community: 2516:1050 7660:9003
      path 7FE0BEE67160 RPKI State not found
      rx pathid: 0, tx pathid: 0
      ```
  2.
  ![image](https://user-images.githubusercontent.com/95243483/154533312-6a816b9b-eb25-43b0-af3c-737759bb558b.png)

3.

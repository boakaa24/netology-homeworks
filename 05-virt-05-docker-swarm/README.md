1.
- В случае, когда указан mode global, то сервис запустится на всех нодах, в случае с replication - только на тех нодах, на которых мы указали в конфиге.
- Алгоритм RAFT - алгоритм построен на распределенном консенсусе, то есть в единицу времени, как минимум две ноды участвуют, отправляют заявку на лидерство, тот кто первый ответил, то становится лидером. Дальше в работе ноды между собой посылают запросы, чтобы определить доступен ли лидер и отвечает ли он до сих пор самый первый, в случае, когда лидер не ответил в заданное время идет пересогласование по тому же принципу. попытался дать пояснения своими словами
- Overlay Network - распределенная сеть кластера, которая позволяет общаться контейнерам между собой на разных нодах, возможно шифрование трафика. docker engine в рамках такой сети, сам занимается маршрутизацией.
2.
![image](https://user-images.githubusercontent.com/95243483/169289792-4a51348d-b9d9-40c4-8498-40fd40706b24.png)
3.
![image](https://user-images.githubusercontent.com/95243483/169290061-248c89bd-6795-4700-ad72-a2f1297fcb48.png)

1. Сделанно.  
2. 
![image](https://user-images.githubusercontent.com/95243483/162024048-34635e55-685c-48a2-97fa-4c587328d270.png)

3.
![image](https://user-images.githubusercontent.com/95243483/162038722-9dfaca41-733a-4d44-a76e-2657d0f23889.png)
![image](https://user-images.githubusercontent.com/95243483/162038861-dc8e8ec8-b134-418f-a953-81304fd79a3d.png)
4.
![image](https://user-images.githubusercontent.com/95243483/162585574-6c46eb40-c00b-4893-89c5-f26a65bcbf46.png)
![image](https://user-images.githubusercontent.com/95243483/162585552-64d7e6be-d88f-4584-bd01-82413af72efe.png)
![image](https://user-images.githubusercontent.com/95243483/162585598-424ad098-4513-4a21-a4d7-ce366d62b6c2.png)

срок правда поставил 20 дней  
5.
![image](https://user-images.githubusercontent.com/95243483/162265066-a704541c-6886-400b-a8ba-8d4b788bf56d.png)
![image](https://user-images.githubusercontent.com/95243483/162265169-c675d750-2d58-4a83-99c9-ce3b9679d2d5.png)

6.
![image](https://user-images.githubusercontent.com/95243483/162494717-107c9a29-315b-4515-821a-d435d86b48a5.png)

7.
![image](https://user-images.githubusercontent.com/95243483/162585966-51a4b73f-a365-420e-9a51-6d17346ee138.png)
8.
![image](https://user-images.githubusercontent.com/95243483/162585783-ffb67b54-2fbb-4b8e-ab40-1733dfea530b.png)
![image](https://user-images.githubusercontent.com/95243483/162585804-a5c380bc-6eff-451c-9e53-a5b3782c66e7.png)
9.
```
#!/bin/bash

# Create cert
vault write -format=json pki/issue/example-dot-com \
    common_name="dev.example.com" \
    ttl="480h" > dev.example.com.crt

# save cert
cat dev.example.com.crt | jq -r .data.certificate > dev.crt
cat dev.example.com.crt | jq -r .data.private_key > dev.key

systemctl restart nginx
```
![image](https://user-images.githubusercontent.com/95243483/162587413-f148345f-afa5-408b-b5a4-da8704423ea8.png)

10.
![image](https://user-images.githubusercontent.com/95243483/162590534-393477f8-c49d-403b-8fab-82525c3a0182.png)
![image](https://user-images.githubusercontent.com/95243483/162590453-9dce14c0-a3f7-453c-8de4-609c61ae6fc5.png)

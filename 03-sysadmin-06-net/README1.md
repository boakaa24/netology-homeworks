1. 
```
HTTP/1.1 301 Moved Permanently
cache-control: no-cache, no-store, must-revalidate
location: https://stackoverflow.com/questions
x-request-guid: f8b267a6-eeaa-46f2-99cf-57092efc5cd8
feature-policy: microphone 'none'; speaker 'none'
content-security-policy: upgrade-insecure-requests; frame-ancestors 'self' https://stackexchange.com
Accept-Ranges: bytes
Date: Fri, 11 Feb 2022 18:12:52 GMT
Via: 1.1 varnish
Connection: close
X-Served-By: cache-fra19182-FRA
X-Cache: MISS
X-Cache-Hits: 0
X-Timer: S1644603172.262387,VS0,VE85
Vary: Fastly-SSL
X-DNS-Prefetch-Control: off
Set-Cookie: prov=8ac24e7f-c59d-6019-a93d-08cd44876ccb; domain=.stackoverflow.com; expires=Fri, 01-Jan-2055 00:00:00 GMT; path=/; HttpOnly

Connection closed by foreign host.
```
Код 301 означает, что контент перемещён и его новое расположение передано в параметре Location. Браузер, получив ответ 301 должен перейти на новое расположение.  
Так же 301 означает не просто "перемещено", а "перемещено навсегда". Браузер при повторном запросе изначального адреса может даже не обращаться к серверу, а сразу требовать   документ из нового местоположения  
2.
```
Request URL: http://stackoverflow.com/
Request Method: GET
Status Code: 307 Internal Redirect
Referrer Policy: strict-origin-when-cross-origin
Location: https://stackoverflow.com/
Non-Authoritative-Reason: HSTS
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.82 Safari/537.36
```
https://stats.g.doubleclick.net/j/collect?t=dc&aip=1&_r=3&v=1&_v=j96&tid=UA-108242619-1&cid=744015493.1638705365&jid=837816335&gjid=921661297&_gid=1598206914.1644484830&_u=SCCACEAAFAAAAC~&z=620643143

![image](https://user-images.githubusercontent.com/95243483/153649918-b446653e-3ff5-433e-b132-98095988d8d5.png)

3. 176.59.38.222  
4. Tele2 Russia Groups  
   AS12958  
5.
```
 sudo traceroute -An 8.8.8.8
[sudo] password for andrew:
traceroute: invalid option -- 'A'
Try 'traceroute --help' or 'traceroute --usage' for more information.
```
6.
![image](https://user-images.githubusercontent.com/95243483/153654764-ff477695-5dab-46e2-9532-a586711f959e.png)


 14. 74.125.244.132 

7. 
7.

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

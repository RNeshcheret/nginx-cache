# nginx-cache

NGINX setup

### Start docker

```sh
docker compose up
```

### Hit image 3 times

```sh
curl -I http://localhost/imgs/img1.jpeg

Responses
1 ==========
HTTP/1.1 200 OK
Server: nginx/1.27.1
Content-Type: text/plain
Content-Length: 8782
Connection: keep-alive
ETag: "66c050da-224e"
Accept-Ranges: bytes
X-Cache-Status: MISS

2 ==========
HTTP/1.1 200 OK
Server: nginx/1.27.1
Content-Type: text/plain
Content-Length: 8782
Connection: keep-alive
ETag: "66c050da-224e"
X-Cache-Status: MISS
Accept-Ranges: bytes

3 ==========
HTTP/1.1 200 OK
Server: nginx/1.27.1
Content-Type: text/plain
Content-Length: 8782
Connection: keep-alive
ETag: "66c050da-224e"
X-Cache-Status: HIT
Accept-Ranges: bytes
```

### Purge cache key

```sh
curl -I http://localhost/purge/imgs/img1.jpeg

HTTP/1.1 200 OK
Server: nginx/1.27.0
Content-Type: text/html
Content-Length: 156
Connection: keep-alive
X-Purged-Key: /imgs/img1.jpeg
```

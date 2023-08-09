# How Do We Setup BookStackApp?

1. **Server**: cdh16
2. **Pre-requirement:** 
    - create /data/bookstackapp, (lazy: chmod 777, better to create a docker user for this app)
    - create database bookstackapp on MySQL
3. **Run the docker cmd:**

```
docker run -d \
--name=bookstack \
-e PUID=1000 \
-e PGID=1000 \
-e TZ=EST \
-e APP_URL=http://10.71.220.16:6875 \
-e DB_HOST=10.71.220.16 \
-e DB_PORT=3306 \
-e DB_USER=bookstack \
-e DB_PASS='2wsx!QAZ' \
-e DB_DATABASE=bookstackapp \
-p 6875:80 \
-v /data/bookstackapp:/config \
--restart unless-stopped \
lscr.io/linuxserver/bookstack:v23.06.2-ls96
```
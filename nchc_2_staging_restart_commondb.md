# Restart CommonDB - nchc 2案 staging
## 上層
1. ssh to db node
```
ssh centos@10.168.60.15 # from undercloud
```
2. Restart MariaDB
```
docker restart mariadb
```
3. Set max_connection
```
docker exec -u root -it mariadb bash
mysql -u root -p
mysql > SET GLOBAL max_connections=10000;
mysql > quit;
```
## 下層
一次關閉一台
1. ssh to db node 
> 10.168.60.16
> 10.168.60.17
> 10.168.60.18
```
ssh centos@10.168.60.16
```
2. Stop MaraiaDB
```
systemctl restart mariadb
```
3. Start MariaDB 
依照剛才關閉的相反順序打開DB
```
systemctl restart mariadb
```

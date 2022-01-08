# MySQL

### Check which threads are running.

`SHOW PROCESSLIST` shows you which threads are running. You can also get this information from the `information_schema.PROCESSLIST` table or the `mysqladmin processlist` command. If you have the `PROCESS privilege`, you can see all threads. Otherwise, you can see only your own threads (that is, threads associated with the MariaDB (MySQL) account that you are using).

```mysql
SHOW FULL PROCESSLIST;
```

 If you do not use the `FULL` keyword, only the first 100 characters of each statement are shown in the Info field.

## Dumping data from a MySQL Docker container

Are you one of those who does not like to have `mysql-server` installed on your machine ?  Do you use **MySQL** in **Docker + MyCli** for your development environments ? Having any trouble dumping data ?

Here you go:

```bash

# Backup
docker exec CONTAINER /usr/bin/mysqldump -u root --password=root DATABASE > backup.sql

# Backup create only 
docker exec CONTAINER /usr/bin/mysqldump -u root --password=toor --no-data --compact polpdb | egrep -v "(^SET|^/\*\!)" | sed 's/ AUTO_INCREMENT=[0-9]*\b//'

# Restore
cat backup.sql | docker exec -i CONTAINER /usr/bin/mysql -u root --password=root DATABASE
```

## Dumping data with a MySQL Docker container

```shell
docker run -it mysql:5.7 /usr/bin/mysqldump  -h [MYSQL_HOST] -u [MYSQL_USER] -P 6612 --password=[MYSQL_PASSWORD]   [MYSQL_DATABASE] > backup.sql
```

# docker-phpmyadmin
phpMyadmin docker

### Pull latest phpmyadmin image from docker-hub
```
docker pull phpmyadmin/phpmyadmin:latest
```
#### Given that, already a MySQL container named "mysql_docker" is up and running, run below command to start phpmyadmin container linking with that MySQL container

```
docker run --name phpmyadmin -d --link mysql_docker:db -p 8081:80 phpmyadmin/phpmyadmin
```

### Set a user and password for phpmyadmin panel on MySQL docker container

```
docker exec -it mysql_docker bash
echo $MYSQL_ROOT_PASSWORD
mysql -u root -p

CREATE USER 'phpmyadmin'@'%' IDENTIFIED BY 'Str@ngP#&&W@!D';

GRANT ALL PRIVILEGES ON *.* TO 'phpmyadmin'@'%' WITH GRANT OPTION;

flush privileges;

exit
```

- Browse to <http://server_ip:8081> and use **phpmyadmin**/**Str@ngP#&&W@!D** as credentials to access phpmyadmin panel.

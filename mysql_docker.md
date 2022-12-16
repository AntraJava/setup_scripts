# mysql
docker run --name=mysql_new -d -p 3306:3306 mysql/mysql-server:8.0
* Get password
  `docker logs mysql_sep 2>&1 | grep GENERATED`
* copy the password from the output
* Login `docker exec -it mysql_sep mysql -uroot -p`
* Paste the password. (when you paste it, it won't show on the screen, make sure you copy/paste it right)
* Now you are in the mysql cli like this:`mysql>`
* **Don't forget the semicolon ";" when you copy the SQL queries below;**
* Change password: mysql> `ALTER USER 'root'@'localhost' IDENTIFIED BY 'aabbccdd';`
* Create new user `CREATE USER 'sep_user'@'%' IDENTIFIED WITH mysql_native_password BY 'aabbccdd';`
* Grant privileges `GRANT ALL PRIVILEGES ON *.* TO 'sep_user'@'%' WITH GRANT OPTION;`
* Flush the privileges `FLUSH PRIVILEGES;`
* Create a new database `create database sep_training;`
* Now we have a MySQL with
    - `sep_user/aabbccdd`
    - `localhost:3306`

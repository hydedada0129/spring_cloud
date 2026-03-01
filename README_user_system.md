# spring_cloud
1. create a docker mysql
2. docker mysql image name : dev-mysql
3. launch by ubuntu terminal: docker start dev-mysql
4. list the docker container: docker ps
5. check the mysql's port 3306: sudo lsof -i :3306
6. create a table : docker exec -it dev-mysql mysql -u root -p
7. enter mysql sql command for creating a table: create database userdb;
8. list out the schemas: show databases;
9. after created, use the table: use userdb;
10. sql command for creating table: create table user_info(....);
11. list out the table: show tables;
12. show the columns: describe user_info;

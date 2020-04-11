# php-app
Sample PHP Code which connects to mysql-server to get list of friends.

### use the below to create table and insert records

```
CREATE TABLE IF NOT EXISTS MyGuests (id INT AUTO_INCREMENT PRIMARY KEY, firstname VARCHAR(255) NOT NULL, lastname VARCHAR(255) NOT NULL )  ENGINE=INNODB;insert into MyGuests (firstname,lastname) VALUES ("Chandler","Bing");
insert into MyGuests (firstname,lastname) VALUES ("Rachel","Green");
insert into MyGuests (firstname,lastname) VALUES ("Monica","Geller");
insert into MyGuests (firstname,lastname) VALUES ("Dr. Ross","Geller");
insert into MyGuests (firstname,lastname) VALUES ("Joey","Tribbiani Jr.");
insert into MyGuests (firstname,lastname) VALUES ("Phoebe","Buffay");
insert into MyGuests (firstname,lastname) VALUES ("Chandler","Bing"); 
```
### To deploy it on openshift use the below commands
```
oc new-app --name mysql mysql MYSQL_USER=swapnil MYSQL_PASSWORD=redhat MYSQL_DATABASE=friends MYSQL_ROOT_PASSWORD=r00tpa55

oc new-app --name friends php:7.2~https://github.com/swapnil-linux/openshift-training.git --context-dir=php-friends MYSQL_USER=swapnil MYSQL_PASSWORD=redhat MYSQL_DATABASE=friends

oc expose svc friends

```
### wait for pods to come up and hit the url of your route
```
oc get pods
oc get route

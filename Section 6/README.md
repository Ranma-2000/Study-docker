# Assignment 1: Databases Upgrade with Named Volumes
Problem Description: 

## Oracle
Step 1: Login into oracle in docker

    docker login container-registry.oracle.com
  
Step 2: Pull Oracle DB image

    docker pull container-registry.oracle.com/database/standard
  
Step 3: Create ora_db_env.dat file

Step 4: Run Oracle DB Container

    docker container run -d --env-file ./Documents/ora_db_env.dat -p 1521:1521 --shm-size="4g" -v oracledb_volume:/var/lib/ora/v1 --name my_oracle container-registry.oracle.com/database/standard
  
Step 5: Install DBeaver or SQLPlus to check if DB works

Step 6: Connect to Oracle DB container using DBeaver
Get information from ora_db_env.dat

    Host: my.domain.com
    Port: 1521
    Database: OraDoc - SID
    Authentication: Oracale Database Native
    Username: sys - Role: SYSDBA
    Password: MyPasswd123
  
## MySQL
    
Step 1: Pull 2 versions of MySQL Database

    docker image pull mysql:8.0.31 mysql:5.7.40

Step 2: Create mysql_db_env.dat file 

Step 3: Create Docker volume

    docker volume create mysql_volume

Step 4: Run MySQL 5.7.40 container

    docker container run -v mysql_volume:/var/lib/mysql --env-file Documents/mysql_db_env.dat --name my_mysql -p 3306:3306 --network mysql_network --shm-size="3g" -d mysql:5.7.40 -h 127.0.0.1

Step 5: Connect to MySQL Server container from local machine using CMD

    mysql -h localhost -P 3306 --protocol=tcp -u root -p
    
or using DBeaver, get info from .dat file

    ServerHost: localhost - Port: 3306
    Username: root
    Password: 123456
    
Then, stop the old version container and run MySQL newer version container with named volume.

## DB2

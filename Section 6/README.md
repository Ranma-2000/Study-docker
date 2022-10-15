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

Step 5: Install DBeaver or SQLPlus

  

Step 6: Connect to Oracle DB container using DBeaver
Get information from ora_db_env.dat

  Host: my.domain.com
  Port: 1521
  Database: OraDoc - SID
  Authentication: Oracale Database Native
  Username: sys - Role: SYSDBA
  Password: MyPasswd123
  
## MariaDB


## DB2

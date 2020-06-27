# DO101-apps

Apps for the DO101 course.

## In order to check remote postgresql DB

(base) jmayo (troubleshoot) bin $ oc login --token=********** --server=https://api.ocp-eu2.prod.nextcle.com:6443
Logged into "https://api.ocp-eu2.prod.nextcle.com:6443" as "jomayma" using the token provided.

You have one project on this server: "jomayma-troubleshoot-app"

Using project "jomayma-troubleshoot-app".
(base) jmayo (troubleshoot) bin $ oc get pods
NAME                  READY   STATUS      RESTARTS   AGE
contacts-1-build      0/1     Error       0          39m
contacts-1-deploy     0/1     Completed   0          28m
contacts-2-build      0/1     Completed   0          31m
contacts-2-deploy     0/1     Completed   0          22m
contacts-3-build      0/1     Completed   0          21m
contacts-3-deploy     0/1     Completed   0          19m
contacts-4-deploy     0/1     Completed   0          14m
contacts-4-wkfpq      1/1     Running     0          14m
postgresql-1-deploy   0/1     Completed   0          43m
postgresql-1-qh896    1/1     Running     0          43m
(base) jmayo (troubleshoot) bin $ oc rsh postgresql-1-qh896
sh-4.2$ psql
psql (10.6)
Type "help" for help.

postgres=# \l
                                 List of databases
    Name    |  Owner   | Encoding |  Collate   |   Ctype    |   Access privileges   
------------+----------+----------+------------+------------+-----------------------
 contactsdb | userXDY  | UTF8     | en_US.utf8 | en_US.utf8 | 
 postgres   | postgres | UTF8     | en_US.utf8 | en_US.utf8 | 
 template0  | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +
            |          |          |            |            | postgres=CTc/postgres
 template1  | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +
            |          |          |            |            | postgres=CTc/postgres
(4 rows)

postgres-# \c contactsdb
You are now connected to database "contactsdb" as user "postgres".
contactsdb-# \dt+
                       List of relations
 Schema |   Name   | Type  |  Owner  |    Size    | Description 
--------+----------+-------+---------+------------+-------------
 public | contacts | table | userXDY | 8192 bytes | 
(1 row)

contactsdb-# 
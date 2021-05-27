# pgsetup
Just document hub

## Install PostgreSQL in Windows 10 from binary zip
Author: Worathan Boonwijit  
Date: May 28, 2021

### Step to install
1. Download binary installation file.  
Visit the PostgreSQL web site https://www.postgresql.org/ or visit this link https://www.enterprisedb.com/download-postgresql-binaries and then choose your binary that you want. In this tutorial use binary for Windows. In this time currently version of PostgreSQL is PostgreSQL 13.3

2. Unpack the binary   
Extract the binary file as you downloaded to the path that you want to install. In this document use "C:\\" then create two folder name "data" and "log" inside the "C:\\pgsql". Complete directory structure will look like this.
```
C:\
+-- pgsql
    +-- bin
    +-- data <--- Create new folder name "data"
    +-- doc
    +-- include
    +-- lib
    +-- log <--- Create new folder name "log"
    +-- pgAdmin 4
    +-- share
    +-- StackBuilder
    +-- symbols

```
>- The "data" directory contains the data files of your PostgreSQL installation.
>- The "log" directory contains the logs of your PostgreSQL installation.   

You have now finished the needed preparations and can move on to the next phase of the installation process.

3. Initial database   
The next step is to create a new PostgreSQL database cluster. You can do this by using the [initdb command](https://www.postgresql.org/docs/13/app-initdb.html) which is found from the POSTGRESQL_ROOT\bin directory ("C:\\pgsql\bin"). You can create the database cluster by running the following command from the bin directory of your PostgreSQL installation:   
Open command prompt with Administrator privilege and then type this command to initail postgres database.


```
initdb -U postgres -A password -E utf8 -W -D C:\pgsql\data
```
The command line parameters of the initdb command are described in following:   
```
-U postgres means that the superuser account of your database is called ‘postgres’.
-A password means that password authentication is used.
-E utf8 means that the default encoding will be UTF-8.
-W means that you will enter the superuser password manually.
-D POSTGRESQL_ROOT\data specifies the data directory of your PostgreSQL installation.
```
After you have successfully created the database cluster, your PostgreSQL installation is ready to be used. You can start and stop your database instance by using the following commands:

The database can be started by running the following command:
```
pg_ctl -D "C:/pgsql/data" -l "C:/pgsql/log/pgsql.log" start
```
The database can be stopped by running the following command:
```
pg_ctl -D "C:/pgsql/data" -l "C:/pgsql/log/pgsql.log" stop
```
If you want to run PostgreSQL as a service, you should run the following command:
```
pg_ctl register -N "postgresql" -U "NT AUTHORITY\NetworkService" -D "C:/pgsql/data" -w
```
After you have done this, you can start the service by using the Services panel.

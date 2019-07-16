# Installing Hive, Tez and using MariaDB as metastore

## Download and extract hive

    Download and extract hive from apache hive website. Download version that support your hadoop version. If hadoop is 3.x download 3.x version of hive else 2.x version of hive.

## Setup MariaDB

### To Install 

``` sudo pacman -S mariadb ```

``` sudo mysql_install_db --user=mysql --basedir=/usr --datadir=/var/lib/mysql ```

``` sudo systemctl enable mariadb ```

``` sudo systemctl start mariadb ```

``` sudo mysql_secure_installation ```

### Download and Install JDBC Connector

```wget https://downloads.mariadb.com/Connectors/java/connector-java-2.4.2/mariadb-java-client-2.4.2.jar```

Copy the jar to HIVE_HOME/lib folder

### Setup metastore

``` sudo su - ``` //if you have access issue, login as root and try

or follow 

https://stackoverflow.com/questions/41645309/mysql-error-access-denied-for-user-rootlocalhost


``` mysql -u root -p ```

``` create database metastore ```

``` use metastore ```

``` source /home/appuser/hive/scripts/metastore/upgrade/mysql/hive-schema-3.1.0.mysql.sql ```

``` CREATE USER 'hiveuser'@'%' IDENTIFIED BY 'hivepassword'; ``` 

```GRANT all on *.* to 'hiveuser'@localhost identified by 'hivepassword';```

```flush privileges;```

* Note replace hiveuser and hivepassword with actual one


* Note : (All commands can be used for mysql as well with slight changes)

## Setup Hive
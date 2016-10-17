#Phinger DB

Collection of phing targets for database manipulations

## Installation

1) Run `composer require phinger/db`  
2) Add  
```
<property file="{path-to-lib}/db.yml" override="false" />
<import file="{path-to-lib}/db.xml" />
```
to your build file  
3) Create overrides configuration file and import it __before__ importing configuration from the library in order to override library properties.  
4) Run `phing -l` if you want to list all available targets  
5) Use library targets  

### Demo

This demo will drop database 'my_database' if it exists and create it back.  

_{project-path}/my-conf.yml_
```
# Only these 3 settings will be overriden. You can override any
# setting in the same way
phinger:
  db:
    dbname:  my_database # override default database name ('acme')
    dbuser:  my_user     # override default database user ('root')
    dbpass:  my_password # override default database password ('')
```

_{project-path}/build.xml_
```
<?xml version="1.0" encoding="UTF-8" ?>

<project
        name="test"
        default="reset-db"
>
    <property file="./my-conf.yml" />
    
    <property file="{path-to-lib}/db.yml" override="false" />
    <import file="{path-to-lib}/db.xml" />
    
    <target
            name="reset-db"
            depends="phinger:db:drop-db,
                     phinger:db:create-db"
    />
</project>
```

## Targets
### Create database
`phinger:db:create-db`  
#### Properties / params (defaults):
* `phinger.db.dsn`       (mysql:host=127.0.0.1)  
* `phinger.db.dbname`    (acme)  
* `phinger.db.dbuser`    (root)  
* `phinger.db.dbpass`    ('')  
* `phinger.db.charset`   (utf8)  
* `phinger.db.collation` (utf8_general_ci)  
### Drop database
`phinger:db:drop-db`  
#### Properties / params (defaults):
* `phinger.db.dsn`       (mysql:host=127.0.0.1)
* `phinger.db.dbname`    (acme)
* `phinger.db.dbuser`    (root)
* `phinger.db.dbpass`    ('')
### Reset database  
`phinger:db:reset-db`
#### Properties / params (defaults):
* `phinger.db.dsn`       (mysql:host=127.0.0.1)
* `phinger.db.dbname`    (acme)
* `phinger.db.dbuser`    (root)
* `phinger.db.dbpass`    ('')
* `phinger.db.charset`   (utf8)
* `phinger.db.collation` (utf8_general_ci)
### Run sql file  
`phinger:db:run-file`  
#### Properties / params (defaults):
* `phinger.db.dsn`       (mysql:host=127.0.0.1)
* `phinger.db.dbuser`    (root)
* `phinger.db.dbpass`    ('')
* `phinger.db.dump_path` (./backup/sql/dump.sql)
### Run sql query  
`phinger:db:run-query`  
#### Properties / params (defaults):
* `phinger.db.dsn`    (mysql:host=127.0.0.1)
* `phinger.db.dbuser` (root)
* `phinger.db.dbpass` ('')
* `phinger.db.query`  (SELECT 0;)

## Usage demo

... TBD ...  

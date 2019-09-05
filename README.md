# wsp1-mysql
Intro till MYSQL

## Starta server

Kör igång Ubuntu(kör du redan linux så...)

kör

    sudo service mysql restart
    sudo service apache2 restart
  
  
Om apache2 bråkar pga. port 80.
Starta services / tjänster i Windows.
Stoppa branchcache och starta om apache2

## MYSQL

**setup**
Kör

    sudo mysql -u root
    
     grant all privileges on *.* to 'username'@'localhost' identified by 'password';

## Skapa vår databas

    CREATE DATABASE torsdag;
    USE torsdag;
    CREATE TABLE tweet (id INT UNSIGNED AUTO_INCREMENT, PRIMARY KEY(id)) ENGINE = innodb;
    ALTER TABLE tweet ADD body VARCHAR (140) NOT NULL;
    ALTER TABLE tweet ADD created_at TIMESTAMP NULL, ADD updated_at TIMESTAMP NULL;
    ALTER TABLE tweet ADD user_id INT UNSIGNED;
    CREATE INDEX user_id ON tweet (user_id);

    DESCRIBE tweet;
    +------------+------------------+------+-----+---------+----------------+
    | Field      | Type             | Null | Key | Default | Extra          |
    +------------+------------------+------+-----+---------+----------------+
    | id         | int(10) unsigned | NO   | PRI | NULL    | auto_increment |
    | body       | varchar(140)     | NO   |     | NULL    |                |
    | created_at | timestamp        | YES  |     | NULL    |                |
    | updated_at | timestamp        | YES  |     | NULL    |                |
    | user_id    | int(10) unsigned | NO   | MUL | NULL    |                |
    +------------+------------------+------+-----+---------+----------------+ 
    5 rows in set (0.00 sec)

    CREATE TABLE users (id INT UNSIGNED AUTO_INCREMENT, PRIMARY KEY(id)) ENGINE = innodb;
    ALTER TABLE users ADD name VARCHAR(32) NOT NULL;
    ALTER TABLE users ADD password VARCHAR(255) NOT NULL;
    ALTER TABLE users ADD email VARCHAR(255) NOT NULL UNIQUE;
    ALTER TABLE users ADD created_at TIMESTAMP NULL, ADD updated_at TIMESTAMP NULL;

    DESCRIBE users;
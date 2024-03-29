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
    +------------+------------------+------+-----+---------+----------------+
    | Field      | Type             | Null | Key | Default | Extra          |
    +------------+------------------+------+-----+---------+----------------+
    | id         | int(10) unsigned | NO   | PRI | NULL    | auto_increment |
    | name       | varchar(32)      | NO   |     | NULL    |                |
    | password   | varchar(255)     | NO   |     | NULL    |                |
    | created_at | timestamp        | YES  |     | NULL    |                |
    | updated_at | timestamp        | YES  |     | NULL    |                |
    | email      | varchar(255)     | NO   | UNI | NULL    |                |
    +------------+------------------+------+-----+---------+----------------+
    6 rows in set (0.00 sec)

## Skapa data i databasen

    INSERT INTO users (name, password, created_at, updated_at, email) VALUES ("username", "password", now(), now(), "username@test.se");
    
    INSERT INTO tweet (body, created_at, updated_at, user_id) VALUES ("Hello world", now(), now(), 1);

    SELECT tweet.*, users.name FROM tweet JOIN users ON tweet.user_id = users.id;

## Exportera databasen

    mysqldump -u USERNAME -p DATABASENAME > FILENAME.sql

## Importera databasen

Se först till att det finns en databas med det namn du ska importera till, i mysql

    create database DATABASENAME;

Sedan så går du ur mysql (exit) och kör från prompten

    mysql -u USERNAME -p DATABASENAME < FILENAME.sql

Starta sedan mysql och välj och kolla att din data har importerats. Vill du testa så ladda ned torsdag.sql från detta repo.

    cd
    cd code
    mkdir jensgit
    cd jensgit
    git clone https://github.com/jensnti/wsp1-mysql.git
    cd wsp1-mysql

Följ sedan instruktionera ovan för att importera. glhf :)

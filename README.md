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

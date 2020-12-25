### Servidor-AWS
#### Passo a passo para criar um servidor web na amazon AWS


#### Instale o Apache
-# sudo apt-get install apache2

-# sudo apache2ctl configtest

-# sudo nano /etc/apache2/apache2.conf

-# sudo apt-get update

---------------------------------------------

 #### Instale o PhP

-# sudo add-apt-repository ppa:ondrej/php

-# sudo apt-get install php libapache2-mod-php php-mysql php-dev php-pear

-# sudo systemctl restart apache2

-# sudo systemctl status apache2

-# php -m | grep mcrypt

-# sudo pecl install mcrypt-1.0.3

-# php -m | grep mcrypt

---------------------------------------------
#### Modifique o limite de Upload

Modifique o tamanho padrão de upload, pra não ter problema depois em subir arquivos grandes.

Abra o php.ini 

-# sudo -i
-# nano /etc/php/7.4/apache2/php.ini

##### Substitua esses:
- File_uploads = On
- max_execution_time = 30
- memory_limit = 128M
- post_max_size = 8M
- max_input_time = 60
-  max_input_vars = 1000
- upload_max_filesize = 2


##### Por esses:
+ file_uploads = On
+ max_execution_time = 300
+ memory_limit = 256M
+ post_max_size = 32M
+ max_input_time = 60
+ max_input_vars = 4440
+ upload_max_filesize = 16
 
 De um restart
 -# sudo systemctl restart apache2

#### Adicione o módulo mcrypt no arquivo de configuração do PHP, edite o arquivo usando o comando:

-# sudo nano /etc/php/7.4/cli/php.ini

Adicione a seguinte instrução ao arquivo php.ini:
-# extension=mcrypt.so

nota: utilize as teclas de atalho [CTRL] + [x] para sair, e confirme com a tecla [y] a alteração do arquivo e depois de um [Enter] para retornar a linha de comando.


Reinicie o servidor Apache utilize o seguinte comando:
-# sudo systemctl restart apache2

Altere a extensão padrão do Apache para PHP:
-# sudo nano /etc/apache2/mods-enabled/dir.conf

Altere a lista de prioridade conforme abaixo:

- DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
+ DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm

Reinicie o Apache
-# ~$ sudo systemctl restart apache2


Crie um arquivo de teste
-# ~$ sudo nano /var/www/html/index.php


Cole esse arquivo php dentro de index.php

<?php
// Mostra todas as informações, usa o padrão INFO_ALL
-# phpinfo();

//Mostra apenas informações dos módulos 
// phpinfo(8) mostra um resultado identico.
-# phpinfo(INFO_MODULES);
?>

--------------------------------------------------

#### Instale o Mcrypt no Servidor Apache no Linux
-# sudo apt install php7.4-dev

-# sudo apt-get install php libapache2-mod-php php-mysql php-dev php-pear

-# sudo apt -y install gcc make autoconf libc-dev pkg-config

-# sudo apt-get -y install o libmcrypt-dev


-# cd /usr/lib/php


-# sudo nano /etc/php/7.4/cli/conf.d/mcrypt.ini
coloque dentro do arquivo.

-# extension=/usr/lib/php/20190902/mcrypt.so


-# sudo nano /etc/php/7.4/apache2/conf.d/mcrypt.ini
coloque dentro do arquivo.

-# extension=/usr/lib/php/20190902/mcrypt.so


-# sudo systemctl restart apache2

-# php -m | grep mcrypt

---------------------------------------------

#### Instalando o PhpMyAdmin
 
 Atualize o Servidor Linux com o comando:
 
-# sudo apt-get update

-# sudo apt-get upgrade

Instale o PhpMyAdmin com o seguinte comando:
-# sudo apt-get install phpmyadmin apache2-utils

-# sudo php -v		

-# sudo apt-get install php-mbstring php7.4-mbstring

-# sudo systemctl restart apache2

-# clear

Insira as configurações do PhpMyAdmin no Apache
-# sudo nano /etc/apache2/apache2.conf

Procure por (#Include list of ports to listen on:)

adicione :

#Configurações do PhpMyAdmin

Insira a seguinte linha de comando no arquivo apache2.conf
Include /etc/phpmyadmin/apache.conf

-# sudo systemctl restart apache2

Dai você pode acessar o PhpMyAdmin pelo seu Ip/phpmyadmin

-------------------------------------------------------

#### Configurando sites em um Servidor Apache na AWS

-# cd /var

-#cd www

-# ls


-# sudo mkdir -p /var/www/meusite.com.br/public_html

-# sudo mkdir -p /var/www/meusite.com.br/public_html

-# sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/meusite.com.br.conf

-# sudo nano /etc/apache2/sites-available/meusite.com.br.conf

Abaixo de (#ServerName www.example.com) 
Adicione:

ServerName example.com.br
ServerAlias www.example.com.br

Substitua :

-ServerAdmin webmaster@localhost
-DocumentRoot /var/www/html

+ServerAdmin contato@jhonatanuss.dev (Seu E-mail)
+DocumentRoot /var/www/meusite.com.br/public_html

-# ls 

Veja se a pasta do seu domínio foi criada

-# sudo a2dissite 000-default

-# sudo a2ensite example.com.br

-# sudo a2enmod rewrite

-# sudo systemctl restart apache2

-# sudo systemctl status apache2

-# sudo chown -R www-data:www-data /var/www/meusite.com.br

-# sudo chmod -R 777 /var/www/meusite.com.br

-# ls

--------------------------------------------------------------

#### Instalando SSL

-# cd /var/www/

-# sudo apache2ctl configtest

-# sudo systemctl reload apache2

-# sudo certbot --apache

--------------------------------------------------------------

#### Configurando UFW Portas

-# sudo ufw enable

-# sudo ufw status

-# sudo ufw allow 'Apache Full'

-# sudo ufw delete allow 'Apache'

-# sudo ufw allow 22

-# sudo ufw allow 80

-# sudo ufw allow 443

-# sudo ufw allow 3306

-# sudo ufw status

--------------------------------------------------------------

	 

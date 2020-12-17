## Servidor-AWS
### Passo a passo para criar um servidor web AWS na amazon


----Instale o Apache------ 
# sudo apt-get install apache2

# sudo apache2ctl configtest

# sudo nano /etc/apache2/apache2.conf

# sudo apt-get update

----Instale o PhP------ 

# sudo add-apt-repository ppa:ondrej/php

# sudo apt-get install php libapache2-mod-php php-mysql php-dev php-pear

# sudo systemctl restart apache2

# sudo systemctl status apache2

# php -m | grep mcrypt

# sudo pecl install mcrypt-1.0.3

# php -m | grep mcrypt

Adicione o módulo mcrypt no arquivo de configuração do PHP, edite o arquivo usando o comando:
# sudo nano /etc/php/7.4/cli/php.ini


Adicione a seguinte instrução ao arquivo php.ini:
# extension=mcrypt.so

nota: utilize as teclas de atalho [CTRL] + [x] para sair, e confirme com a tecla [y] a alteração do arquivo e depois de um [Enter] para retornar a linha de comando.


Reinicie o servidor Apache utilize o seguinte comando:
# sudo systemctl restart apache2

Altere a extensão padrão do Apache para PHP:
# sudo nano /etc/apache2/mods-enabled/dir.conf

Altere a lista de prioridade conforme abaixo:

- DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
+ DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm

Reinicie o Apache
# ~$ sudo systemctl restart apache2


Crie um arquivo de teste
# ~$ sudo nano /var/www/html/index.php


Cole esse arquivo php dentro de index.php

<?php
// Mostra todas as informações, usa o padrão INFO_ALL
# phpinfo();

//Mostra apenas informações dos módulos 
// phpinfo(8) mostra um resultado identico.
# phpinfo(INFO_MODULES);
?>

--------------------------------------------------

Instale o Mcrypt no Servidor Apache no Linux
# sudo apt install php7.4-dev

# sudo apt-get install php libapache2-mod-php php-mysql php-dev php-pear

# sudo apt -y install gcc make autoconf libc-dev pkg-config

# sudo apt-get -y install o libmcrypt-dev


# cd /usr/lib/php


# sudo nano /etc/php/7.4/cli/conf.d/mcrypt.ini
coloque dentro do arquivo.
# extension=/usr/lib/php/20190902/mcrypt.so


# sudo nano /etc/php/7.4/apache2/conf.d/mcrypt.ini
coloque dentro do arquivo.
# extension=/usr/lib/php/20190902/mcrypt.so


# sudo systemctl restart apache2

# php -m | grep mcrypt

----------------------------------------------

Atualize o Servidor Linux com o comando:
~$ sudo apt-get update
~$ sudo apt-get upgrade

Instale o PhpMyAdmin com o seguinte comando:
~$ sudo apt-get install phpmyadmin apache2-utils

Veja qual é a versão do PHP:
~$ sudo php -v

Insira as configurações do PhpMyAdmin no Apache
~$ sudo nano /etc/apache2/apache2.conf

Insira a seguinte linha de comando no arquivo apache2.conf
Include /etc/phpmyadmin/apache.conf

Reinicie o Apache
~$ sudo systemctl restart apache2
------------------------------------------------

 Instalando o PhpMyAdmin
 
# sudo apt-get update

# sudo apt-get upgrade

# sudo apt-get install phpmyadmin apache2-utils

# php -v	

# sudo apt-get install php-mbstring php7.4-mbstring

# sudo systemctl restart apache2

# clear

# sudo nano /etc/apache2/apache2.conf

Procure por (#Include list of ports to listen on:)

adicione :

#Configurações do PhpMyAdmin
Include /etc/phpmyadmin/apache.conf

# sudo systemctl restart apache2

Dai você pode acessar o PhpMyAdmin pelo seu Ip/phpmyadmin

-------------------------------------------------------

Configurando sites em um Servidor Apache na AWS

# cd /var

#cd www

# ls


# sudo mkdir -p /var/www/meusite.com.br/public_html

# sudo mkdir -p /var/www/meusite.com.br/public_html

# sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/meusite.com.br.conf

# sudo nano /etc/apache2/sites-available/meusite.com.br.conf

Abaixo de (#ServerName www.example.com) 
Adicione:

ServerName example.com.br
ServerAlias www.example.com.br

Substitua :

-ServerAdmin webmaster@localhost
-DocumentRoot /var/www/html

+ServerAdmin contato@jhonatanuss.dev (Seu E-mail)
+DocumentRoot /var/www/meusite.com.br/public_html

# ls 
Veja se a pasta do seu domínio foi criada

# sudo a2ensite example.com.br

# sudo a2enmod rewrite

# sudo systemctl restart apache2

# sudo systemctl status apache2

# sudo chown -R www-data:www-data /var/www/meusite.com.br

# sudo chmod -R 777 /var/www/meusite.com.br

# ls
--------------------------------------------------------------
     ordens do Dns AWS    
     
     obs: Essa é a ordem correta Para que o DNS funcione corretamente no seu dominio
     
     .net
     .com
     .org
     .uk
	 

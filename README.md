# tutorialpkp
instalar terminator<br>
sudo su<br>
apt update<br>
apt install terminator<br>
-configurar aplicativos padrão Default applications - utilities - terminal<br>

instalar php 7.4<br>
sudo apt install software-properties-common<br>
sudo add-apt-repository ppa:ondrej/php<br>
sudo apt update<br>
sudo apt install php7.4<br>

sudo apt install php7.4-common php7.4-mysql php7.4-xml php7.4-xmlrpc php7.4-curl php7.4-gd php7.4-imagick php7.4-cli php7.4-dev php7.4-imap php7.4-mbstring php7.4-opcache php7.4-soap php7.4-zip php7.4-intl -y<br>

Instalar e configurar mariadb<br>
sudo apt install mariadb-server<br>
sudo mariadb<br>
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%' IDENTIFIED BY 'admin' WITH GRANT OPTION;<br>
quit<br>
exit<br>

instalar ferramentas complementares<br>
vscodium<br>
https://github.com/VSCodium/vscodium/releases<br>
.deb<br>
sudo apt install ./codium_1.81.1.23222_amd64.deb<br>
extensão Smarty Template Support<br>

baixar ojs versões<br>
https://pkp.sfu.ca/software/ojs/download/archive/<br>
verificar qual é a sua versão<br>

rodar página ojs<br>
php -S 0.0.0.0:8888<br>
http://0.0.0.0:8888/<br>

baixar php my admin<br>
https://www.phpmyadmin.net/downloads/<br>
php -S 0.0.0.0:7777<br>
http://0.0.0.0:7777/<br>

criar database mariadb<br>
mariadb -uadmin -padmin<br>
create database ojsaaa;<br>
show databases;<br>
quit<br>

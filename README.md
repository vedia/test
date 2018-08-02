# Ubuntu Kurulumunda İlk Yapılacaklar

## Genel Güncelleme İşlemleri
```
sudo apt update -y
sudo apt upgrade -y
```

## GIT Kurulumu
```
sudo apt install git -y
git config --global user.email "xxx@gmail.com"
git config --global user.name "ADINIZ SOYADINIZ"
```

## Apache Kurulumu
```
sudo apt install apache2
```

## PHP Kurulumu
```
sudo apt install php-pear php-fpm php-dev php-zip php-curl php-xmlrpc php-gd php-mysql php-mbstring php-xml libapache2-mod-php
```

## MaridDB Kurulumu
```
sudo apt install mariadb-server
```

## MaridDB Kurulum Sonrası Ayarları
```
sudo mysql -u root
  show databases;
  use mysql;
  update user set plugin='' where User='root';
  flush privileges;
  exit;

sudo mysql_secure_installation
```


### Servislerin Başlatılması
```
sudo service apache2 restart
sudo service mariadb restart
sudo systemctl enable mariadb
sudo systemctl enable apache2
```

## html dizini için yetkilendirme
```
sudo adduser $USER www-data
sudo chown -R $USER:www-data /var/www/html/
```

## Masaüzerine HTML klasörü kısayolunun açılması
```
cd ~/Masaüstü
ln -s /var/www/html/
```

## Adminer Programı Kurulumu
```
cd /var/www/html
mkdir adminer
cd adminer
wget -O index.php https://www.adminer.org/latest.php
```

## ATOM Editörü Kurulumu
```
sudo add-apt-repository ppa:webupd8team/atom
sudo apt update
sudo apt install atom
```

### Atom Eklentileri Kurulumu
```
Adres: [Eklenti Sayfası] (https://atom.io/packages/list?direction=desc&sort=stars)
#shift+ctrl+p
#Settings View:Install Packages and Themes
#veya: apm install PAKETADI
#apm install file-icons minimap pigments highlight-selected minimap-highlight-selected
#apm install atom-beautify project-manager autoclose-html highlight-line markdown-pdf
#apm install project-manager autoclose-html highlight-line markdown-pdf
#apm install linter linter-php color-picker intentions
```


## php.ini ayarları
```
sudo find /etc -name "php.ini"

sudo atom /etc/php/7.2/apache2/php.ini

display_startup_errors = On
display_errors         = On
upload_max_filesize    = 128M
upload_max_size        = 128M
post_max_size          = 128M
max_input_vars         = 5000
error_reporting        = E_ALL & ~E_DEPRECATED & ~E_STRICT & ~E_NOTICE & ~E_WARNING
mbstring.language          = Turkish
mbstring.internal_encoding = UTF-8
disable_functions          = exec,passthru,shell_exec,system,proc_open,popen,curl_exec,curl_multi_exec,parse_ini_file,show_source

sudo service apache2 restart
```

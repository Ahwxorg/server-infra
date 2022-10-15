### Install LibreX

```
doas apt install php php-fpm php-dom php-curl nginx

cd /var/www/html/librex
git clone https://github.com/hnhx/librex

cd librex
mv config.php.example config.php
mv opensearch.xml.example opensearch.xml

sed -i 's/http:\/\/localhost/https:\/\/search.ahwx.org/g' opensearch.xml

sudo systemctl enable --now php7.4-fpm nginx

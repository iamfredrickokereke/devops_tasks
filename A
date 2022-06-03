vi / etc/httpd/conf/httpd.conf 

Header set X-XSS-Protection "1; mode=block"

Header always append X-Frame-Options SAMEORIGIN

Header set X-Content-Type-Options nosniff


cat /etc/httpd/conf/httpd.conf  |grep Listen
cat /etc/httpd/conf/httpd.conf  |grep X
vi /var/www/html/index.html

cat /var/www/html/index.html

systemctl start httpd

systemctl status  httpd

curl http://localhost:8083
curl -i http://localhost:8083

Question: The Nautilus devops team got some requirements related to some Apache config changes. They need to setup some redirects for some URLs. There might be some more changes need to be done. Below you can find more details regarding that:

httpd is already installed on app server 2. Configure Apache to listen on port 5003.

Configure Apache to add some redirects as mentioned below:

a.) Redirect http://stapp02.stratos.xfusioncorp.com:<Port>/ to http://www.stapp02.stratos.xfusioncorp.com:<Port>/ i.e non www to www. This must be a permanent redirect i.e 301

b.) Redirect http://www.stapp02.stratos.xfusioncorp.com:<Port>/blog/ to http://www.stapp02.stratos.xfusioncorp.com:<Port>/news/. This must be a temporary redirect i.e 302.
  
  
  
  
  
  
  ## Solutions
  
  systemctl status httpd
vi /etc/httpd/conf/httpd.conf
vi /etc/httpd/conf.d/main.conf



<VirtualHost *:5004>

ServerName stapp02.stratos.xfusioncorp.com

Redirect 301 / http://www.stapp02.stratos.xfusioncorp.com:5004/

</VirtualHost>

 

<VirtualHost *:5004>

ServerName www.stapp02.stratos.xfusioncorp.com:5004/blog/

Redirect 302 /blog/ http://www.stapp02.stratos.xfusioncorp.com:5004/news/

</VirtualHost>

systemctl restart httpd
 service httpd status
curl localhost:3000

curl http://stapp02.stratos.xfusioncorp.com:5004/

curl http://www.stapp03.stratos.xfusioncorp.com:5004

curl http://www.stapp03.stratos.xfusioncorp.com:5004/blog/

curl http://www.stapp03.stratos.xfusioncorp.com:5004/news/

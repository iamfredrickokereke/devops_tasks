#Task one - Create a Linux User with non-interactive shell

sudo adduser user -s /sbin/nologin/
cut -d: -f1 /etc/passwd

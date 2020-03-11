Support Me by visit to indobatch.com
# Centos 6 
# install stunnel

yum install epel-release

yum update

yum install dropbear -y

yum install stunnel -y

# put dropbear config to 

nano /etc/pesan ( put anyting you want ) this just message if user login to your server

nano /etc/sysconfig/dropbear

# config dropbear

OPTIONS="-p 80 -p 109 -p 110 -p 445 -b /etc/pesan"

and save ctrl + x and y

# stunnel init config

put init config on https://raw.githubusercontent.com/FosterG4/stunnel/master/stunnel

put stunnel config to /etc/init.d/stunnel 

# add this config to /etc/stunnel/stunnel.conf

pid = /var/run/stunnel.pid

cert = /etc/stunnel/stunnel.pem

client = no

socket = a:SO_REUSEADDR=1

socket = l:TCP_NODELAY=1

socket = r:TCP_NODELAY=1

[dropbear]

connect = 127.0.0.1:22

accept = YOUR IP ADDRESS:443

# Create SSL Certificate Stunnel and put to /etc/stunnel/
# just run this command and automated copy key.pem and cert.pem to stunnel.pem on /etc/stunnel

openssl genrsa -out key.pem 2048

openssl req -new -x509 -key key.pem -out cert.pem -days 1095

cat key.pem cert.pem >> /etc/stunnel/stunnel.pem


# Restart stunnel and dropbear

/etc/init.d/stunnel restart

/etc/init.d/stunnel restart

#if failed check port on dropbear and stunnel are conflict change to not same port from dropbear and stunnel



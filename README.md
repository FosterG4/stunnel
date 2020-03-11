# stunnel
Stunnel /etc/init.d/stunnel config

put stunnel config to /etc/init.d/stunnel 
and /etc/init.d/stunnel restart

add this config to /etc/stunnel/stunnel.conf

pid = /var/run/stunnel.pid
cert = /etc/stunnel/stunnel.pem
client = no
socket = a:SO_REUSEADDR=1
socket = l:TCP_NODELAY=1
socket = r:TCP_NODELAY=1

[dropbear]
connect = 127.0.0.1:22
accept = YOUR IP ADDRESS:443

# CWP

## CWP fail to start

> Jul 02 09:44:05 www.home.kiwi cwpsrv[1995]: cwpsrv: [emerg] annot load
> certificate "/etc/pki/tls/certs/hostname.crt": BIO_new_file() failed
> (SSL: error:02001002:system library:fopen:No such file or
> directory:fopen('/etc/pki/tls/certs/hostname.crt','r') error:2006D080:
> 
> Jul 02 09:44:05 www.home.kiwi cwpsrv[1995]: cwpsrv:configuration file
> /usr/local/cwpsrv/conf/cwpsrv.conf test failed
> 
> Jul 02 09:44:05 www.home.kiwi systemd[1]: cwpsrv.service: control
> process exited, code=exited status=1
> 
> Jul 02 09:44:05 www.home.kiwi systemd[1]: Failed to start CentOS Web
> Panel service (daemon).

> #openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/pki/tls/private/hostname.key -out /etc/pki/tls/certs/hostname.crt
> #systemctl restart cwpsrv.service


<!--stackedit_data:
eyJoaXN0b3J5IjpbMjEwNzcxNTA1LC0xOTI3NjAwNjUyXX0=
-->
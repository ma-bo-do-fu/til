# デーモン化するときにこけた

'$sudo /etc/rc.d/init.d/httpd start'
Starting httpd (via systemctl):  Job for httpd.service failed because the control process exited with error code. See "systemctl status httpd.service" and "journalctl -xe" for details.
                                                           [FAILED]

'$systemctl status httpd.service'
● httpd.service - LSB: start and stop Apache HTTP Server
   Loaded: loaded (/etc/rc.d/init.d/httpd; bad; vendor preset: disabled)
   Active: failed (Result: exit-code) since Tue 2017-04-04 07:59:45 UTC; 1min 1s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 2869 ExecStart=/etc/rc.d/init.d/httpd start (code=exited, status=1/FAILURE)

# マルチドメインの設定
- httpd.confのNameVirtualHost *:80を有効化する  
- VirtualHostの設定を追記していく  
例)  
```
<VirtualHost *:80>
    ServerName www.sample1.net
    DocumentRoot /var/www/
    ServerAdmin sample@sample1.net
    ErrorLog /var/www/sample1.net/logs/error_log
    CustomLog /var/www/sample1.net/logs/access_log combined
</VirtualHost>
```

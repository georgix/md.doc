Squid proxy
----------------

## linux

### add diladele apt key
    wget -qO - http://packages.diladele.com/diladele_pub.asc | sudo apt-key add -

### add repo
    echo "deb http://squid48.diladele.com/ubuntu/ bionic main" > /etc/apt/sources.list.d/squid48.diladele.com.list

### update the apt cache
    apt-get update

### install 
    apt-get install squid-common
    apt-get install squid 
    apt-get install squidclient

### create spool ssl (root)
    /usr/lib/squid/security_file_certgen -c -s /var/spool/squid_ssldb -M 4MB
    chown -R proxy:proxy /var/spool/squid_ssldb/
    sudo mkdir /var/cache/squid
    sudo chown -R proxy:proxy /var/cache/squid

## Webproxy (Docker)


(https://github.com/wrouesnel/docker-squid4)
[webproxy github](https://github.com/diladele/squid-ubuntu)

[Docker doc](https://docs.diladele.com/docker/docker_windows_10/index.html)


## Other guide

(https://wiki.squid-cache.org/ConfigExamples)
(https://wiki.squid-cache.org/ConfigExamples/Intercept/DebianWithRedirectorAndReporting)
(http://roberts.bplaced.net/index.php/linux-guides/centos-6-guides/proxy-server/squid-transparent-proxy-http-https)

## Webproxy docker volumes
zhangjin@ubuntu:~$ sudo ls /media/fusion/Docker/volumes/
439fd4fd2b8f78d42129876a7c9865047888227e0e6521328066465134fdb6d9  b3b69bbed8c6ae969fd6cbf50fb1dddca89ff21fbf4dabe5b4d92dd7f9c1fba8
9718b97aa14abee92bf4c160ea5caf2ff9b4b7590a9fcf6122747b0546b13506  ca1d262ed31685db5a27e4e48c7af763e99711f10c7caeb9d84552b882c2aca7
995c2ac9007f06d6f4d2317d94d82fc64981c6aeeac110adb09c9aae11ae496d  cc5f525fabe541de0976ea227e78b4dc1dcf49ee4b81d24b755bd9f7fa842c41
9edea171bf7c5944d885fec2f9b7c5230c4fe4e0a39dd27a4e326f5011435ca7  fce6d78d8d7dc681a65e95e725724a514fde6cd4573e3b7345c336c837cec2fb
ab2c47c2ad69d21c22159aa72770e319e1a48f3d629cfc56c07934ec9fed4926  metadata.db
zhangjin@ubuntu:~$ sudo ls /media/fusion/Docker/volumes/9edea171bf7c5944d885fec2f9b7c5230c4fe4e0a39dd27a4e326f5011435ca7
_data
zhangjin@ubuntu:~$ sudo ls /media/fusion/Docker/volumes/9edea171bf7c5944d885fec2f9b7c5230c4fe4e0a39dd27a4e326f5011435ca7/_data
antivirus    console  frame        manage.py  pdf_generator_runner.py  safety  switch_db.py  test.py  upgrade.py  utils.py
automate.py  _domain  generate.py  node       reset_password.py        squid   sync_db.py    traffic  utility     www


zhangjin@ubuntu:~$ sudo ls /media/fusion/Docker/volumes/439fd4fd2b8f78d42129876a7c9865047888227e0e6521328066465134fdb6d9/_data
antivirus          blocked_page.html           config.json      diladele.pem  myca.pem  safety.bak  traffic       websafety.pem
antivirus.bak      blocked_safe_browsing.html  config.json.bak  license.pem   node      squid       traffic.bak
blocked_image.gif  bypass_partial.html         config.sqlite    myca.der      safety    squid.bak   version.json

zhangjin@ubuntu:~$ sudo ls /media/fusion/Docker/volumes/995c2ac9007f06d6f4d2317d94d82fc64981c6aeeac110adb09c9aae11ae496d/_data
cron_license.log  database.log       database.log.2.gz  error.log.1.gz  license.status  report.log.1.gz  websafety.version  wsmgrd.log.1.gz
cron_update.log   database.log.1.gz  error.log          error.log.2.gz  report.log      report.log.2.gz  wsmgrd.log         wsmgrd.log.2.gz

zhangjin@ubuntu:~$ sudo ls /media/fusion/Docker/volumes/9718b97aa14abee92bf4c160ea5caf2ff9b4b7590a9fcf6122747b0546b13506/_data
access.log  access.log.1  access.log.2.gz  cache.log  cache.log.1  cache.log.2.gz

zhangjin@ubuntu:~$ sudo ls /media/fusion/Docker/volumes/ab2c47c2ad69d21c22159aa72770e319e1a48f3d629cfc56c07934ec9fed4926/_data
config.dump.json  config.sqlite.default  monitor.sqlite.default  node.sqlite.default   report.json
config.sqlite     monitor.sqlite         node.sqlite             non_categorized.json

zhangjin@ubuntu:~$ sudo ls /media/fusion/Docker/volumes/b3b69bbed8c6ae969fd6cbf50fb1dddca89ff21fbf4dabe5b4d92dd7f9c1fba8/_data
conf.d  errorpage.css  squid.conf

zhangjin@ubuntu:~$ sudo ls /media/fusion/Docker/volumes/ca1d262ed31685db5a27e4e48c7af763e99711f10c7caeb9d84552b882c2aca7/_data
'Top Domains By Requests'  'Top Policies By Requests'  'Top Users By Requests'  'User Activities'  'User Search Queries'

zhangjin@ubuntu:~$ sudo ls /media/fusion/Docker/volumes/cc5f525fabe541de0976ea227e78b4dc1dcf49ee4b81d24b755bd9f7fa842c41/_data
cron  mail  squid  squid_ssldb

zhangjin@ubuntu:~$ sudo ls /media/fusion/Docker/volumes/fce6d78d8d7dc681a65e95e725724a514fde6cd4573e3b7345c336c837cec2fb/_data
adblock           adult           categories_custom    ctiru.bak       iwf           privacy           safe_browsing  youtube_cache
adblock.bak       categories      categories.download  ctiru.download  iwf.bak       privacy.bak       youtube        youtube.download
adblock.download  categories.bak  ctiru                files           iwf.download  privacy.download  youtube.bak

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU4OTM0MTQwXX0=
-->
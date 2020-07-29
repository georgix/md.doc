
    ssh -i "/home/zhangjin/.ssh/mumbai.pem" -p 443 ubuntu@35.154.222.243

    scp -i "/home/zhangjin/.ssh/mumbai.pem" -P 443 /etc/squid/squid.conf  ubuntu@35.154.222.243:/home/ubuntu
    scp -i "/home/zhangjin/.ssh/mumbai.pem" -P 443 -r /etc/squid/ssl  ubuntu@35.154.222.243:/home/ubuntu
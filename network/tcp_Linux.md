TCP
----------------

https://oxnz.github.io/2016/05/03/performance-tuning-networking/


## opened connection

netstat -tp

lsof -i -a -p `pidof firefox`

ss -nap | grep $(pidof firefox)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcyNjAxNjA1Nl19
-->
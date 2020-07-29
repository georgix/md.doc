Wireshark
------------------


## Linux

    sudo usermod -a -G wireshark $USER
    [Reboot Required]
    sudo chgrp wireshark /usr/bin/dumpcap
    sudo chmod 750 /usr/bin/dumpcap
    sudo setcap cap_net_raw,cap_net_admin=eip /usr/bin/dumpcap

    $ sudo getcap /usr/bin/dumpcap
       /usr/bin/dumpcap = cap_net_admin,cap_net_raw+eip

## Windows

Install winpcap if no interface found
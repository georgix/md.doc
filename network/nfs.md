NFS setup
-----------------

## windows 10 client

mount -o anon \\192.168.249.128\media\f E:

## linux server

NFS
---------------------

    sudo apt-get install nfs-kernel-server
    cat /etc/default/nfs-kernel-server
    sudo emacs /etc/exports
    cat /etc/exports
    # Example for NFSv2 and NFSv3:
    # /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
    /media/f           192.168.249.0/24(rw,sync,no_subtree_check)

    sudo exportfs -a
    sudo exportfs -v
    sudo mount 192.168.249.128:/media/f /media/f3
    sudo ufw status
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUzNDAwNTE4Nl19
-->
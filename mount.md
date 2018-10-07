# Mount
$> sudo mkdir nfsdata
$> sudo mount.nfs4 10.194.184.139:/mnt/tank/cours-virt2017-data /mnt/nfsdata
$> sudo mount.nfs4 -w 10.194.184.139:/mnt/tank/cours-virt2017-data /mnt/nfsdata
=> [root@m1 nfsdata]# ls
=> ls: reading directory .: Input/output error

$> sudo mount -t nfs4 -o nfsvers=4 10.194.184.139:/mnt/tank/cours-virt2017-data /mnt/nfsdata/
$> sudo mount -t nfs4 10.194.184.139:/mnt/tank/cours-virt2017-data /mnt/nfsdata/
$> sudo mount -t nfs4 -o nolock 10.194.184.139:/mnt/tank/cours-virt2017-data /mnt/nfsdata/
=> access denied by server while mounting 10.194.184.139:/mnt/tank/cours-virt2017-data
=> [root@m1 nfsdata]# ls
=> ls: reading directory .: Input/output error

# Unmount
$> umount -f -l /mnt/nfsdata

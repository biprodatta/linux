# linux

## java path setup:
```bash
echo $JAVA_HOME
export JAVA_HOME=/opt/java/bin
export PATH=$PATH:$JAVA_HOME
java -vesrion
pwd
cd /usr/bin/
ln -s java /opt/java/bin/java
ln -s /opt/java/bin/java java
java -version
```


## use of growpart command to increate aws ec2 volume

```bash
# For server 10.20.30.40:

[root@ip-10-20-30-40 ~]# lsblk
NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
xvda    202:0    0    25G  0 disk
└─xvda1 202:1    0    10G  0 part /
nvme0n1 259:0    0 442.4G  0 disk /mnt
[root@ip-10-20-30-40 ~]# df -khPT
Filesystem     Type   Size  Used Avail Use% Mounted on
/dev/xvda1     ext4   9.8G  6.1G  3.2G  66% /
tmpfs          tmpfs  7.5G     0  7.5G   0% /dev/shm
/dev/nvme0n1   ext3   436G  199M  414G   1% /mnt


[root@ip-10-20-30-40 ~]# growpart /dev/xvda 1
CHANGED: partition=1 start=2048 old: size=20962777 end=20964825 new: size=52418047,end=52420095
```

## Volume Mount for AWS Linux Server:
```bash
sudo file -s /dev/nvme1n1
mkfs -t ext4 /dev/nvme1n1
mkdir /sas
mount /dev/nvme1n1 /sas
lsblk
df -h
vi /etc/fstab
#ADD BELOW LINE
/dev/nvme1n1 /sas ext4  defaults,nofail 0 0
```

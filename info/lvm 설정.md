# LVM 설정
`fdisk -l`  
`fdisk /dev/vdb`  

# lvm2 설치
`yum install lvm2 -y`  

`pvcreate /dev/vdb1`  
`vgcreate datavg /dev/vdb1`  
`lvcreate -n datalv -l +100%FREE datavg`  

`mkfs.ext4 /dev/datavg/datalv`  
`mkdir /data`  
`mount /dev/datavg/datalv /data`  
`df -h`  

`vi /etc/fstab`  
```bash
/dev/datavg/datalv                      /data ext4 defaults 0 0
```  

# LVM 삭제
`umount /data`  
`vgremove datavg`  

`dmsetup remove /dev/datavg/*`  
`pvscan --cache`  

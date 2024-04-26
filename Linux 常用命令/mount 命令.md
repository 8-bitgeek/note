### 1. 以普通用户挂载

```shell
sudo mount -t minix -o umask=000 /dev/sda1 /mnt
```

### 2. 将一个目录挂载到另一个目录上

```shell
mount --bind old_dir new_dir                # 绑定
mount --move old_dir new_dir                # 取消绑定
```

### 3. 挂载 samba 分区

```shell
mount -t smbfs -o username=root,password=xxx,codepage=936,iocharset=gc2312 //192.168.192.1/share /mnt/share
```

### 4. 以用户可读写的形式自动挂载 exfat 格式的分区
```shell
sudo vi /etc/fstab
# 添加如下信息
/dev/sda1 /home/gldwolf/data exfat defaults,uid=1000,gid=1000 0 0
# 自动挂载
sudo mount -a
```

### 1. 以普通用户挂载

```shell
sudo mount -t minix -o umask=000 /dev/sda1 /mnt
sudo mount -t exfat -o uid=1000,gid=1000,rw /dev/sda1 /mnt/sda1
```

### 2. 将一个目录挂载到另一个目录上

```shell
mount --bind old_dir new_dir                # 绑定
mount --move old_dir new_dir                # 取消绑定
sudo umount new_dir
```

### 3. 以用户可读写的形式自动挂载 exfat 格式的分区
```shell
sudo vi /etc/fstab
# 添加如下信息
/dev/sda1 /home/gldwolf/data exfat defaults,uid=1000,gid=1000 0 0
# 自动挂载
sudo mount -a
```

### 4. 普通用户挂载 smaba 共享目录

```shell
sudo mount -t cifs -o username=user,password=pass,uid=1000,gid=1000,iocharset=utf8 //server/{share_name} {local_dir}
```
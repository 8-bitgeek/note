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


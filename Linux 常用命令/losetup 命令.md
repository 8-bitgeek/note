### 1. 查找空闲的 lo 设备

```shell
losetup -f 
```

### 2. 挂载整个硬盘文件到 lo 设备

```shell
sudo losetup /dev/loop1 rootimage        # 将硬盘文件 rootimage 挂载到 /dev/loop1 上
```

### 3. 此时可以用 fdisk 来查看这个硬盘文件情况

```shell
sudo fdisk /dev/loop1
```

### 4. 挂载硬盘文件的某个分区

``
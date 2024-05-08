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
# 输出示例如下:

```

### 4. 挂载硬盘文件的某个分区

```shell
# 将硬盘文件的第一个分区(偏移 512 字节)挂载到 /dev/loop1
sudo losetup -o 512 /dev/loop1 rootimage
```

### 5. 挂载 lo 设备到目录下

```shell
sudo mount /dev/loop1 /mnt/hda
```

### 6. 解除挂载

```shell
sudo umount /dev/loop1
sudo losetup -d /dev/loop1
```
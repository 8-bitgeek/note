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
############ 输出示例如下 ############
Command (m for help): x

Expert command (m for help): p
Disk /dev/loop0: 239.7 MiB, 251338752 bytes, 490896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device       Boot  Start    End Sectors Id Type                 Start-C/H/S End-C/H/S Attrs
/dev/loop0p1 *         1 132047  132047 81 Minix / old Linux          0/1/1 130/15/63    80
/dev/loop0p2      132048 264095  132048 81 Minix / old Linux        131/0/1 261/15/63
/dev/loop0p3      264096 396143  132048 81 Minix / old Linux        262/0/1 392/15/63
/dev/loop0p4      396144 478799   82656 82 Linux swap / Solaris     393/0/1 474/15/63
############ 以上为 fdisk 输入及输出 ############
# start = 1 则表示分区的起始扇区是 1 号扇区, 起始字节是 1 * 512 = 512
```

### 4. 挂载硬盘文件的某个分区

```shell
# 将硬盘文件的第一个分区(起始扇区是 1 号扇区, 见上面说明, 偏移 1 * 512 字节)挂载到 /dev/loop1
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
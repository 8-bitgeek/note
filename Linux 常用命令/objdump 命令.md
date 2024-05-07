## 1. 基本用法

```shell
objdump <option(s)> <file(s)>
```

常用的选项有:
- `-d` : 反汇编目标文件中的代码段, 显示二进制命令
- `-t`: 显示目标文件的符号表中的信息
- `-S`: 同时显示源代码(编译时需要指定 `-g` 选项)和反汇编代码
- `-r`: 显示重定位表
- `-x`: 显示所有 header 的信息
- `-h`: 显示所有 section header 中的 sections 信息
- `-g`: 显示目标文件的 debug 信息
- `-f`: 显示目标文件的文件头信息
### 2. 示例
#### 2.1 反汇编裸二进制文件

```shell
objdump -m i8086 -b binary -D bootsect
```
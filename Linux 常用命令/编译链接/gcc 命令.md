### 1. 基本用法

```shell
gcc -E -o hello.i hello.c               # 对 hello.c 进行预处理, 生成 hello.i 文件
gcc -S -o hello.s hello.i               # 对邓处理文件进行编译, 生成汇编文件
gcc -c -o hello.o hello.s               # 对汇编文件进行处理, 生成目标文件
gcc -o hello hello.o                    # 对目标文件进行链接, 生成可执行文件
gcc -o hello hello.c                    # 对源文件进行编译链接, 生成可执行文件
```
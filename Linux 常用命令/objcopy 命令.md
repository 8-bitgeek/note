## 1. 基本用法
```shell
objcopy [option(s)] <in_file> [out_file]
```

常用选项: 
- `-I bfdname`: 指定输入文件的 bfdname, 而不是由程序自动推断, 取值: elf32-little, elf32-big, 可用 [[objdump 命令]] -I 查看相应的信息
- `-O bfdname`: 指定输出文件的 bfdname
- `-F bfdname`: 指定输入/输出文件的 bfdname
- `-j sectionname`: 只将由 sectionname 指定的 section 拷贝到输出文件 
- `-R sectionname`: 去掉由 sectionname 指定的 section, 可以指定多次
- `-S, --strip-all`: 去掉源文件的符号信息和 relocation 信息
- `-g, --strip_debug`: 去掉源文件中的调试符号信息和相关的段. 对使用 -g 编译生成的可执行文件执行之后, 生成的结果几乎和不使用 -g 进行编译生成的可执行文件一样
- `-K symbolname`
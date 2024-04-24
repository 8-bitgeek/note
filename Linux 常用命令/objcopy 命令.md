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
- `-K symbolname`: 保留由 symbolname 指定的符号信息
- `-N symbolname`: 去掉由 symbolname 指定的符号信息
- `--set-start val`: 设定新文件的 start address
- `--change-start incr --adjust-start`: 调整 start address, 使其增加 incr
- `--change-address incr  --adjust-vma incr`: 调整所有 sections 的  LMA(linear memory address) 和 VMA(virtual memory address)
- `--change-section-address section{=,+,-}val --adjust-section-vma section{=,+,-}val`: 调整指定 section 的 LMA/VMA
- `--set-section-flags section=flag`: 指定 section 的 flag, flag 的取值可以是: alloc, contents, load, noload, readonly, code, data, rom, share, debug
- `--rename-section oldname=newname[,flags]`: 更改 section 的名
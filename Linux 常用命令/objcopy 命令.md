## 1. 基本用法
```shell
objcopy [option(s)] <in_file> [out_file]
```

常用选项: 
- `-I bfdname`: 指定输入文件的 bfdname
- `-O bfdname`: 指定输出文件的 bfdname
- `-R sectionname`: 只将指定的 section 拷贝到输出文件, 可以指定多次
- `-S, --strip-all`: 不从源文件中拷贝符号信息和 relocation 信息
- `-g, --strip_debug`: 不从源文件中拷贝调试符号和相关的段. 对使用 -g 编译生成的可执行文件执行之后, 生成的结果几乎和不使用 -g 进行编译
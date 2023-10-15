---
title: 1.06 判断文件/wt是否是字符文件并且将其复制到/root下   
type: docs
weight: 1
---

思路：
1、如何输入要处理的文件（要进行判断的文件），如果不输入文件会报错退出，如果输入的文件的格式不同会执行不同操作   
2、如何判断为字符文件，如果是字符文件，就将其移动到/dev下；如果不是，输出该文件不是字符文件  
3、如何定义不同操作，包括判断为字符文件，如果是字符文件，就将其移动到/dev下；如果不是，输出该文件不是字符文件  
4、变量处理，按照脚本规范原则，对于脚本中出现的特定数值一律通过全局变量来定义，对于特定的字符或字符串变量也一律用全局变量来定义   
5、汇总脚本   

下面一层层来解决   
1) 如何输入要处理的文件（要进行判断的文件），如果不输入文件会报错退出，如果输入的文件的格式不同会执行不同操作   
```bash
# 指定输入的目录方式为位置参数，同时如果不输入位置参数会报错退出
[ $ -ne 1 ] && { echo "Usage: $(basename $0) need one argument.";exit 1; }
file=$1
# 根据不同文件格式，执行不同的函数操作   
[[ ! $file == /* ]] && { File="/${file}";panduanfile1; } || panduanfile2

```   

2) 如何判断为字符文件，如果是字符文件，就将其移动到/dev下；如果不是，输出该文件不是字符文件   
`[ -c /wt ] && mv /wt /dev || echo "/wt is not a char file."`   

3) 如何定义不同操作，包括判断为字符文件，如果是字符文件，就将其移动到/dev下；如果不是，输出该文件不是字符文件   
操作1   
```bash
[ -c $file ] && mv $file /dev || echo "$file is not a char file."      
```   

操作2   
```bash
[ -c $File ] && mv $File /dev || echo "$File is not a char file."
```   

4) 变量处理，按照脚本规范原则，对于脚本中出现的特定数值一律通过全局变量来定义，对于特定的字符或字符串变量也一律用全局变量来定义    
dir="/dev"   

5) 汇总脚本   
```bash   
#!/bin/bash

panduanfile1 () {
[ -c $file ] && mv $file $dir || echo "$file is not a char file."      
}

panduanfile2 () {
[ -c $File ] && mv $File $dir || echo "$File is not a char file."
}

[ $# -ne 1 ] && { echo "Usage: $(basename $0) need one argument.";exit 1; }
file=$1
dir="/root"
[[ ! $file == /* ]] && { File="/${file}";panduanfile2; } || panduanfile1
```  


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell5">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell7">下一页➡️</a></p>
</div>
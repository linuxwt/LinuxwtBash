---
title: 1.01 找出某个目录下超过50M的文件    
type: docs
weight: 1
---

思路：
1、如何输入要处理的目录（要进行搜索的目录），如果不输入目录会报错退出，如果输入的目录格式不同会执行不同操作    
2、如何定义不同的操作，这里面包括：如何获取目标目录下的文件，如何获取符合要求的文件，如何输出符合要求的文件
3、变量处理，按照脚本规范原则，对于脚本中出现的特定数值一律通过全局变量来定义   
4、汇总脚本   


下面一层层来解决  
1）如何输入要处理的目录，如果不输入会报错退出，如果输入的目录格式不同执行不同的下一步   
```bash
# 指定输入的目录方式为位置参数，同时如果不输入位置参数会报错退出
[ $# -ne 1 ] && { echo "Usage: $(basename $0) needs one argument.";exit 1; }
dir=$1
# 根据不同目录格式，执行不同的函数操作   
[[ ! $dir == /* ]] && { Dir="/${dir}";finddir1; } || { finddir2; }
```   

2）如何定义不同的操作   
操作1   
```bash 
# 获取目标目录下所有文件   
du -sm $dir > dir.txt    
# 获取符合要求的文件   
# 输入目标目录下的所有文件
while read size file 
do
# 按照要求过滤出符合要求的文件并输出      
[ $size -gt 50 ] && echo -e "$size\t\t$file"
done <dir.txt  
```   
操作2  
```bash 
# 获取目标目录下所有文件   
du -sm $Dir > dir.txt    
# 获取符合要求的文件   
# 输入目标目录下的所有文件
while read size file 
do
# 按照要求过滤出符合要求的文件并输出      
[ $size -gt 50 ] && echo -e "$size\t\t$file"
done <dir.txt  
```   

3）使用全局变量处理特定数值   
declare -i size Size
Size=50

4）汇总脚本   
```bash
#!/bin/bash

finddir1 () {
du -sm $dir/* > dir.txt
while read size file
do
[ $size -gt $Size ] && echo -e "$size\t\t$file"
done <dir.txt
}

finddir2 () {
du -sm $Dir/* > dir.txt
while read size file
do
[ $size -gt $Size ] && echo -e "$size\t\t$file"
done <dir.txt
}

[ $# -ne 1 ] && { echo "Usage: $(basename $0) needs one argument.";exit 1; }
dir=$1
declare -i size Size
Size=50
[[ ! $dir == /* ]] && { Dir="/${dir}";finddir2;exit 0; } || { finddir1; }
>dir.txt
```   



<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell2">下一页➡️</a></p>
</div>
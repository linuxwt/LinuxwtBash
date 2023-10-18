---
title: 1.02 在/oldboy目录下通过随机小写10个字母加固定字符串oldboy批量创建10个html文件
type: docs
weight: 1
---

思路：
1、如何输入要处理的目录（要进行创建文件的目录），如果不输入目录会报错退出，如果输入的目录格式不同会执行不同操作    
2、如何生成随机的10个小写字母   
3、如何批量处理   
4、如何创建文件   
5、如何批量创建文件   
6、如何定义不同的操作，包括进入目标目录、创建符合条件的文件   
7、变量处理，按照脚本规范原则，对于脚本中出现的特定数值一律通过全局变量来定义    
8、汇总脚本       


下面一层层来解决  
1）如何输入要处理的目录，如果不输入会报错退出，如果输入的目录格式不同执行不同的下一步   
```bash
# 指定输入的目录方式为位置参数，同时如果不输入位置参数会报错退出
[ $# -ne 1 ] && { echo "Usage: $(basename $0) needs one argument.";exit 1; }
dir=$1
# 根据不同目录格式，执行不同的函数操作   
[[ ! $dir == /* ]] && { Dir="/${dir}";finddir1; } || { finddir2; }    
```   

2）如何生成随机的10个小写字母      
`tr -dc "a-z" < /dev/urandom | head -c 10`    

3) 如何批量处理   
```bash
i=1
while ((i < 11))
do
  ...  
done
```   

4) 如何创建文件   
`touch $(tr -dc "a-z" < /dev/urandom | head -c 10)_oldboy.html`   

5) 如何批量创建文件   
```bash
```bash
i=1
while ((i < 11))
do
  `touch $(tr -dc "a-z" < /dev/urandom | head -c 10)_oldboy.html` 
done
```  

6) 如何定义不同操作    
操作1   
```bash 
# 进入目标目录    
cd $dir     
# 批量创建符合条件的文件   
i=1
while ((i < 11))
do
  `touch $(tr -dc "a-z" < /dev/urandom | head -c 10)_oldboy.html` 
done
```    

操作2   
```bash   
# 进入目标目录    
cd $Dir        
# 批量创建符合条件的文件   
i=1
while ((i < 11))
do
  `touch $(tr -dc "a-z" < /dev/urandom | head -c 10)_oldboy.html` 
done
```    

7) 使用全局变量处理特定数值   
declare -i size
size=1   

8) 汇总脚本   
```bash
#!/bin/bash

createfile1 () {
cd $dir     
i=1
while ((i < 11))
do
  `touch $(tr -dc "a-z" < /dev/urandom | head -c 10)_oldboy.html` 
  i=$((i + 1))
done
}

createfile2 () {
cd $Dir
i=1
while ((i < 11))
do
  `touch $(tr -dc "a-z" < /dev/urandom | head -c 10)_oldboy.html`
  i=$((i + 1))
done
}

[ $# -ne 1 ] && { echo "Usage: $(basename $0) needs one argument.";exit 1; }
dir=$1
[[ ! $dir == /* ]] && { Dir="/${dir}";createfile2; } || { createfile1; }  

declare -i i
```   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell1">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell3">下一页➡️</a></p>
</div>
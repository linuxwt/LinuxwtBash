---
title: 1.03 将/oldboy目录下的文件名改为oldgirl,并且html改成大写
type: docs
weight: 1
---

思路：
1、如何输入要处理的目录（要进行创建文件的目录），如果不输入目录会报错退出，如果输入的目录格式不同会执行不同操作    
2、如何批量处理   
3、如何按照要求修改文件名   
4、如何批量按照要求修改文件名  
5、如何定义不同操作，包括进入目标目录，按照要求修改文件名    
6、汇总脚本   

下面一层层来解决   
1）如何输入要处理的目录（要进行创建文件的目录），如果不输入目录会报错退出，如果输入的目录格式不同会执行不同操作   
```bash
# 指定输入的目录方式为位置参数，同时如果不输入位置参数会报错退出
[ $# -ne 1 ] && { echo "Usage:$(basename $0) needs one argument.";exit 1; }
dir=$1
# 根据不同目录格式，执行不同的函数操作 
[[ !  $dir == /* ]] && { Dir=/${dir};changefile1; } || { changefile2; }   
```   

2) 如何批量处理   
```bash
for i in $(ls -l | awk '{print $9}' | awk -F '_' '{print $1}' | egrep -v '#|^$')
do
...
done   
```   

3) 如何按照要求修改文件名   
`mv ${i}_oldboy.html ${i}_oldgirl.HTML`   
**ps:这里的$i就是第2步中的i**   

4) 如何批量按照要求修改文件名   
```bash
for i in $(ls -l | awk '{print $9}' | awk -F '_' '{print $1}' | egrep -v '#|^$')
do
  mv ${i}_oldboy.html ${i}_oldgirl.HTML
done 
```    

5) 如何定义不同操作，包括进入目标目录，按照要求修改文件名     
操作1   
```bash 
# 进入目标目录    
cd $dir     
# 批量修改文件名     
for i in $(ls -l | awk '{print $9}' | awk -F '_' '{print $1}' | egrep -v '#|^$')
do
  mv ${i}_oldboy.html ${i}_oldgirl.HTML
done 
```    

操作2   
```bash   
# 进入目标目录    
cd $Dir        
# 批量修改文件名      
for i in $(ls -l | awk '{print $9}' | awk -F '_' '{print $1}' | egrep -v '#|^$')
do
  mv ${i}_oldboy.html ${i}_oldgirl.HTML
done 
```     

6）汇总脚本   
```bash
#!/bin/bash

changefile1 () {
cd $Dir        
for i in $(ls -l | awk '{print $9}' | awk -F '_' '{print $1}' | egrep -v '#|^$')
do
  mv ${i}_oldboy.html ${i}_oldgirl.HTML
done 
}

changefile2 () {
cd $dir
for i in $(ls -l | awk '{print $9}' | awk -F '_' '{print $1}' | egrep -v '#|^$')
do
  mv ${i}_oldboy.html ${i}_oldgirl.HTML
done
}

[ $# -ne 1 ] && { echo "Usage:$(basename $0) needs one argument.";exit 1; }
dir=$1
[[ ! $dir == /* ]] && { Dir="/${dir}";changefile1; } || { changefile2; }
```   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell2">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell4">下一页➡️</a></p>
</div>
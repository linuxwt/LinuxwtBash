---
title: 1.13 查找某个目录下的符号链接文件及其指向目标                     
type: docs
weight: 1
---

思路：   
1、如何输入要处理的目录（要进行创建文件的目录），如果不输入目录会报错退出，如果输入的目录格式不同会执行不同操作
2、如何查找当前目录的符号链接文件     
3、如何查找当前目录及其子目录下的符号链接文件     
4、如何找出获取符号链接的文件的目标路径   
5、如何批量获取所有符号链接文件的目标路径    
6、如何将符号链接文件与目标路径输出到一个文件便于查看 
7、如何定义不同的操作，这里面包括：如何查找当前目录及其子目录下的符号链接文件、如何批量获取所有符号链接文件的目标路径、如何将符号链接文件与目标路径输出到一个文件便于查看   
8、汇总脚本   

1) 如何输入要处理的目录（要进行创建文件的目录），如果不输入目录会报错退出，如果输入的目录格式不同会执行不同操作   
```bash
[ $# -ne 1 ] && { echo "Usage:$(basename $0) need onr arguments.";exit 1; }
dir=$1
[[ ! $dir == /* ]] && { $Dir="/${dir}";linkfind1;} || linkfind2 

2) 如何查找符号链接文件      
`ls -l | grep ^l`   

3) 如何查找当前目录及其子目录下的符号链接文件   
`find . -type l -print`   

4) 如何找出获取符号链接的文件的目标路径  
`readlink filename`   

5) 如何批量获取所有符号链接文件的目标路径    
```bash
for linkfile in $(find . -type l -print)
do
readlink $linkfile
done
```   

6) 如何将符号链接文件与目标路径输出到一个文件便于查看   
```bash
linkpath=$(readlink ${linkfile})      
echo "$linkfile $linkpath" >> jieguofile.txt   
```  

7) 如何定义不同的操作，这里面包括：如何查找当前目录及其子目录下的符号链接文件、如何批量获取所有符号链接文件的目标路径、如何将符号链接文件与目标路径输出到一个文件便于查看
操作1  
```bash
cd $dir
for linkfile in $(find . -type l -print)
do
linkpath=$(readlink ${linkfile})      
echo "$linkfile $linkpath" >> jieguofile.txt 
done
```   

操作2   
```bash
cd $Dir
for linkfile in $(find . -type l -print)
do
linkpath=$(readlink ${linkfile})      
echo "$linkfile $linkpath" >> jieguofile.txt 
done
```   
8) 汇总脚本   
```bash
#!/bin/bash

linkfind2 () {
for linkfile in $(find $dir -type l -print)
do
linkpath=$(readlink ${linkfile})      
echo "$linkfile $dir/$linkpath" 
done
}

linkfind1 () {
for linkfile in $(find $Dir -type l -print)
do
linkpath=$(readlink ${linkfile})      
echo "$linkfile $Dir/$linkpath" 
done
}

[ $# -ne 1 ] && { echo "Usage:$(basename $0) need one arguments.";exit 1; }
dir=$1
[[ ! $dir == /* ]] && { $Dir="/${dir}";linkfind1;} || linkfind2
```   

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell8">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell10">下一页➡️</a></p>
</div>
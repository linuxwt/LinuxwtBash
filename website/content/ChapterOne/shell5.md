---
title: 1.05 将当前目录大于5M的文件移动到/tmp 
type: docs
weight: 1
---

思路：
1、如何输入要处理的目录（要进行搜索的目录），如果不输入目录会报错退出，如果输入的目录格式不同会执行不同操作   
2、如何找出大于5M的文件,并将符合条件的文件名输出到结果文件   
3、如何读取结果文件中的文件名内容，并批量将其移动到/tmp下   
4、如何定义不同操作，包括找出大于5M文件，并将符合条件的文件名输出到结果文件；读取结果文件中的文件名内容，并批量将其移动到/tmp下  
5、变量处理，按照脚本规范原则，对于脚本中出现的特定数值一律通过全局变量来定义   
6、汇总脚本       

下面一层层来解决   
1) 如何输入要处理的目录（要进行搜索的目录），如果不输入目录会报错退出，如果输入的目录格式不同会执行不同操作  
```bash
# 指定输入的目录方式为位置参数，同时如果不输入位置参数会报错退出
[ $# -ne 1 ] && { echo "Usage: $(basename $0) need argument.";exit -1; }
dir=$1
# # 根据不同目录格式，执行不同的函数操作
[[ ! $dir == /* ]] && { Dir="/${dir}";yidongfile1; } || yidongfile2     
```   

2) 如何找出大于5M的文件，并将符合条件的文件名输出到结果文件   
```bash
# 输出所有文件大小和文件名到文件   
du -sm ./* > ./allfile.txt   
# 将符合条件的文件名输出到结果文件   
```bash
while read size file 
do
[ $size -gt 5 ] && echo $file >> jieguofile.txt
done <allfile.txt
```  

3) 如何读取结果文件中的文件名内容，并批量将其移动到/tmp下   
```bash
for jieguofile in $(cat ./jieguofile.txt)
do
mv $jieguofile /tmp
done
```   

4) 如何定义不同操作，包括找出大于5M文件，并将符合条件的文件名输出到结果文件；读取结果文件中的文件名内容，并批量将其移动到/tmp下   
操作1   
```bash   
# 进入目标目录  
cd $dir   
# 输出符所有文件大小和名字到文件   
du -sm ./* > ./allfile.txt
# 输出符合条件的文件名到结果文件
while read size file 
do
[ $size -gt 5 ] && echo $file >> jieguofile.txt
done <allfile.txt  
# 读取结果文件中的文件名内容，并批量将其移动到/tmp
for jieguofile in $(cat ./jieguofile.txt)
do
mv $jieguofile /tmp
done
# 清理临时文件   
echo "" > jieguofile.txt
echo "" > allfile.txt
```   

操作2   
```bash
# 进入目标目录  
cd $Dir   
# 输出符所有文件大小和名字到文件   
du -sm ./* > ./allfile.txt
# 输出符合条件的文件名到结果文件
while read size file 
do
[ $size -gt 5 ] && echo $file >> jieguofile.txt
done <allfile.txt  
# 读取结果文件中的文件名内容，并批量将其移动到/tmp
for jieguofile in $(cat ./jieguofile.txt)
do
mv $jieguofile /tmp
done
# 清理临时文件   
echo "" > jieguofile.txt
echo "" > allfile.txt
```   

5) 变量处理，按照脚本规范原则，对于脚本中出现的特定数值一律通过全局变量来定义   
declare -i Size size
Size=5

6) 汇总脚本   
```bash
#!/bin/bash

yidongfile1 () {
cd $Dir   
du -sm * > allfile.txt
while read size file 
do
[ "$size" -gt "$Size" ] &&  echo  $file >> jieguofile.txt
done < allfile.txt
for jieguofile in $(cat ./jieguofile.txt)
do
mv $jieguofile /tmp
done
echo "" > jieguofile.txt
echo "" > allfile.txt
}


yidongfile2 () {
cd $dir   
du -sm * > allfile.txt
while read size file 
do
[ "$size -gt $Size" ] && echo  $file >> jieguofile.txt
done < allfile.txt  
for jieguofile in $(cat ./jieguofile.txt)
do
mv $jieguofile /tmp
done
echo "" > jieguofile.txt
echo "" > allfile.txt
}


[ $# -ne 1 ] && { echo "Usage: $(basename $0) need argument.";exit -1; }
dir=$1
declare -i size Size
Size=5
[[ ! $dir == /* ]] && { Dir="/${dir}";yidongfile1; } || yidongfile2
```  

 


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell4">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell6">下一页➡️</a></p>
</div>
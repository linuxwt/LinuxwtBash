---
title: 1.02  重定向中的exec
type: docs
weight: 1
---

# exec重定向标准输入
```bash
#!/bin/bash

exec 6<&0 # 将stdin重定向到文件标识符6
exec < test.txt # 使用test.txt文件内容代替stdin，即后面的输入全部来自该文件
read a1 # 读取test.txt第一行
read a2 

echo "Following lines read from file"
echo "--------"
echo $a1
echo $a2

exec 0<&6 6<&-  # 从文件标识符6恢复stdin并关闭文件标识符6
echo "enter data"
read b1
echo "Input read from stdin"
echo "--------"
echo $b1

exit 0
```   
执行脚本输出   
```bash
Following lines read from file
--------
a
b
enter data
v
Input read from stdin
--------
v
```   

# exec重定向标准输出   
```bash
#!/bin/bash

exec 6>&1   # 将标准输出重定向到文件标识符6
exec > test1.txt # 输出到stdout的内容全部输出到文件test1.txt

echo "logfile"
date
echo "------------"

echo "output of \"ls -la\" command"
ls -la
echo "output of \"df\" command"
df

exec 1>&6 6>&- # 从文件标识符6恢复stdout并关闭文件标识符6

echo "stdout now restored to default"
echo "------------"
ls -la

exit 0
```   

# exec同时重定向标准输入标准输出   
```bash
#!/bin/bash

E_FILE_ACCESS=70
E_WRONG_ARGS=71

if [ ! -r "$1" ]
then
  echo "can not read from inputfile"
  echo "Usage :$0 input file"
 exit $E_FILE_ACCESS
fi

if [ -z "$2" ]
then
  echo "need to specify output file"
  echo "Usage: $0 inputfile outputfile"
  exit $E_WRONG_ARGS
fi

exec 4<&0
exec < $1

exec 6>&1
exec > $2

cat - | tr a-z A-Z # 从$1处获得输入并将其中小写字符转换成大写

exec 0<&4 4<&-
exec 1>&6 6>&-

echo "File \"$1\" written to \"$2\""
```   
这个脚本需要事先创建一个文件   
cat test2.txt   
```bash
a
b
c
```   
   
bash 3.sh test2.txt test3.txt   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterFive/Chongdingxiang1">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterSix">下一章➡️</a></p>
</div>

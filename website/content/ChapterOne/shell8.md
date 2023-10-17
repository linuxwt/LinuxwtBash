---
title: 1.08 统计/etc、/var、/usr目录中共有多少个一级子目录和文件      
type: docs
weight: 1
---

思路： 
1、如何获得目录下的文件    
2、如何批量获得目录下的文件   
3、如何区分获得的文件   
4、如何在区分后，统计文件数   
5、如何汇总文件数   
6、变量处理，按照脚本规范原则，对于脚本中出现的特定数值一律通过全局变量来定义，对于特定的字符或字符串变量也一律用全局变量来定义   
7、汇总脚本   

下面一层层来解决   
1) 如何获得目录下的文件   
```bash
ls /etc
ls /var
ls /usr
```  

2) 如何批量获得目录下的文件   
```bash
cd /etc
for etc_file in $(ls)
do
...
done   

cd /var
for var_file in $(ls)
do
...
done   

cd /usr
for usr_file in $(ls)
do
...
done   

```    

3) 如何区分获得的文件   
```bash
[ -d $etc_file ]

[ -d $var_file ]

[ -d $usr_file ]
```   

4) 如何在区分后，统计文件数    
```bash
etc_dir_num=0
etc_file_num=0
for etc_file in $(ls)
do
[ -d $etc_file ] && ((etc_dir_num+=1)) || ((etc_file_num+=1))
done

var_dir_num=0
var_file_num=0
cd /var
for var_file in $(ls)
do
[ -d $var_file ] && ((var_dir_num+=1)) || ((var_file_num+=1))   
done


usr_dir_num=0
usr_file_num=0
cd /usr
for usr_file in $(ls)
do
[ -d $usr_file ] && ((usr_dir_num+=1)) || ((usr_file_num+=1))
done
```   

5) 如何汇总文件数   
allfile=$((${$etc_file_num}+${var_file_num}+${usr_file_num}))   
alldir=$((${$etc_dir_num}+${var_dir_num}+${usr_dir_num}))

echo "There are ${allfile} files and ${alldir} dirs."   

6) 变量处理，按照脚本规范原则，对于脚本中出现的特定数值一律通过全局变量来定义，对于特定的字符或字符串变量也一律用全局变量来定义     
declare -i etc_dir_num var_dir_num usr_dir_num 
declare -i etc_file_num var_file_num usr_file_num   
etc_dir_num=0 
var_dir_num=0 
usr_dir_num=0
etc_file_num=0
var_file_num=0 
usr_file_num=0

7) 汇总脚本   
```bash
#!/bin/bash

jisuan () {
cd $dira
for a_file in $(ls)
do
[ -d $a_file ] && ((a_dir_num+=1)) || ((a_file_num+=1))
done

cd $dirb
for b_file in $(ls)
do
[ -d $b_file ] && ((b_dir_num+=1)) || ((b_file_num+=1))
done

cd $dirc
for c_file in $(ls)
do
[ -d $c_file ] && ((c_dir_num+=1)) || ((c_file_num+=1))
done
}

[ $# -ne 3 ] && { echo "Usage: $(basename $0) need three arguments.";exit -1; }

declare -i a_file_num b_file_num c_file_num  a_dir_num b_dir_num c_dir_num
a_dir_num=0 
b_dir_num=0 
c_dir_num=0
a_file_num=0
b_file_num=0 
c_file_num=0

dira=$1
dirb=$2
dirc=$3

jisuan

allfile=$((a_file_num+b_file_num+c_file_num))
alldir=$((a_dir_num+b_dir_num+c_dir_num))

echo "There are ${allfile} files and ${alldir} dirs."
```   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell6">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell8">下一页➡️</a></p>
</div>
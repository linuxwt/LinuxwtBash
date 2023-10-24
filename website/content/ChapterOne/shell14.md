---
title: 1.14 统计某个目录下的文件类和数量                       
type: docs
weight: 1
---

思路：   
1) 如何处理需要输入的目标目录，也就是要进行统计查询的对象   
2) 如何判断文件类型并获取文件类型关键字      
3) 如何根据将文件类型与文件数量进行挂钩   
4) 如何在将文件类型和文件数量挂钩后进行文件数量的计算   
5）如何批量处理文件   
6）如何输出文件类型和相应的数量   
7) 全局变量设置   
8) 汇总脚本   

下面一层层来解决   
1) 如何处理需要输入的目标目录，也就是要进行统计查询的对象    
```bash
[ $# -ne 1 ] && { echo "Usage: $(basename $0) need one argument"}   
dir=$1
```    

2) 如何判断文件类型并获取文件类型关键字     
`file -b filename | cut -d, -f1`   

3) 如何根据将文件类型与文件数量进行挂钩     
```bash
ftype=$(file -b filename | cut -d, -f1)   
# 利用关联数组来实现，文件类型作为数组索引，数组元素的值作为文件统计的数量   
# 先定义一个数组   
declare -A filearray  
```   

4) 如何在将文件类型和文件数量挂钩后进行文件数量的计算
`((filearray["$ftype"]+=1))`   

5) 如何批量处理文件   
```bash
while read line
do
ftype=$(file -b $line | cut -d, -f1)   
((filearray["$ftype"]+=1))
done < <(find $dir -type f -print)
```   

6) 如何输出文件类型和相应的数量    
```bash
for ftype in "${!filearray[@]}"
do
echo $ftype ${filearray["$ftype"]}
done
```   

7) 全局变量设置   
`declare -A filearray`   


8) 汇总脚本    
```bash
#!/bin/bash

findfile () {
while read line
do
ftype=$(file -b $line | cut -d, -f1)   
((filearray["$ftype"]+=1))
done < <(find $dir -type f -print)

for ftype in "${!filearray[@]}"
do
echo $ftype ${filearray["$ftype"]}
done
}

[ $# -ne 1 ] && { echo "Usage: $(basename $0) need one argument";exit -1; }   
dir=$1
declare -A filearray

findfile
```  
**ps:脚本中用文件类型ftype作数组索引，每个索引对应的值是该类型文件的数量**

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell8">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell10">下一页➡️</a></p>
</div>
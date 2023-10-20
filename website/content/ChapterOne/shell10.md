---
title: 1.10 查找某目录下大小一样的文件                 
type: docs
weight: 1
---

思路：  
1、如何按照大小对目录下的文件进行排序，这样大小一样的文件就会排列在相邻      
2、如何使用BEGIN语块读取文件的大小和文件名，并定义初始化变量      
3、如何在文件大小一样的时候进行文件名打印   
4、如何对比参照变量进行迭代      
5、如何将输出的文件名排序后输入到某个文件   
6、汇总脚本     


下面一层层来解决   
1) 如何按照大小对目录下的文件进行排序，这样大小一样的文件就会排列在相邻  
`ls -lS --time-style=long-iso`    

2) 如何使用BEGIN语块读取文件的大小和文件名，并定义初始化变量     

```bash
ls -lS --time-style=long-iso | awk 'BEGIN
{
# 第一个getline是用来丢弃第一行无用的文件数量值
getline;getline;
# 变量初始化
name1=$8;size=$5;
}
'
```   

3) 如何在文件大小一样的时候进行文件名打印   
```bash
{
name2=$8;
if ($size==$5) {
print name1;print name2;
};
}
```   

4) 如何对比参照变量进行迭代    
`size=$5;name1=name2;`   

5) 如何将输出的文件名排序后输入到某个文件    
`sort -u > duplicate_files`   

6) 汇总脚本   
```bash
#!/bin/bash

ls -lS --time-style=long-iso | awk 'BEGIN
{
getline;getline;
name1=$8;size=$5;
};

{
name2=$8;
if (size==$5) {
print name1;print name2;
};
size=$5;name1=name2;
}
}' | sort -u > duplicate_files
```   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell8">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell10">下一页➡️</a></p>
</div>
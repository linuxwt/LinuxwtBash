---
title: 1.16 比较两个文件之间的差异                             
type: docs
weight: 1
---

思路：   
1、如何输入待比较的文件           
2、何实现两文件之间差异,并将结果输出到结果文件      
3、如何设置全局变量
4、汇总脚本   

下面一层层来解决   
1) 如何输入带比较的文件   
```bash   
[ $# -me 2 ] && { echo "Usage: $0 need two arguments.";exit 1 }     
file1=$1
file2=$2          
```   

2) 如何实现两文件之间差异,并将结果输出到结果文件   
`diff -u $file1 $file2 > file.path`      

3) 如何设置全局变量   
略   

4) 汇总脚本   
```bash
#!/bin/bash

bijiaofile () {
diff -u $file1 $file2 > file.path  
}

xiufufile () {
# 利用差异结果文件可以将file1的内容补充成file2一样   
pathch -p1 $file1 < file.path
}

[ $# -me 2 ] && { echo "Usage: $0 need two arguments.";exit 1 }     
file1=$1
file2=$2 

bijiaofile
xiufufile
```    


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell8">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell10">下一页➡️</a></p>
</div>
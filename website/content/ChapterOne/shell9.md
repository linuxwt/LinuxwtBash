---
title: 1.09 输出两个文件A和B中相同的行、不同的行、A区别于B的行         
type: docs
weight: 1
---

思路：  
1、如何输入要处理的文件A和B   
2、如何排序现有的文件     
3、如何获取A和B文件中相同的行     
4、如何获取A和B中不同的行   
5、如何获取A中区别于B的行   
6、如何规整输出的文件内容，很明显会有制表符的存在   
7、汇总脚本   


下面一层层来解决   
1) 如何输入要处理的文件   
```bash
[ $# -ne 1 ] && { echo "Usage: $(basename $0) need two arguments.";exit -1; }   
A=$1
B=$2  
```   

2) 如何排序现有的文件   
`sort A -o A && sort B -o B`  

3) 如何获取A和B文件中相同的行   
# 输出两个文件的内容   
`comm A B`   
# 删除A和B的不同的内容        
`comm A B -1 -2`   

4) 如何获取A和B文件中不同的内容
`comm A B -3`   

5) 如何获取A区别于B的内容   
`comm A B -2 -3`

6) 如何规整输出的文件内容，很明显会有制表符的存在   
`comm A B -3 | tr -d '\t'`   

7) 汇总脚本  
```bash
#!/bin/bash

jiaoji  ()  {
comm  $A  $B  -1  -2
}

qiucha  ()  {
comm  $A  $B   -3 | tr -d '\t'
}

chaji  ()  {
comm  $A  $B  -2  -3
}


[ $# -ne 2 ] && { echo "Usage: $(basename $0) need two arguments.";exit -1; }   
A=$1
B=$2 
sort  $A  -o $A
sort  $B  -o  $B

jiaoji
echo "------"
qiucha
echo "------"
chaji
echo "------"
```  


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell8">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell10">下一页➡️</a></p>
</div>
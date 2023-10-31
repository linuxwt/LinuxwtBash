---
title: 1.20 获取文件的行数单词数字符数                                    
type: docs
weight: 1
---   

思路：   
1、如何获取文件行数   
2、如何获取文件单词数   
3、如何获取文件字符数   
4、如何获取文件中最长的一行的长度   
5、汇总脚本   


下面一层层来解决    

1) 如何获取文件行数   
`cat file | wc -l`   

2) 如何获取文件单词数   
`cat file | wc -w`   

3) 如何获取文件字符数   
`cat file | wc -c`   

4) 如何获取文件中最长一行的长度   
`wc file -L`   

5) 汇总脚本   
```bash
#!/bin/bash

wcfile1 () {
cat $file | wc -l
}

wcfile2 () {
cat $file | wc -w
}

wcfile3 () {
cat $file | wc -c
}

wcfile4 () {
wc $file -L
}

[ $# -ne 1 ] && { echo "Usage: $(basename $0) need one argument.";exit -1; }
file=$1   
wcfile1 
wcfile2
wcfile3
wcfile4
```   

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell19">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell21">下一页➡️</a></p>
</div>
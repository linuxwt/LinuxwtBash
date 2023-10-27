---
title: 1.18 列出当前路径的所有一级子目录                                 
type: docs
weight: 1
---   

思路：   
1、只列出目录名   
2、列出带属性的目录      
3、汇总脚本   

下面一层层来解决    

1) 只列出目录名   
`ls -d */`   

2) 只列出带属性的目录   
`ls -l | grep "^d"`    

3) 汇总脚本   
```bash
#!/bin/bash

dirls () {
ls -d */
ls -l | grep "^d"
}

[ $# -ne 1 ] && { echo "Usage:$(basename $0) need onr argument.";exit -1; }
dir=$1 
dirls
```   

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell8">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell10">下一页➡️</a></p>
</div>
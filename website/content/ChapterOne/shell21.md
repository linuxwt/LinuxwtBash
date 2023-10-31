---
title: 1.21 打印文件目录树                                    
type: docs
weight: 1
---   

思路：   
1、如何打印目录树   
2、如何打印符合需求的目录树   
3、如何打印不符合需求的目录树   
4、如何打印带有文件大小的目录树   
5、汇总脚本   

下面一层层来解决    
1) 如何打印目录树   
`tree /root/test`   

2) 如何打印符合需求的目录树   
`tree /root/test -P '*.sh'`   

3) 如何打印不符合需求的目录树   
`tree /root/test -I '*.sh'`   

4) 如何打印带有文件大小的目录树   
`tree -h /root/test`   

5) 汇总脚本   
```bash
#!/bin/bash

treefile1 () {
tree /root/test
}

treefile2 () {
tree /root/test -P '*.sh'
}

treefile3 () {
tree /root/test -I '*.sh'
}

treefile4 () {
tree -h /root/test
}

[ $# -ne 1 ] && { echo "Usage: $(basename $0) need one argument.";exit -1; }   
dir=$1
treefile1
treefile2
treefile3
treefile4
```   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell20">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterTwo">下一页➡️</a></p>
</div>
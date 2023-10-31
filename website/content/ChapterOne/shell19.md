---
title: 1.19 在多个路径进行多目录切换                                      
type: docs
weight: 1
---   

思路：   
1、如何实现多路径存储   
2、如何选择某个路径进行切换   
3、汇总脚本   

下面一层层来解决    
1) 如何实现多路径存储   
`pushd /var/www1`   
`pushd /var/www2`   
`pushd /var/www3`   
`dirs`   

2) 如何选择某个路径进行切换   
`pushd +2`   
可以通过命令dirs来查看路径列表，列表会按照0、1、2...的序列进行排序   

3) 汇总脚本   
```bash
#!/bin/bash

qiehuan () {
pushd /var/www1   
pushd /var/www2   
pushd /var/www3
}

qiehuan   
```   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell18">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell20">下一页➡️</a></p>
</div>
---
title: 1.17 打印文件的特定行数                               
type: docs
weight: 1
---

思路：   
1、打印文件的前10行   
2、打印文件的前5行   
3、打印除去最后5行之外的所有行   
4、打印文件的最后10行   
5、打印文件的最后5行   
6、打印文件出去前5行之外的所有行   
7、文件监视   
8、汇总脚本   


下面一层层来解决   
    
1) 打印文件的前10行   
`head file`   

2) 打印文件的前5行    
`head -n 5 file`   

3) 打印除去最后5行之外的所有行   
`head -n -5 file`   

4) 打印文件的最后10行   
`tail file`   

5) 打印文件的最后5行   
`tail -n 5 file`   

6) 打印文件出去前5行之外的所有行   
`tail -n +6 file`   

7) 文件监视   
`tail -f file`   

8) 汇总脚本   
```bash
#!/bin/bash

fileprint () {
head -n 5 file   
head -n -5 file
...
}

fileprint
```   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell8">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell10">下一页➡️</a></p>
</div>
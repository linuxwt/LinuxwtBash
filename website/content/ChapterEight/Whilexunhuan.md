---
title: 8.02 while循环      
type: docs
weight: 1
---    

# while循环   
```bash
#!/bin/bash

a=1
while [[ $a -lt 10 ]]
do
    echo $a
    a=$(expr $a + 1)
done
```     


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterEight/Forxunhuan">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterEight/Untilxunhuan">下一页➡️</a></p>
</div>

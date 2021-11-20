---
title: 8.03 until循环      
type: docs
weight: 1
---    

# until循环   
until循环与while相反   
```bash
#!/bin/bash

a=1
until [[ $a -gt 5 ]]
do
    echo $a
    a=$(expr $a +1)
done
```   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterEight/Whilexunhuan">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterNine">下一页➡️</a></p>
</div>

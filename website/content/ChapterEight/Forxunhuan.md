---
title: 8.01 for循环      
type: docs
weight: 1
---    

# for循环    
for循环有两种格式   
**传统shell格式**   
```bash
#!/bin/bash

for i [in words]
do
    ....
done
```   

words列别可以通过多种方式实现   
* 花括号   
```bash
#!/bin/bash

for i in {A..D}
do
    ...
done
```  

* 路径名    
```bash
#!/bin/bash

for i in dir*.txt
do
    ...
done
```   

* 命令替换    
```bash
#!/bin/bash

for i in $(seq 1 10)
do
    ...
done
```  

**C语言格式**   
```bash
#!/bin/bash

for (( i=0;i<10;i++ ))   
do
    echo $i
done
```   




<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterEight/">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterEight/Whilexunhuan">下一页➡️</a></p>
</div>

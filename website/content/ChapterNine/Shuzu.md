---
title: 9.01 数组      
type: docs
weight: 1
---    

# 数组赋值   
a=(1 2 3 4)整体赋值   
a[1]=100 单个元素赋值   


# 数组一般使用     
ex:   
```bash
#!/bin/bash

aray=(a b c d)
for i in ${array[@]}
do
    echo $i
done
```    

# 数组元素下标获取   
ex:   
```bash
#!/bin/bash

a=(1 2 3 4)   
for i in ${!a[@]}
do
    echo $i
done   
```   
执行脚本返回   
0
1
2
3   

# 获取数组元素值长度   
a[100]=foo   
echo ${#a[100]}返回3   
echo ${#a[@]}返回1   

# 数组末尾添加元素   
a=( a b c d)
a+=(d e f)   
echo ${a[@]}返回a b c d d e f   




<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterNine">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterNine">下一页➡️</a></p>
</div>
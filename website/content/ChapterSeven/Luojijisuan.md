---
title: 7.02 逻辑计算   
type: docs
weight: 1
---    

# 逻辑运算符   
bash里的逻辑运算符也可以认作是比较运算符，有以下   
>    
<   
==   
>=   
<=   
!=   
&&   
||   
expr?expr1:expr2（三元表达式，expr非0执行expr1,否则执行expr2）   

ex1   
```bash
#!/bin/bash

printf "a\ta**2\ta**3\n"   
printf "===\t===\t===\n"    
for ((a=0;a<11;a++))
do
    b=$((a**2))  
    c=$((a**3))
    printf "%d\t%d\t%d\n" $a $b $c
done
```   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterSeven/Suanshujisuan/">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterEight">下一页➡️</a></p>
</div>

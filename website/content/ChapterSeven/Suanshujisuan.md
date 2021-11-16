---
title: 7.01 算数计算   
type: docs
weight: 1
---    

# 简单计算   
bash中运算只针对整数，结果也均为整数    
简单运算就是常规计算，加、减、乘、除、求余(%)、乘方(**)   
ex1   
```bash
#!/bin/bash

for (( i=0;i<=5;i++))
do
    a=$(( i%5 ))
    if (( $a == 0 ));then
        printf "<%d>" $i
    else
        printf  "%d" $i
    fi
    echo
done
```   

# 赋值计算    
ex2   
```bash
#!/bin/bash

foo=
echo $foo
if (( foo=5 ));then 
    echo "ok."
fi
```   
这里的((foo=5))就是将5赋值给foo这个变量，注意必须加上(())才能生效，否则仍然按字符处理    
除了=以外还有以下   
+=   
-=   
/=   
%=  
*=  
++i  
--i    
i++   
i--    
但是注意，所有这些赋值运算都需要加上(())   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterSeven/">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterSix/Luojijisuan">下一页➡️</a></p>
</div>

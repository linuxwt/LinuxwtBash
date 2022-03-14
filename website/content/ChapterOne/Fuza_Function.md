---
title: 1.02 函数   
type: docs
weight: 1
---

# 带参数的函数  
exp1:   
```bash
#!/bin/bash

DEFAULT=default

func () 
{
    if [ -z "$1" ]
    then
        echo "Parameter #1 is zero length."
    else
        echo "Parameter #1 is \"$1\"."
    fi
    variable=${1:-$DEFAULT}
    echo "variable=$variable"
}

func  
echo $variable

func abc
echo $variable
```   
执行脚本输出   
```bash
Parameter #1 is zero length.
variable=default
default
Parameter #1 is abc   
variable=abc   
abc  
```  

# 函数如何使用传给脚本的命令行参数   
exp2:   
```bash
#!/bin/bash

func () 
{
    echo $1
}

func

func $1   
```   
执行脚本`bash exp.sh`   输出为空   
执行脚本`bash exp.sh abc` 输出为abc   

# 函数的返回状态值   
可以由return指定一个整数返回值，否则就由函数中执行的最后一条命令的退出状态来决定   
return可以选择带一个整数参数，这个整数可以作为函数的返回值返回给调用此函数的脚本，且赋值给$?    
下面使用一个例子来展示return的用法   





<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterOne/Function_DiaoYong">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterOne/">下一页➡️</a></p>
</div>
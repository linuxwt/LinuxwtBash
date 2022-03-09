---
title: 1.02 复杂函数   
type: docs
weight: 1
---

function_name $arg1 $arg2函数也可以处理传递的参数返回状态码，这有点类似于位置参数   

# 带参函数   
exp1:   
```bash
#!/bin/bash

DEFAULT=default

func1 ()
{
    if [ -z "$1" ]
    then
        echo "parameter #1 zero length."
    else
        echo  "parameter #1 is \"$1\"."
    fi

    variable=${1:-$DEFAULT}
    echo "variable=$variable"
}

echo 
echo "no parameter"   
func1
echo

echo "zero length parameter"
func1
echo

echo "One parameter"
func1 first
echo

exit0
```   
执行脚本输出    
```bash
no parameter
parameter #1 zero length.
variable=default

zero length parameter
parameter #1 zero length.
variable=default

One parameter
parameter #1 is "first".
variable=first
```   

# 处理位置参数的函数   
exp2:   
```bash
#!/bin/bash

func () 
{
    echo "$1"
}

echo "first call to function:no arg passed"

func

echo
echo "second call to function: arg passed"
func $1

exit 0
```   
不带位置参数执行脚本     
输出   
first call to function:no arg passed   
second call to function: arg passed    

带位置参数123执行脚本   
输出   
first call to function:no arg passed   
second call to function: arg passed    
123   



<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterOne/Function_DiaoYong">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterOne/">下一页➡️</a></p>
</div>
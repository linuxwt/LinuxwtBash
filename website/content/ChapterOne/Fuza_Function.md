---
title: 1.02 复杂函数   
type: docs
weight: 1
---

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



<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterOne/Function_DiaoYong">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterOne/">下一页➡️</a></p>
</div>
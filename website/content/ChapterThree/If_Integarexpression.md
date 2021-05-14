---
title: 3.03 if与整型表达式
type: docs
weight: 1
---  

# if与整型表达式   
判断一个变量是否是整型无法像文件表达式和字符串表达式有特定的选项来判断，需要使用正则来做匹配甚至需要结合一些数值计算来判断   

脚本说明   
```bash
#!/bin/bash

int=-10
if [ ${int} =~ ^-?[0-9]+$ ];then
    if [ ${int} -eq 0 ];then
        echo "${int} is equal 0."
    else
        if [ ${int} -lt 0 ];then
            echo "${int} is 负数。"
        else
            echo "${int} is 正数。"
        fi
    fi
    if [ $((int % 2)) -eq 0 ];then
        echo "${int} is a 偶数。"
    else
        echo "${int} is a 奇数。"
    fi
else
    echo "${int} is not a 整数。"
    exit 1
fi
```    

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterThree/If_Charexpression">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterThree/Fuhecommand">下一页➡️</a></p>
</div>

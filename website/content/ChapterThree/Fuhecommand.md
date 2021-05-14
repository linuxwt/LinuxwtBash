---
title: 3.04 复合命令
type: docs
weight: 1
---  

# [[]]    

[[]]也可以用来实现字符的匹配    
**使用=~实现**   

脚本说明 
```bash
#!/bin/bash

INT=-10
if [[ ${INT} =~ ^-?[0-9]+$ ]];then
    if [ ${INT} -eq 0 ];then
        echo "${INT} is equal 0."
    elif [ ${INT} -lt 0 ];then
        echo "${INT} is a 负数."
    else
        echo "${INT} is a 正数."
    fi
else
    echo "${INT} is not 数."
    exit 1
fi
```   

**使用==实现**   

脚本说明   
```bash
#!/bin/bash

FILE=wangteng.wangshu
if [[ ${FILE} == wangteng.* ]];then
    echo "${FILE} can be matched by wangteng.*"
fi
```   


# (())   
bash中，常用来操作整数，它里面的变量可以直接使用，并不需要像[[]]里面需要结合$进行展开   

脚本说明   
```bash
#!/bin/bash

INT=10
if [[ ${INT} =~ ^-?[0-9]+$ ]];then
    if [ $(( INT % 2 )) -eq 0 ];then
        echo "${INT} is a 偶数."
    else
        echo "${INT} is a 奇数."
    fi
else
    echo "${INT} is not a 数."
    exit 1
fi
```   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterThree/If_Charexpression">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterFour/">下一章➡️</a></p>
</div>

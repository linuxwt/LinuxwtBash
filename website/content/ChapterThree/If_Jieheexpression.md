---
title: 3.05 if与结合表达式
type: docs
weight: 1
---   

# if与结合表达式   
结合表达式常见类型有以下几种   
|表达式|含义|  
|:------|:------|   
|&&|与操作|   
||||或操作|   
|!|否操作|    


**&&**   
脚本说明   
```bash
#!/bin/bash

a=1
b=10
c=5
if [[ ${c} =~ ^-?[0-9]+$ ]];then
    if [[ ${c} -ge ${a} && ${c} -le ${b} ]];then
        echo "${c} is within $a and $b ."   
    else
        echo "${c} is out of range."
    fi
else
    echo "${c} is not a integer."
fi
```   

**||**   
脚本说明   
```bash
#!/bin/bash

a=1
b=10
c=5
if [[ ${c} =~ ^-?[0-9]+$ ]];then
    if [[ ${c} -lt ${a} || ${c} -gt ${b} ]];then
        echo "${c} is out of range."   
    else
        echo "${c} is within ${a} and ${b}."
    fi
else
    echo "${c} is not a integer."
fi
```   

**!**   
脚本说明   
```bash
#!/bin/bash

a=1
b=10
c=5
if [[ ${c} =~ ^-?[0-9]+$ ]];then
    if [[ ! \( ${c} -ge ${a} && ${c} -le ${b} \) ]];then
        echo "${c} is out of range."   
    else
        echo "${c} is within ${a} and ${b}."
    fi
else
    echo "${c} is not a integer."
fi
```   
> 在bash中>、<、( 、)与特殊含义，需要进行转义处理   




<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterThree/Fuhecommand">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterThree/If_Anotherway">下一页➡️</a></p>
</div>
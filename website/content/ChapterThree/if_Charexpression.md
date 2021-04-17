---
title: 3.02 if与字符串表达式
type: docs
weight: 1
---    

# if与字符串表达式   
字符串表达式常见的有以下几种   
|表达式|含义|  
|:------|:------|   
|-z|字符串长度为0|   
|-n|字符串长度不为0|   

脚本说明   
```bash
#!/bin/bash

answer="wangteng"   
if [ -z "${answer}" ];then
    echo "there is no answer."
    exit 1
fi
if [ "$answer" == "ab" ];then
    echo "the answer is incorrect"
elif [ "$answer" == "cd" ];then
    echo "the answer is also incorrect."
elif [ "$answer" == "wangteng" ];then
    echo "the answer is correct."
else
    echo "the answer is unknown."
fi
```  

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterThree/If_Fileexpression">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterThree/If_Integarexpression">下一页➡️</a></p>
</div>

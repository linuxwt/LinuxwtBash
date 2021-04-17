---
title: 3.01 if与文件表达式
type: docs
weight: 1
---   

# if与文件表达式    
文件表达式类型常见的有以下几种   
|表达式|含义|   
|:------|:------|   
|-f|常规文件|   
|-d|常规目录|   
|-r|可读文件|   
|-w|可写文件|   
|-x|可执行文件|   
|-e|是否存在|      

脚本说明     
```bash
#!/bin/bash

file=~/.bashrc   
if [ -e "$file" ];then
    if [ -f "$file" ];then
        echo "$file is a regular file."   
    fi   
    if [ -d "$file" ];then
        echo "$file is a directory."   
    fi
    if [ -r "$file" ];then
        echo "$file is readable."
    fi
    if [ -w "$file" ];then
        echo "$file is writable."
    fi
    if [ -x "$file" ];then
        echo "$file is executable."
    fi
else
    echo "$file does not exist."
    exit 1
fi
exit
```   

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterThree/">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterThree/If_Charexpression">下一页➡️</a></p>
</div>

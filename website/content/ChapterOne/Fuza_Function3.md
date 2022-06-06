---
title: 1.04 函数使用重定向标准输入   
type: docs
weight: 1
---

#  获取用户名   
exp1：   
```bash
#!/bin/bash

ARGCOUNT=1
E_ARGEXIT=65
FILE=/etc/passwd

if [ $# -ne $ARGCOUNT ]
then
  echo "Usage: `basename $0` USERNAME"
  exit $E_ARGEXIT
fi

find_user ()
{
  while read line
  do
    echo "$line" | awk -F ":" '{print $5}' | grep $1
  done  
}<$FILE

find_user $1
exit 0
```   

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterOne/Fuza_Function2">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterOne/Fuza_Function4">下一页➡️</a></p>
</div>
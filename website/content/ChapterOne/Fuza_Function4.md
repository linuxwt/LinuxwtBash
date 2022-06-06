---
title: 1.05 函数使用局部变量   
type: docs
weight: 1
---

# 局部变量与全局变量   
exp:
```bash
#!/bin/bash

func ()
{
  local a=5
  b=10
}

func

echo "\"a\" is equal $a"
echo "\"b\" is equal $b"
```   
执行脚本输出     
"a" is equal 
"b" is equal 10    

**ps:函数内没有使用local声明的变量均是全局变量**   

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterOne/Fuza_Function3">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterTwo">下一章➡️</a></p>
</div>
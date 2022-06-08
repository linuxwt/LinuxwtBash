---
title: 1.01  子shell里的变量
type: docs
weight: 1
---

```bash
#!/bin/bash

echo "outside subshell=$BASH_SUBSHELL"

var1=a

(
echo "inside subshell=$BASH_SUBSHELL"
var2=b
echo "from subshell \"var2\" = $var2"
echo "from subshell \"var1\" = $var1"
)

if [ -z "$var2" ]
then
  echo "var2 undefined in main body of shell"
else
  echo "var2 defined in main body of shell "
fi

echo "from main body 0f shell \"var2\" = $var2"

exit 0
```   
执行输出   
```bash
outside subshell=0
inside subshell=1
from subshell "var2" = b
from subshell "var1" = a
var2 undefined in main body of shell
from main body 0f shell "var2" = 
```   
小括号开启了子shell，子shell里定义的变量无法被该子shell所在的父shell(脚本运行时开启的shell)识别，可以当作局部变量     

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterFour">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterFour/Subshell2">下一页➡️</a></p>
</div>
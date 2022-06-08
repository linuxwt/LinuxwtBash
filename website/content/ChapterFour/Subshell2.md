---
title: 1.02  子shell对父shell影响
type: docs
weight: 1
---  

```bash
#!/bin/bash

FILE=.bashrc

for i in $(awk -F ':' '{print $6}' /etc/passwd)
do
  [ -d "$i" ] || continue #不存在家目录就跳过此次循环
  [ -r "$i" ] || continue #家目录不可读就跳过此次循环
  (cd $i;[ -e "$FILE" ] && more $FILE)
done

exit 0
```   
加入这个脚本在/root下。执行完这个脚本，退出脚本开启的shell后，父shell所在的位置仍然是/root，这说明**在子shell中的目录更改不会影响父shell**        


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterFour/Subshell1">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterFour/Subshell3">下一章➡️</a></p>
</div>
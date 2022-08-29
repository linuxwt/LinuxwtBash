---
title: 1.02 Heredocument与函数
type: docs
weight: 1
---

同一脚本中heredocument输出内容作为函数的输入使用   
```bash
#!/bin/bash


geo ()
{
read a
read b
read c
}

geo <<EOF
1
2
3
EOF

echo $a $b $c
exit 0
```

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterSix/Heredoc1">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterSix/Heredoc3">下一页➡️</a></p>
</div>

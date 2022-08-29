---
title: 1.03 Heredocument与变量
type: docs
weight: 1
---

heredocument的输出保存到变量中   
```bash
#!/bin/bash

a=$(
cat <<EOF
def
EOF
)

echo $a
```

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterSix/Heredoc2">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterSix/Heredoc4">下一页➡️</a></p>
</div>

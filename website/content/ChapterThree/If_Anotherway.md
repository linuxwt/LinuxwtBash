---
title: 3.06 if的简易写法   
type: docs
weight: 1
---   

# if的简易写法   

脚本说明   
```bash
#!/bin/bash
   
[ -d /temp ] || mkdir /temp ## 不存在就创建   
[ -d /temp ] && cd /temp    ## 存在就进入 
```   

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterThree/If_Jieheexpression">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterFour/">下一章➡️</a></p>
</div>

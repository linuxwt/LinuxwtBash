---
title: 1.03  子shell里的串行处理   
type: docs
weight: 1
---

```bash
#!/bin/bash

(cat list1 list2 list3 | sort | uniq > list123) &
(cat list4 list5 list6 | sort | uniq > list456) &

wait # 子shell执行王之前不会执行下面的命令   

diff list123 list456
```   
子shell里也可以串行执行命令      


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterFour/Subshell2">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterThree">下一章➡️</a></p>
</div>
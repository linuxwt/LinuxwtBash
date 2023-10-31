---
title: 1.12 批量生成空白文件                  
type: docs
weight: 1
---

思路：  
1、如何生成空白文件   
2、如何批量操作   
3、汇总脚本   

1) 如何生成空白文件    
`touch filename`   

2) 如何批量操作   
```bash
for name in {1..100}
do
...
done
```    

3) 汇总脚本   
```bash
for name in {1..100}
do
touch ${name}.txt
done   
```   

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell11">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell13">下一页➡️</a></p>
</div>
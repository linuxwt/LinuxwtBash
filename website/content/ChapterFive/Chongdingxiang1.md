---
title: 1.01  常规重定向
type: docs
weight: 1
---

|重定向式子|作用|
|:---:|:---:|   
|1>file|重定向stdout到file|
|2>file|重定向stderr到file|
|0>file|重定向stdin到file|
|&>file|重定向stdout和stderr到file|
|2>&1|重定向stderr到stdout|
|i>&j|指向i文件的所有输出发送到j中|
|>&j|默认重定向描述符1的输出发送到j中|
|[i]<>file|分配文件描述符i给file|
|\||管道|
|n<&-|关闭输入文件标识符n|
|n>&-|关闭输出文件标识符n|


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterFive">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterFive/Chongdingxiang2">下一页➡️</a></p>
</div>
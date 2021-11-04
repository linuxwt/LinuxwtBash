---
title: 6.01 空变量展开  
type: docs
weight: 1
---    

# ${parameter:-word}   

ex1:   
foo=
echo ${foo:-"hahaha"}   
输出的结果是 hahaha   

ex2:  
foo=tengwang
echo ${foo:-"hahaha"}   
输出的结果是 tengwang   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterSix/">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/NotNullargs/">下一章➡️</a></p>
</div>




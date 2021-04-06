---
title: 2.03 中括号
type: docs
weight: 1
---     

# 结合^使用    

`grep -h '[^wt]zip file1'`   
输出文件file1中不包含wzip或tzip的文本行   

`grep -h '^[wt]zip' file1`  
输出文件file1中包含wzip或tzip的文本行    

`grep -h '[A-Z]' file1`   
输出文件file1中包含字母的文本行   

`grep -h '[-AZ]' file1`   
输出文件file1中包含连字符或字母A或字母Z的文本行    

>在中括号中使用其他符号会产生与其初始意义完全不同的意思，比如^在括号内开头则表示否定意义，而-在A-Z中则表示一个范围   

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterTwo/Regular_Mao">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterTwo/Regular_Jt">下一页➡️</a></p>
</div>
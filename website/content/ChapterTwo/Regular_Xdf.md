---
title: 2.05 限定符   
type: docs
weight: 1
---    

# 限定符？   
`echo "123 4567890" | grep -Eh '\(?[0-9][0-9][0-9]\)? [0-9][0-9][0-9][0-9][0-9][0-9][0-9]$'`      
通过grep使用正则匹配echo打印的内容然后将内容输出，可以使用echo $?来判断输出的正确与否，该过滤可以判定echo打印的内容是否为电话号码       
？匹配前面的子表达式0次或1次     

# 限定符*   
`echo "Iam am wangteng." | grep -Eh '[[:upper:][:lower:] [:lower:] [:lower:]]*\.'`   
通过grep使用正则匹配echo打印的内容然后将内容输出，可以使用echo $?来判断输出的正确与否
*匹配前面的子表达式0次或多次，或者也可以说时匹配0个或多个元素       

# 限定符+   
`echo "This that" | grep -Eh '^([[:alpha:]]+ ?)+$'`  
这个过滤过程可以这样理解：   
* [:alpha:]]+ ?表示匹配字母及空格组成的字符串，且这个字符串有1个
* ([:alpha:]]+ ?)+表示匹配多个字母元素，注意这里使用+前提是前面必须有1个能匹配的字符串，不能为空
* ^([[:alpha:]]+ ?)+$表示匹配的内容必须字母开头字母结尾   
+匹配前面的子表达式1次或多次，且前面的匹配内容必须是字母

# 限定符{}   
`echo "123 4567890" | grep -Eh '\(?[0-9]{3}\)? [0-9]{7}$'`   
{m}匹配前面子表达式m次   

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterTwo/Regular_Jt">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterThird/">下一章➡️</a></p>
</div>



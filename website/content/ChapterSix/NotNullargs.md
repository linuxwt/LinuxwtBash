---
title: 6.02 非空变量展开       
type: docs
weight: 1
---    

# 字符串展开   

**${#parameter}**   
foo="abcd"   
echo ${#foo}   
输出结果 4   
该展开的意思是返回字符串的长度   

**${parameter:m}**    
foo="ab abc cde"   
echo ${foo:5}    
输出结果 c cde    
该展开的意思是返回从位置为5至最末位的字符串，注意这里的位置类似于切片，位置0对应的是第一个a   

**${parameter:m:n}**   
foo="ab abc cde"   
echo ${foo:5:4}   
输出结果  c cd  
该展开的意思是返回一个字符串，从位置为5开始，字符串长度为4   

**${parameter#para}**   
foo="file.txt.zip"      
echo ${foo#*.}   
输出结果 txt.zip    
该展开的意思是匹配开头的字符串清除，但是这个匹配可能会是多种情况，比如*.可以匹配成file.也可以匹配成file.txt.，但这里取最短的匹配项即file.   

**${parameter##para}**   
foo="file.txt.zip"   
echo ${foo##\*.}   
输出结果 zip   
该展开的意思是匹配开头的字符串清除，但是这个匹配可能会是多种情况，比如*.可以匹配成file.也可以匹配成file.txt.，但这里取最长的匹配项即file.txt   

**${parameter%para}**   
foo="file.txt.zip"   
echo ${foo%.\*}   
输出结果 file.txt   
该展开的意思是匹配末尾的字符串清除，但是这个匹配可能会是多种情况，比如.*，可以匹配成.zip，也可以匹配成.txt.zip，这里取最短的匹配项即.zip      

**${parameter%%para}**   
foo="file.txt.zip"   
echo ${foo%%.\*}   
输出结果 file   
该展开的意思是匹配末尾的字符串清除，但是这个匹配可能会是多种情况，比如.*，可以匹配成.zip，也可以匹配成.txt.zip，这里取最长的匹配项即.txt.zip         

**${parameter/para/string}**   
foo="JPGJPG"   
echo ${foo/JPG/jpg}   
输出结果 jpgJPG    
该展开的意思是匹配JPG,然后用jpg去替换，但是只替换第一个JPG    

**${parameter//para/string}**   
foo="JPGJPG"   
echo ${foo//JPG/jpg}   
输出结果 jpgjpg   
该展开的意思是匹配JPG，然后用jpg去替换，且替换所有的JPG   

**${parameter/#para/string}**   
foo="JPGJPG"   
echo ${foo/#JPG/jpg}   
输出结果 jpgJPG   
该展开的意思是匹配字符串JPG，但必须是字符串开头的JPG，然后用jpg替换    

**${parameter/%para/string}**   
foo="JPGJPG"  
echo ${foo/%JPG/jpg}    
输出结果  JPGjpg   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterSix/Nullargs/">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/NotNullargs/Jisuan">下一页➡️</a></p>
</div>

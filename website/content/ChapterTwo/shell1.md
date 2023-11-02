---
title: 1.01 grep使用正则实现下文本处理     
type: docs
weight: 1
---

思路：  
1、如何在标准输入中搜索匹配特定模式的文本行   
2、如何在单个文件中搜索匹配特定模式的文本行   
3、如何在多个文件中搜索匹配特定模式的文本行   
4、如何在文件中搜索匹配包含任意单词的文本行  
5、如何在文件中搜索匹配到的行中的具体文本   
6、如何在文件中搜索出不匹配的文本行   
7、如何在文件中搜索匹配的文本行的数量   
5、汇总脚本      

下面一层层来解决   
1) 如何在标准输入中搜索匹配特定模式的文本行   
`echo -e "this is a word\nnext line" | grep word`   

2) 如何在单个文件中搜索匹配特定模式的文本行   
`grep word test.txt`   

3) 如何在多个文件中搜索匹配特定模式的文本行    
`grep word test.txt test1.txt test2.txt`   

4) 如何在文件中搜索匹配包含任意单词的文本行   
`grep -E '[a-zA-Z]+' test.txt` 或者 `egrep '[a-z]+' test.txt`   

5) 如何在文件中搜索匹配到的行中的具体文本    
`grep -o 'word' test.txt` 或者 `egrep  -o  'word' test.txt`    
**这里要注意，grep会去匹配每一个符合的文本，然后依次输出**   

6) 如何在文件中搜索出不匹配的文本行    
`grep -v 'word' test.txt` 或者 `egrep -v 'word' test.txt`   

7) 如何在文件中搜索匹配的文本行的数量 
`grep -c 'word' test.txt`   
**这里要注意，grep会去匹配每一行的符合的文本，但同一行匹配到的文本无论有多少符合条件的文本都只能算一次**   




<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterTwo/">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell2">下一页➡️</a></p>
</div>
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
8、如何在文件中搜索出匹配的文本的数量     
9、如何在文件中搜索出匹配的文本所在的行数   
10、如何在文件中搜索出匹配的具体文本和其所在的字符偏移位置  
11、如何在目录中搜索包含匹配文本的文件    
12、如何在多级目录中递归搜索包含匹配文本的文件及文本所在的行数    
13、如何在文件中搜索时忽略匹配的文本大小写    
、汇总脚本      

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

8) 如何在文件中搜索出匹配的文本的数量   
`grep -o 'word' test.txt | wc -l`   

9) 如何在文件中搜索出匹配的文本所在的行数   
`cat test.txt | grep -n 'word'` 或者 `grep -n 'word' test.txt test1.txt`   

10) 如何在文件中搜索出匹配的具体文本和其所在的偏移位置   
`grep -b -o 'word' test.txt`   

11) 如何在目录中搜索包含匹配文本的文件    
`grep -l 'word' ./*`   
**ps1：-L选项相反，筛选出不匹配的文件**   
**ps2: -l与-n一起使用时，因为-l是输出符合匹配文本的文件，-n是既输出了文件名同时也输出了文本的行数，所以为了满足两个选项都满足就会按照输出内容更少即-l输出的内容来输出**   

12) 如何在多级目录中递归搜索包含匹配文本的文件及文本所在的行数     
`grep -Rn 'word' .`   
**ps：选项-R表示可以实现递归特性，结合其他选项使用，不单独使用**   

13) 如何在文件中搜索时忽略匹配的文本大小写   
`grep -i 'word' test.txt`   



<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterTwo/">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell2">下一页➡️</a></p>
</div>
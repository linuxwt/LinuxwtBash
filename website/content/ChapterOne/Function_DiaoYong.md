---
title: 1.01 函数调用   
type: docs
weight: 1
---

# 函数调用   
**常规调用**    
```bash
fun () 
{
  i=0
  REPEATS=30

  echo
  echo "And now the fun really begins."
  echo

  sleep $JUST_A_SECOND
  while [ $i -lt $REPEATS ]
  do
    echo "<------FUNCTIONS------>"
    echo "<------ARE------>"
    echo "<------FUN------>"
    echo
    let "i+=1"
  done
} 

# 现在调用函数
funky
```

**函数内部调用函数**    
```bash
#!/bin/bash

f1 () 
{
  echo "在函数\"f1\"里调用函数\"f2\"."
  f2
}

f2 ()
{
  echo "function\"f2\"."
}

f1
```   

**函数嵌套**   
```bsah
#!/bin/bash

f1 () 
{
  
  f2 ()
  {
    echo "function\"f2\" inside function\"f1\"."
  }  

}

f1
f2
```   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterOne/">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterOne/Fuza_Function">下一页➡️</a></p>
</div>
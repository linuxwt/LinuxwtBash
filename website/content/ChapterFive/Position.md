---
title: 5.01 位置参数   
type: docs
weight: 1
---    

# $0 ${n} $#   
**脚本传参**         
car posi1.sh   
```bash
#!/bin/bash

echo "
\$0 = $0
\$1 = $1
\$2 = $2
\$3 = $3
\$4 = $4
\$5 = $5
\$6 = $6
\$7 = $7
\$8 = $8
\$9 = $9
\$0 = $0   
num is of args is $#
"
```      

`bash posi1.sh a b c`   
输出

```bash
$0 = /root/posi1.sh
$1 = a
$2 = b
$3 = c
$4 =
$5 =
$6 =
$7 =
$8 =
$9 =
number of args is 3
```   

# $* $@  
**函数传参**   
cat posi2.sh   
```bash
#!/bin/bash

test1 () {
echo "\$1=$1"
echo "\$2=$2"
echo "\$3=$3"
echo "\$4=$4"
}

test2 () {
echo  -e "\n" '$* :'
test1 $*
echo -e "\n" '$* :'
test1 "$*"

echo -e "\n" '$@ :'
test1 $@
echo -e "\n" '$@ :'
test1 "$@"
}

test2 "wo" "shi wang" "teng"
```     

`bash posi2.sh`   
输出   

```bash
 $* :
$1=wo
$2=shi
$3=wang
$4=teng

 $* :
$1=wo shi wang teng
$2=
$3=
$4=

 $@ :
$1=wo
$2=shi
$3=wang
$4=teng

 $@ :
$1=wo
$2=shi wang
$3=teng
$4=
```   

函数在传递位置参数列表$*和$@时，是否使用双引号输出的内容区别   
|参数|无双引号|有双引号|   
|:----|:----|:----|   
|$*|展开成一个从1开始的位置参数列表|展开成一个由双引号引起来的包含了所有的位置参数的字符串|   
|$@|展开成一个从1开始的位置参数列表|每一个位置参数展开成一个由双引号引起来的分开的字符串|   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterFive/">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterSix/">下一章➡️</a></p>
</div>




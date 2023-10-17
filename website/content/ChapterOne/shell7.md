---
title: 1.07 创建指定路径/path的模板脚本文件abc.sh并带有说明信息      
type: docs
weight: 1
---

思路：
1、如何输入要处理的文件（要创建的脚本文件），如果不输入文件会报错退出，如果输入的文件的格式不同会执行不同操作   
2、如何创建脚本文件，并输入相关信息到文件   
3、如何定义不同操作，包括床脚脚本、输入脚本说明信息   
4、变量处理，按照脚本规范原则，对于脚本中出现的特定数值一律通过全局变量来定义，对于特定的字符或字符串变量也一律用全局变量来定义   
5、汇总脚本   


下面一层层来解决   
1) 如何输入要处理的文件（要创建的脚本文件），如果不输入文件会报错退出，如果输入的文件的格式不同会执行不同操作    
```bash
# 指定输入的文件方式为位置参数，同时如果不输入位置参数会报错退出
[ $# -ne 1 ] && { echo "Usage: $(basename $0) need one argument.";exit 1; }
shfile=$1
# 根据不同文件格式，执行不同的函数操作    
[[ ! ${shfile} == /* ]] && { Shfile="${shfile}";chuangjianfile1; } || chuangjianfile2 
```   

2) 如何创建脚本文件，并输入相关信息到文件   
```bash
cat <<EOF>> /path/abc.sh
# /bin/bash
# mail tengwanginit@gmail.com
EOF
```   

3) 如何定义不同操作，包括创建脚本、输入脚本说明信息   
操作1      
```bash
cat <<EOF>> $shfile
# /bin/bash
# mail tengwanginit@gmail.com
EOF
```  

操作2   
```bash
cat <<EOF>> $Shfile
# /bin/bash
# mail tengwanginit@gmail.com
EOF
```   

4) 变量处理，按照脚本规范原则，对于脚本中出现的特定数值一律通过全局变量来定义，对于特定的字符或字符串变量也一律用全局变量来定义    
略   

5) 汇总脚本   
```bash
#!/bin/bash

chuangjianfile1 () {
cat <<EOF> $Shfile
# /bin/bash
# mail tengwanginit@gmail.com
EOF
}

chuangjianfile2 () {
cat <<EOF> $shfile
# /bin/bash
# mail tengwanginit@gmail.com
EOF
}

[ $# -ne 1 ] && { echo "Usage: $(basename $0) need one argument.";exit 1; }
shfile=$1
[[ ! ${shfile} == /* ]] && { Shfile="/${shfile}";chuangjianfile1; } || chuangjianfile2 
```   

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell6">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell8">下一页➡️</a></p>
</div>
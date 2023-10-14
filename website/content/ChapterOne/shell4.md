---
title: 1.04 检查目录/www下的文件是否被篡改并输出被改的文件名
type: docs
weight: 1
---

思路：
1、如何输入要处理的目录（要进行搜索的目录），如果不输入目录会报错退出，如果输入的目录格式不同会执行不同操作   
2、如何生成初始扫描文件  
3、如何对扫描文件进行校验，并将校验结果输入到结果文件   
4、如何定义不同的操作，包括进入目标目录，生成初始扫描文件，对扫描文件进行校验，并将校验结果输入到结果文件      
5、如何区分校验结果   
6、如何在校验结果显示文件有被改动时输出被改动的文件名   
7、如何在校验结果显示文件没有被改动时，输出无变化   
8、汇总脚本        

下面一层层来解决   
1）如何输入要处理的目录，如果不输入会报错退出，如果输入的目录格式不同执行不同的下一步   
```bash
# 指定输入的目录方式为位置参数，同时如果不输入位置参数会报错退出
[ $# -ne 1 ] && { echo "Usage: $(basename $0) need one argument.";exit -1; }
# 根据不同目录格式，执行不同的函数操作  
dir=$1
[[ ! ${dir} == /* ]] && { Dir=/${dir};checkfile1; } || { checkfile2; }
```   
2) 如何生成初始扫描文件   
`[ -f /tmp/html.md5 ] || { find ./ -type f | xargs md5sum > /tmp/html.md5; }`  

3) 如何对扫描文件进行校验，并将扫描文件结果输入到结果文件  
`md5sum -c /tmp/html.md5 > /tmp/md5.check 2>&1`   

4) 如何定义不同的操作，包括进入目标目录，生成初始扫描文件，对扫描文件进行校验，并将扫描文件结果输入到结果文件   
操作1  
```bash
# 进入目标目录    
cd $dir     
# 生成初始扫描文件   
[ -f /tmp/html.md5 ] || { find ./ -type f | xargs md5sum > /tmp/html.md5; }
# 对扫描文件进行校验，并将扫描文件结果输入到结果文件   
md5sum -c /tmp/html.md5 > /tmp/md5.check 2>&1
```    

操作2   
```bash   
cd $Dir     
# 生成初始扫描文件   
[ -f /tmp/html.md5 ] || { find ./ -type f | xargs md5sum > /tmp/html.md5; }
# 对扫描文件进行校验，并将扫描文件结果输入到结果文件   
md5sum -c /tmp/html.md5 > /tmp/md5.check 2>&1
```   

5) 如何区分校验结果  
`[ $? -eq 0 ]` && nogaidong || gaidong   


6) 如何在校验结果显示文件有被改动时输出被改动的文件名   
```bash
file=$(grep FAILED /tmp/md5.check | awk -F ':' '{print $1}')
echo -e "$file is changed ."
``` 

7) 如何在校验结果显示文件没有被改动时，输出无变化   
`echo "not change"`   

8) 汇总脚本   
```bash
#!/bin/bash

checkfile1 () {
cd $Dir     
[ -f /tmp/html.md5 ] || { find ./ -type f | xargs md5sum > /tmp/html.md5; }
md5sum -c /tmp/html.md5 > /tmp/md5.check 2>&1
return  $?
}

checkfile2 () {
cd $dir     
[ -f /tmp/html.md5 ] || { find ./ -type f | xargs md5sum > /tmp/html.md5; }
md5sum -c /tmp/html.md5 > /tmp/md5.check 2>&1
return $?
}

nogaidong () {
echo "not change"
}

gaidong () {
file=$(grep 失败 /tmp/md5.check | awk -F ':' '{print $1}')
echo -e "$file is changed ."
}


[ $# -ne 1 ] && { echo "Usage: $(basename $0) need one argument.";exit -1; }
dir=$1
[[ ! $dir == /* ]] && { Dir="/${dir}";checkfile1; } 
[[ $dir == /* ]] && checkfile2

[ $? -eq 0 ] && nogaidong || gaidong 
```   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell3">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell5">下一页➡️</a></p>
</div>
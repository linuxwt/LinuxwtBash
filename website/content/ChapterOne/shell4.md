---
title: 1.04 检查目录/var/www/html下的文件是否被篡改并输出被改的文件名
type: docs
weight: 1
---

思路：
1、如何输入要处理的目录（要进行搜索的目录），如果不输入目录会报错退出，如果输入的目录格式不同会执行不同操作   
2、如何校验文件内容被篡改       
3、如何定义不同操作，包括待搜索的目标目录，发现被篡改后的操作，没有篡改的操作     
4、汇总脚本      

下面一层层来解决   
1）如何输入要处理的目录，如果不输入会报错退出，如果输入的目录格式不同执行不同的下一步   
```bash
# 指定输入的目录方式为位置参数，同时如果不输入位置参数会报错退出
[ $# -ne 1 ] && { echo "Usage: $(basename $0) need one argument.";exit -1; }
# 根据不同目录格式，执行不同的函数操作  
dir=$1
[[ ! ${dir} == /* ]] && { Dir=/${dir};checkfile1; } || { checkfile2; }
```   

2) 如何校验文件被篡改了         
被篡改的意思就是前后内容不一致，那么通过什么来判断文件内容不一致了呢，可以使用shell命令md5\_sum来进行校验，通过对目标目录的文件进行一个扫描，将扫描信息输入到某个文件，这个文件会与目录下的文件形成动态映射，一旦目标目录下的文件内容被改动，会报错，我们将扫描结果也输入到结果文件，针对这个文件来进行下一步判断   
```bash
# 先生成初始的扫描文件   
md5file () {
find /var/www/html -type f | xargs md5sum > /tmp/html.md5
}
[ -f html.md5 ] || find { md5file; }
# 对扫描文件进行校验，并将扫描文件的结果输入到结果文件，也包括错误信息      
md5sum -c /tmp/html.md5 > /tmp/md5.check 2>&1
```   

3) 如何定义不同操作，包括待搜索的目标目录，发现被篡改后的操作，没有篡改的操作  






<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell3">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell5">下一页➡️</a></p>
</div>
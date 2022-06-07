---
title: 1.01  进程替换
type: docs
weight: 1
---

# 格式   
<(command) or >(command)   
注意小括号与标识符之间无空格，否则会报错   

# 例子      
exp1:   
```bash
#!/bin/bash

mkdir -p /root/day{1..3}
cat <(ls -l)    
```   
执行输出     
```bash
total 4
drwxr-xr-x. 2 root root  6 Jun  7 18:12 day1
drwxr-xr-x. 2 root root  6 Jun  7 18:12 day2
drwxr-xr-x. 2 root root  6 Jun  7 18:12 day3
-rwxr-xr-x. 1 root root 54 Jun  7 18:12 exp1.sh
```   

exp2:   
```bash
#!/bin/bash

touch /root/day1/test{1..3}   
touch /root/day2/test{4..6}

diff <(ls -l /root/day1) <(ls -l /root/day2)   
```   
执行输出   
```bash
2,4c2,4
< -rw-r--r--. 1 root root 0 Jun  7 18:17 test1
< -rw-r--r--. 1 root root 0 Jun  7 18:17 test2
< -rw-r--r--. 1 root root 0 Jun  7 18:17 test3
---
> -rw-r--r--. 1 root root 0 Jun  7 18:17 test4
> -rw-r--r--. 1 root root 0 Jun  7 18:17 test5
> -rw-r--r--. 1 root root 0 Jun  7 18:17 test6
```   
通过进程替换来查看两个目录   

exp3:   
```bash
#!/bin/bash

while read a b c d
do
  echo $a $b $c $d
done < <(route -n)
```   
执行输出   
```bash
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.0.1 0.0.0.0 UG 100 0 0 ens32
192.168.0.0 0.0.0.0 255.255.255.0 U 100 0 0 ens32
```   
要特别注意上面的进程替换部分，两个<是有空格的，这里有点类似与前面的函数使用重定向标准输入，但那里是直接使用文件，本例的进程替换就可以看作是标准输入的的文件       


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterThree">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterThree">下一章➡️</a></p>
</div>
---
title: 1.01   脚本中使用别名
type: docs
weight: 1
---

# 脚本中设置别名    
```bash
#!/bin/bash

shopt -s expand_aliases

alias abc='echo "\"Alias abc\" was a 1950 comedy"'
abc

alias ll="ls -l"
ll /root

mkdir -p /root/test{1..3}
directory=/root/
prefix=test*

alias lll="ls -l $directory$prefix"
lll

TRUE=1
if [ TRUE ]
then
  alias rr="ls -l"
  rr /root/test*
fi

count=0
while [ $count -lt 3 ]
do
  alias rrr="ls -l"
  rrr /root/test*
  let "count=count+1"
done
alias xyz='cat $0'
xyz

exit 0
```   
执行输出    
```bash
"Alias abc" was a 1950 comedy
total 0
drwxr-xr-x. 2 root root 73 Jun  6 21:07 day2
drwxr-xr-x. 2 root root  6 Jun  6 21:05 test1
drwxr-xr-x. 2 root root  6 Jun  6 21:05 test2
drwxr-xr-x. 2 root root  6 Jun  6 21:05 test3
/root/test1:
total 0

/root/test2:
total 0

/root/test3:
total 0
alias.sh: line 22: rr: command not found
alias.sh: line 29: rrr: command not found
alias.sh: line 29: rrr: command not found
alias.sh: line 29: rrr: command not found
#!/bin/bash

shopt -s expand_aliases

alias abc='echo "\"Alias abc\" was a 1950 comedy"'
abc

alias ll="ls -l"
ll /root

mkdir -p /root/test{1..3}
directory=/root/
prefix=test*

alias lll="ls -l $directory$prefix"
lll

TRUE=1
if [ TRUE ]
then
  alias rr="ls -l"
  rr /root/test*
fi

count=0
while [ $count -lt 3 ]
do
  alias rrr="ls -l"
  rrr /root/test*
  let "count=count+1"
done


alias xyz='cat $0'
xyz

exit 0
```    

# 脚本中删除别名   
```bash
#!/bin/bash

shopt -s expand_aliases

alias lm="ls -la"
lm

unalias lm
lm
```   
执行脚本   
```bash
total 20
drwxr-xr-x. 2 root root  91 Jun  6 21:17 .
dr-xr-x---. 6 root root 163 Jun  6 21:05 ..
-rwxr-xr-x. 1 root root 417 Jun  6 21:04 alias.sh
-rwxr-xr-x. 1 root root 274 Jun  6 14:07 get-id2.sh
-rwxr-xr-x. 1 root root 290 Jun  6 13:49 get-id.sh
-rwxr-xr-x. 1 root root 101 Jun  6 15:03 local.sh
-rwxr-xr-x. 1 root root  74 Jun  6 21:17 unalias.sh
unalias.sh: line 9: lm: command not found
```   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterTwo">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/">下一章➡️</a></p>
</div>
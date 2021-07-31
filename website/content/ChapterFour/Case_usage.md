---
title: 4.01 case使用
type: docs
weight: 1
---    

# case结构   
结构   
```bash
case $i in 
a) command 
  ;;
b) command
  ;;
c) command
  ;;
*) command
  ;;
esac
```    

# case使用   
```bash
#!/bin/bash

clear
while true
done
echo "
please select:
1、display disk space
2、display system information
3、display home space utilization
0、quit
"
read -p "enter select [0-3] >"
case $REPLY in
0) echo "program terminated"
  ;;
1) df -h
  ;;
2) echo "HOSTNAME:$HOSTNAME"
  ;;
3) if [ $(id -u) -eq 0 ];then
       du -sh /home/*
   else
       du -sh $HOME
   fi
   ;;
*) echo "invalid entry"
   exit -1
   ;;
esac
done 
```    

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterFour/">⬅️上一页</a></p>
<p><a href="https://books.linuxwt.com/linuxwtbash/ChapterFive/">下一章➡️</a></p>
</div>




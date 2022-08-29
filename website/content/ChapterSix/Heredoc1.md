---
title: 1.01 使用heredocument打印消息
type: docs
weight: 1
---

## 打印常规消息
```bash
#!/bin/bash

cat << EOF
------------
This is line 1 of the essage.
This is line2 of the message.
This is line3 of the message.
This is line4 of the message
This is the last line of the message.
-------------
EOF
```   
执行输出    
```bash
------------
This is line 1 of the essage.
This is line2 of the message.
This is line3 of the message.
This is line4 of the message
This is the last line of the message.
-------------
```   

## 打印抑制tab消息   
```bash
#!/bin/bash

cat <<-EOF
------------
	This is line 1 of the essage.
	This is line2 of the message.
	This is line3 of the message.
	This is line4 of the message
 This is the last line of the message.
-------------
EOF
```   
执行输出    
```bash
------------
This is line 1 of the essage.
This is line2 of the message.
This is line3 of the message.
This is line4 of the message
 This is the last line of the message.
-------------
```   

## 打印帮助信息   
```bash
#!/bin/bash

DOC_REQUEST=80

if [ "$1" = "-h" -o "$1" = "--help" ]
then
  cat <<EOF
List the statistics of a specified directory in tabular format
---------------------------------------------------------------
The command line parameter gives the directory to be listed
EOF
exit $DOC_REQUEST
fi
```   

## 打印的消息输入到文件   
```bash
#!/bin/bash

cat > newfile << EOF
------------
This is line 1 of the essage.
This is line2 of the message.
This is line3 of the message.
This is line4 of the message
This is the last line of the message.
-------------
EOF
```   



<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterSix">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterFive/Chongdingxiang2">下一页➡️</a></p>
</div>

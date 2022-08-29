---
title: 1.04 Heredocument与参数替换
type: docs
weight: 1
---

heredocument输出内容是可以含有变量,但是变量是否被替换取决于heredocument的limit string是否被引用   

## 不被引用的情况   
```bash
#!/bin/bash
Name="wangteng"
Respondent="the author of the fine scripts"
cat <<EOF
hello,there ,$Name
greetings to you,$Name,from $Respondent
EOF

exit 0
```   
执行输出   
```bash
hello,there ,wangteng
greetings to you,wangteng,from the author of the fine scripts
```   

## 引用的情况   
```bash
#!/bin/bash
Name="wangteng"
Respondent="the author of the fine scripts"
cat <<'EOF'
hello,there ,$Name
greetings to you,$Name,from $Respondent
EOF

exit 0
```   
执行输出   
```bash
hello,there ,$Name
greetings to you,$Name,from $Respondent
```   

## 利用禁用参数替换的特点来实现使用脚本生成脚本或其他代码   
```bash
#!/bin/bash

outfile=generated.sh

(
cat <<'EOF'
#!/bin/bash

echo "this is a generated shell script"
echo "generated file will be named $outfile"

a=7
b=3

let "c = $a * $b"
echo "c = $c"
exit 0
EOF
) > $outfile

if [ -f "$outfile" ]
then
  chmod 755 $outfile
else
  echo "have in creating file: \"$outfile\""
fi

exit 0
```   

<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterSix/Heredoc2">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterSix/Heredoc4">下一页➡️</a></p>
</div>

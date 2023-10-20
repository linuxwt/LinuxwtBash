---                        
title: 1.11 文件的几个特殊权限                   
type: docs
weight: 1
---

思路：  
1、给一个目录赋予一个粘滞位权限，这个目录里的文件只有所有者才能够删除，即使这个文件其他用户有写入权限也无法删除      
2、给一个二进制文件赋予setuid权限，其它用户能够使用该文件的所有者执行文件   
3、给一个文件赋予不可修改权限，其他用户包括root也无法修改或删除此文件   

1) 给一个目录赋予一个粘滞位权限，这个目录里的文件只有所有者才能够删除，即使这个文件其他用户有写入权限也无法删除    
`chmod a+t filename`   

2) 给一个二进制文件赋予setuid权限，其它用户能够使用该文件的所有者执行文件   
比如现在有两个用户abc root，文件所有者是root，现在想用abc这个用户来执行文件   
首先切换至abc用户，执行命令   
`chmod +s filename`   
其次切换至root用户      
`chown -R root.root filename`   
`chmod +s filename`   
最后切换至abc用户     
`./filename`这个时候abc用户就可以使用root权限来执行该文件   
   
**ps:setuid权限只能用于二进制程序文件，不能用于脚本**   

3) 给一个文件赋予不可修改权限，其他用户包括root也无法修改或删除此文件   
`chattr +i filename`  



<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell8">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell10">下一页➡️</a></p>
</div>
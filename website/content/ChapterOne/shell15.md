---
title: 1.15 创建并挂载一个环回文件                          
type: docs
weight: 1
---

思路：   
1、如何创建环回文件   
2、如何挂载环回文件   
3、汇总脚本   


下面一层层来解决   
1) 如何创建环回文件   
`dd if=/dev/zero of=loopbackfile.img bs=1G count=1`
`mkfs.xfs loopbackfile.img`   

2) 如何挂载环回文件   
`mkdir -p /mnt/loopback`
`mount -o loop loopbackfile.img /mnt/loopback`   

3) 汇总脚本   
```bash
#!/bin/bash

loopfile () {
dd if=/dev/zero of=loopbackfile.img bs=1G count=1
mkfs.xfs loopbackfile.img
mkdir -p /mnt/loopback
mount -o loop loopbackfile.img /mnt/loopback
}

loopfile
```   


<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell8">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtsbc/ChapterOne/shell10">下一页➡️</a></p>
</div>
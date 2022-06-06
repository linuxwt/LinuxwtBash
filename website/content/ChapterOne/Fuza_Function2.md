---
title: 1.03 函数使用return  
type: docs
weight: 1
---

# return与$?   
bash中$?为上一条命令执行后的退出状态，如果是函数则为函数中执行的最后一条命令后的退出状态，但这种退出状态往往不由我们控制，这时return就派上作用了。下面总结了以下几种return使用情况   
* 返回具体数值   
return 20   
* 根据判断返回不同的值  
return $var

return返回的数值会赋值给$?   

# 返回常规值           
exp1： 
```bash
#!/bin/bash

# 比较两个数的大小
# 0、为情况1、2设定两个特定值   
# 1、是否有足够的位置参数 输出返回值1
# 2、两个参数值相等 输出返回值2
# 3、参数1大于参数2 输出返回值3
# 4、参数2大于参数1 输出返回值4
# 5、 将1-4使用函数封装
# 6、将函数执行后的返回值赋值给一个变量
# 7、将变量值与设定值作比较，输出结果

E_QUAL=200
E_NUM=201

max ()
{
    if [ -z "$2" ];then
        return $E_NUM
    fi
    if [ "$1" -eq "$2" ];then
        return $E_QUAL
    fi
    if [ "$1" -gt "$2" ];then
        return $1
    else
        return $2
    fi
}

max $1 $2
return_val=$?

if [ "$return_val" -eq "$E_NUM" ];then
    echo "The function max need two args."
elif [ "$return_val" -eq "$E_QUAL" ];then
    echo "The two args are equal."
else
    echo "The bigger args is $return_val."
fi
```   
执行脚本   
bash exp3.sh 10 20   
输出The bigger args is 20.

上面这个脚本写的太冗余，其实可以优化一下   
exp2:   
```bash
#!/bin/bash

E_QUAL=200
E_NUM=201

max ()
{
    if [ -z "$2" ];then
        result=$E_NUM
    fi
    if [ "$1" -eq "$2" ];then
        result=$E_QUAL
    fi
    if [ "$1" -gt "$2" ];then
        result=$1
    else
        result=$2
    fi
    return $result
}

max $1 $2
return_val=$?

if [ "$return_val" -eq "$E_NUM" ];then
    echo "The function max need two args."
elif [ "$return_val" -eq "$E_QUAL" ];then
    echo "The two args are equal."
else
    echo "The bigger args is $return_val."
fi
```  

# 返回非常规值   
在函数里返回值是有范围的，最大为255   
```bash
#!/bin/bash

return_test ()
{
  return $1 
}

return_test 20
echo $?
return_test 255
echo $?
return_test 256
echo $?
return_test 20000
echo $?
```   
执行输出   
27
255
0
32   
显然后二出现的值并非预期出现的值     

那么如何处理这种情况，返回我们想要的值呢？   
bash里可以通过命令替换的方式来实现，具体思路是在函数中将要返回的值通过echo打印到stdout，然后通过命令替换捕获该值   
exp1:   
cat return_echo.sh   
```bash
#!/bin/bash

E_ARGS_ERR=100
E_EQUAL=65

max2 () 
{

if [ -z "$2" ]
then
  echo "Usage:The function need two args"
  exit $E_ARGS_ERR
fi

if [ "$1" -eq "$2" ]
then
  result=$E_EQUAL
elif [ "$1" -gt "$2" ]
then
  result=$1
else
  result=$2
fi

echo $result
}

re_val=$(max2 30000 4000)

if [[ "$re_val" -eq "$E_EQUAL" ]]
then
  echo "arg1  is equal arg2"
elif [[ "$re_val" -eq "$E_ARGS_ERR" ]]
then
  echo "args is not enough"
else
  echo "The bigger number is $re_val"
fi

echo

exit 0
```  



<div style="display: flex;justify-content: space-between;align-items: center;">
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterOne/Fuza_Function">上一页➡️</a></p>
<p><a href="https://books.linuxwt.com/linuxwtabs/ChapterOne/Fuza_Function3">下一页➡️</a></p>
</div>
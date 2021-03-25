## Shell进阶

* [1.<strong>举例如何写一个函数 ?</strong>](#1举例如何写一个函数-)
* [2.写出 shell 脚本中所有循环语法 ?](#2写出-shell-脚本中所有循环语法-)
* [3. &gt; 做什么 ?](#3--做什么-)
* [4.命令： name=John &amp;&amp; echo 'My name is $name' 的输出是什么](#4命令-namejohn--echo-my-name-is-name-的输出是什么)
* [5. Shell中提交了一个脚本，进程号已经不知道了，但是需要kill掉这个进程，怎么操作？](#5-shell中提交了一个脚本进程号已经不知道了但是需要kill掉这个进程怎么操作)
* [6.shell脚本中break命令的作用 ?](#6shell脚本中break命令的作用-)
* [7. shell脚本中continue命令的作用 ?](#7-shell脚本中continue命令的作用-)
* [8.告诉我shell脚本中Case语句的语法 ?](#8告诉我shell脚本中case语句的语法-)
* [9.shell脚本中while循环语法 ?](#9shell脚本中while循环语法-)
* [10.如何使脚本可执行 ?](#10如何使脚本可执行-)
* [参考链接](#参考链接)

#### 1.**举例如何写一个函数 ?**

```
function` `example {
echo` `"Hello world!"
}
```

#### 2.写出 shell 脚本中所有循环语法 ?

**for 循环 :**

```
foriin$(``ls``);``do``echo` `item:$i``done
```

**while 循环 :**

```
#!/bin/bash``COUNTER=0``while` `[ $COUNTER -lt 10 ]; ``do``echo` `The counter is $COUNTER``let` `COUNTER=COUNTER+1``done
```

**until 循环 :**

```
#!/bin/bash``COUNTER=20``until` `[ $COUNTER -lt 10 ]; ``do``echo` `COUNTER $COUNTER``let` `COUNTER-=1``done
```

#### 3. > 做什么 ?

重定向输出流到文件或另一个流。

#### 4.命令： `name=John && echo 'My name is $name'` 的输出是什么

variable

#### 5. Shell中提交了一个脚本，进程号已经不知道了，但是需要kill掉这个进程，怎么操作？

```linux
ssh $i "ps -ef | grep file-flume-kafka | grep -v grep | awk '{print \$2}' | xargs kill
```

#### 6.shell脚本中break命令的作用 ?

break命令一个简单的用途是退出执行中的循环。我们可以在while和until循环中使用break命令跳出循环。

#### 7. shell脚本中continue命令的作用 ?

continue命令不同于break命令，它只跳出当前循环的迭代，而不是整个循环。continue命令很多时候是很有用的，例如错误发生，但我们依然希望继续执行大循环的时候。

#### 8.告诉我shell脚本中Case语句的语法 ?

基础语法如下：

```
case 变量 in  值1)  命令1  命令2  …..  ***命令  !!  值2)  命令1  命令2  ……  ***命令  ;;  esac 
```

#### 9.shell脚本中while循环语法 ?

如同for循环，while循环只要条件成立就重复它的命令块。不同于for循环，while循环会不断迭代，直到它的条件不为真。基础语法：

```
while [ 条件 ] 
do  
命令… 
done 
```

#### 10.如何使脚本可执行 ?

```linux
# chmod a+x myscript.sh 
```



#### 参考链接

https://blog.csdn.net/weixin_45557389/article/details/109466619

https://www.jianshu.com/p/74e620fa863c

https://os.51cto.com/art/201902/592119.htm
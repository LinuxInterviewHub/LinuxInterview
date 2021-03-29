## Shell echo 命令

* [1.语法](#1语法)
* [2. 显示普通字符串:](#2-显示普通字符串)
* [3. 显示转义字符](#3-显示转义字符)
* [4. 显示变量](#4-显示变量)
* [5 显示换行](#5-显示换行)
* [6. 显示不换行](#6-显示不换行)
* [7. 显示结果定向至文件](#7-显示结果定向至文件)
* [8. 原样输出字符串，不进行转义或取变量 (用单引号)](#8-原样输出字符串不进行转义或取变量-用单引号)
* [9. 显示命令执行结果](#9-显示命令执行结果)
* [参考链接](#参考链接)

#### 1.语法

Shell echo 命令 Shell 的 echo 指令与 PHP 的 echo 指令类似，都是用于字符串的输出。

Shell 的 echo 指令与 PHP 的 echo 指令类似，都是用于字符串的输出。命令格式：

```
echo string
```

您可以使用 echo 实现更复杂的输出格式控制。

#### 2. 显示普通字符串:

```
echo "It is a test"
```

这里的双引号完全可以省略，以下命令与上面实例效果一致：

```
echo It is a test
```

#### 3. 显示转义字符

```
echo "\"It is a test\""
```

结果将是:

```
"It is a test"
```

同样，双引号也可以省略

#### 4. 显示变量

read 命令从标准输入中读取一行, 并把输入行的每个字段的值指定给 shell 变量

```
#!/bin/sh
read name 
echo "$name It is a test"
```

以上代码保存为 test.sh，name 接收标准输入的变量，结果将是:

```
[root@www ~]# sh test.sh
OK                     #标准输入
OK It is a test        #输出
```

#### 5 显示换行

```
echo -e "OK! \n" # -e 开启转义
echo "It is a test"
```

输出结果：

```
OK!

It is a test
```

#### 6. 显示不换行

```
#!/bin/sh
echo -e "OK! \c" # -e 开启转义 \c 不换行
echo "It is a test"
```

输出结果：

```
OK! It is a test
```

#### 7. 显示结果定向至文件

```
echo "It is a test" > myfile
```

#### 8. 原样输出字符串，不进行转义或取变量 (用单引号)

```
echo '$name\"'
```

输出结果：

```
$name\"
```

#### 9. 显示命令执行结果

```
echo `date`
```

**注意：** 这里使用的是反引号 `, 而不是单引号 '。

结果将显示当前日期

```
Thu Jul 24 10:08:46 CST 2014
```



#### 参考链接

https://www.runoob.com/linux/linux-shell-printf.html

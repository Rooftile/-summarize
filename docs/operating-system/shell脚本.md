参考：http://c.biancheng.net/view/743.html

# Shell基础

Shell 是一个应用程序，它连接了用户和 Linux 内核，让用户能够更加高效、安全、低成本地使用 Linux 内核，这就是 Shell 的本质。

## 常用的Shell有哪些？

我们还可以通过echo $SHELL 命令来查看当前使用的Shell类型。

下面我们进行一些常见Shell的讲解：

1. **BourneShell(sh)：是由AT&T Bell实验室的 Steven Bourne为AT&T的Unix开发的，它是Unix的默认Shell，也是其它Shell的开发基础。Bourne Shell在编程方面相当优秀，但在处理与用户的交互方面不如其它几种Shell。**
2. ***BourneAgain Shell (\**\**即\**\**bash)\****：是自由软件基金会(GNU)开发的一个Shell，它是Linux系统中一个默认的Shell。Bash不但与Bourne Shell兼容，还继承了C Shell、Korn Shell等优点。
3. **ash：ash Shell是由Kenneth Almquist编写的，是Linux 中占用系统资源最少的一个小Shell，它只包含24个内部命令，因而使用起来很不方便。**
4. **CShell(csh)**是加州伯克利大学的Bill Joy为BSD Unix开发的，共有52个内部命令，与sh不同，它的语法与C语言很相似。它提供了Bourne Shell所不能处理的用户交互特征，如命令补全、命令别名、历史命令替换等。但是，C Shell与BourneShell并不兼容。该Shell其实是指向/bin/tcsh这样的一个Shell，也就是说，csh其实就是tcsh。
5. **KornShell(ksh)**：是AT&T Bell实验室的David Korn开发的，共有42 条内部命令，它集合了C Shell和Bourne Shell的优点，并且与Bourne Shell向下完全兼容。Korn Shell的效率很高，其命令交互界面和编程交互界面都很好。
6. **zsh**：是Linux 最大的Shell之一，由Paul Falstad完成，共有84 个内部命令。如果只是一般的用途，没有必要安装这样的Shell。

​    注释：bash是 Bourne Again Shell 的缩写，是linux标准的默认shell ，它基于Bourne shell，吸收了C shell和Korn shell的一些特性。bash完全兼容sh，也就是说，用sh写的脚本可以不加修改的在bash中执行。



# Shell编程

## Shell变量



当然，如果有必要，你也可以使用 [Shell declare](http://c.biancheng.net/view/2709.html) 关键字显式定义变量的类型，但在一般情况下没有这个需求，Shell 开发者在编写代码时自行注意值的类型即可。

### 定义变量

Shell 支持以下三种定义变量的方式：

```shell
variable=value
variable='value'
variable="value"
```

variable 是变量名，value 是赋给变量的值。如果 value 不包含任何空白符（例如空格、Tab 缩进等），那么可以不使用引号；如果 value 包含了空白符，那么就必须使用引号包围起来。使用单引号和使用双引号也是有区别的，稍后我们会详细说明。

注意，赋值号`=`的周围不能有空格，这可能和你熟悉的大部分编程语言都不一样。

Shell 变量的命名规范和大部分编程语言都一样：

- 变量名由数字、字母、下划线组成；
- 必须以字母或者下划线开头；
- 不能使用 Shell 里的关键字（通过 help 命令可以查看保留关键字）。


变量定义举例：

```shell
url=http://c.biancheng.net/shell/
echo $url
name='C语言中文网'
echo $name
author="严长生"
echo ${author}
```

推荐给所有变量加上花括号`{ }`，这是个良好的编程习惯。

### 修改变量的值

已定义的变量，可以被重新赋值，如：

```shell
url="http://c.biancheng.net"
echo ${url}
url="http://c.biancheng.net/shell/"
echo ${url}
```

第二次对变量赋值时不能在变量名前加`$`，只有在使用变量时才能加`$`。

### 将命令的结果赋值给变量

Shell 也支持将命令的执行结果赋值给变量，常见的有以下两种方式：

```shell
variable=`command`
variable=$(command)
```

### 只读变量

使用 **readonly** 命令可以将变量定义为只读变量，只读变量的值不能被改变。

下面的例子尝试更改只读变量，结果报错：

```shell
#!/bin/bash
myUrl="http://c.biancheng.net/shell/"
readonly myUrl
myUrl="http://c.biancheng.net/shell/"
```

运行脚本，结果如下：

```
bash: myUrl: This variable is read only.
```

### 删除变量

使用 **unset** 命令可以删除变量。语法：

```shell
unset variable_name
```

变量被删除后不能再次使用；unset 命令不能删除只读变量。

举个例子：

```shell
#!/bin/shmy
Url="http://c.biancheng.net/shell/"
unset myUrl
echo $myUrl
```

上面的脚本没有任何输出。

### Shell变量的作用域

### Shell特殊变量

| 变量      | 含义                                                         |
| --------- | ------------------------------------------------------------ |
| $0        | 当前脚本的文件名。                                           |
| $n（n≥1） | 传递给脚本或函数的参数。n 是一个数字，表示第几个参数。例如，第一个参数是 $1，第二个参数是 $2。 |
| $#        | 传递给脚本或函数的参数个数。                                 |
| $*        | 传递给脚本或函数的所有参数。                                 |
| $@        | 传递给脚本或函数的所有参数。当被双引号`" "`包含时，$@ 与 $* 稍有不同，我们将在《[Shell $*和$@的区别](http://c.biancheng.net/view/vip_4559.html)》一节中详细讲解。 |
| $?        | 上个命令的退出状态，或函数的返回值，我们将在《[Shell $?](http://c.biancheng.net/view/808.html)》一节中详细讲解。 |
| $$        | 当前 Shell 进程 ID。对于 Shell 脚本，就是这些脚本所在的进程 ID。 |

### Linux declare命令

Linux declare命令用于声明 shell 变量。

declare为shell指令，在第一种语法中可用来声明变量并设置变量的属性([rix]即为变量的属性），在第二种语法中可用来显示shell函数。若不加上任何参数，则会显示全部的shell变量与函数(与执行set指令的效果相同)。



```
declare [+/-][rxi][变量名称＝设置值] 或 declare -f
```

**参数说明**：

- +/- 　"-"可用来指定变量的属性，"+"则是取消变量所设的属性。
- -f 　仅显示函数。
- r 　将变量设置为只读。
- x 　指定的变量会成为环境变量，可供shell以外的程序来使用。
- i 　[设置值]可以是数值，字符串或运算式。

1. **声明整数型变量**

```shell
declare -i ab //声明整数型变量
ab=56 //改变变量内容
echo $ab //显示变量内容
# 56
```

2. **改变变量属性**

```shell
declare -i ef //声明整数型变量
ef=1  //变量赋值（整数值）
echo $ef //显示变量内容
# 1
ef="wer" //变量赋值（文本值）
echo $ef 
# 0
declare +i ef //取消变量属性
ef="wer"
echo $ef
# wer
```

3. **设置变量只读**

```shell
# declare -r ab //设置变量为只读
# ab=88 //改变变量内容
-bash: ab: 只读变量
# echo $ab //显示变量内容
56
```

4. **声明数组变量**

```shell
declare -a cd='([0]="a" [1]="b" [2]="c")' //声明数组变量
echo ${cd[1]}
# b //显示变量内容

echo ${cd[@]} //显示整个数组变量内容
# a b c
```

5. **显示函数**

```shell
# declare -f
command_not_found_handle () 
{ 
  if [ -x /usr/lib/command-not-found ]; then
    /usr/bin/python /usr/lib/command-not-found -- $1;
    return $?;
  else
    if [ -x /usr/share/command-not-found ]; then
      /usr/bin/python /usr/share/command-not-found -- $1;
      return $?;
    else
      return 127;
    fi;
  fi
}
```

## Shell字符串

字符串可以由单引号`' '`包围，也可以由双引号`" "`包围，也可以不用引号。它们之间是有区别的，稍后我们会详解。

下面我们说一下三种形式的区别：

1) 由单引号`' '`包围的字符串：

- 任何字符都会原样输出，在其中使用变量是无效的。
- 字符串中不能出现单引号，即使对单引号进行转义也不行。


2) 由双引号`" "`包围的字符串：

- 如果其中包含了某个变量，那么该变量会被解析（得到该变量的值），而不是原样输出。
- 字符串中可以出现双引号，只要它被转义了就行。


3) 不被引号包围的字符串

- 不被引号包围的字符串中出现变量时也会被解析，这一点和双引号`" "`包围的字符串一样。
- 字符串中不能出现空格，否则空格后边的字符串会作为其他变量或者命令解析。

### 获取字符串长度

在 Shell 中获取字符串长度很简单，具体方法如下：

${#string_name}

string_name 表示字符串名字。

下面是具体的演示：

```shell
str="http://c.biancheng.net/shell/"
echo ${#str}
```

运行结果：
29

### Shell字符串拼接

```shell
name="Shell"
url="http://c.biancheng.net/shell/"
str1=$name$url  #中间不能有空格
str2="$name $url"  #如果被双引号包围，那么中间可以有空格
str3=$name": "$url  #中间可以出现别的字符串
str4="$name: $url"  #这样写也可以
str5="${name}Script: ${url}index.html"  #这个时候需要给变量名加上大括号
echo $str1
echo $str2
echo $str3
echo $str4
echo $str5
```



### Shell字符串截取

| 格式                       | 说明                                                         |
| -------------------------- | ------------------------------------------------------------ |
| ${string#*chars}           | 从 string 字符串第一次出现 *chars 的位置开始，截取 *chars 右边的所有字符。 |
| ${string%%*chars}          | 从 string 字符串最后一次出现 *chars 的位置开始，截取 *chars 左边的所有字符。 |
| ${string##*chars}          | 从 string 字符串最后一次出现 *chars 的位置开始，截取 *chars 右边的所有字符。 |
| ${string%*chars}           | 从 string 字符串第一次出现 *chars 的位置开始，截取 *chars 左边的所有字符。 |
| ${string: start :length}   | 从 string 字符串的左边第 start 个字符开始，向右截取 length 个字符。 |
| ${string: start}           | 从 string 字符串的左边第 start 个字符开始截取，直到最后。    |
| ${string: 0-start :length} | 从 string 字符串的右边第 start 个字符开始，向右截取 length 个字符。 |
| ${string: 0-start}         | 从 string 字符串的右边第 start 个字符开始截取，直到最后。    |

假设有变量 var=http://www.aaa.com/123.htm.

**1. # 号截取，删除左边字符，保留右边字符。**

```shell
echo ${var#*//}
# www.aaa.com/123.htm
```

其中 var 是变量名，# 号是运算符，*// 表示从左边开始删除第一个 // 号及左边的所有字符
即删除 http://
结果是 ： www.aaa.com/123.htm

**2. ## 号截取，删除左边字符，保留右边字符。**

```shell
echo ${var##*/}
# 123.htm
```

\##*/ 表示从左边开始删除最后（最右边）一个 / 号及左边的所有字符
即删除 http://www.aaa.com/

结果是 : 123.htm

**3. %号截取，删除右边字符，保留左边字符**

```shell
echo ${var%/*}
# http://www.aaa.com
```

%/* 表示从右边开始，删除第一个 / 号及右边的字符

结果是：http://www.aaa.com

**4. %% 号截取，删除右边字符，保留左边字符**

```shell
echo ${var%%/*}
# http:
```

%%/* 表示从右边开始，删除最后（最左边）一个 / 号及右边的字符
结果是：http:

**5. 从左边第几个字符开始，及字符的个数**

```shell
echo ${var:0:5}
# http:
```

其中的 0 表示左边第一个字符开始，5 表示字符的总个数。
结果是：http:

**6. 从左边第几个字符开始，一直到结束。**

```shell
echo ${var:7}
# www.aaa.com/123.htm
```

其中的 7 表示左边第8个字符开始，一直到结束。
结果是 ：www.aaa.com/123.htm

**7. 从右边第几个字符开始，及字符的个数**

```shell
echo ${var:0-7:3}
# 123
```

其中的 0-7 表示右边算起第七个字符开始，3 表示字符的个数。
结果是：123

**8. 从右边第几个字符开始，一直到结束。**

```shell
echo ${var:0-7}
# 123.htm
```

表示从右边第七个字符开始，一直到结束。
结果是：123.htm

### 大小写转换

1. **typeset** 

有两个选项 -l 代表小写 -u 代表大写。

用法：

```shell
typeset -u name
name='asdasdas'
echo $name
typeset -l ame
ame='asdasdas'
echo $ame
```

结果：

```
ASDASDAS
asdasdas
```

2. **利用表达式**

```shell
echo 'hello' | tr 'a-z' 'A-Z'
echo 'HELLO' | tr 'A-Z' 'a-z'
```

结果：

```
HELLO
hello
```

## Shell数组

### Shell获取数组长度

### Shell数组拼接

### Shell删除数组元素

### Shell关联数组

## Shell内建命令

### Shell alias命令

### Shell echo命令

### Shell read命令

### Shell exit命令

### Shell declare和typeset命令

## Shell数学计算

### Shell (())

### Shell let命令

### Shell $[\]

### Shell expr命令

### Linux bc命令

### Shell declare -i

## 分支判断

### Shell if else

### Shell退出状态

### Shell test命令

### Shell [[\]]

### Shell case in

## 循环

### Shell while

### Shell until

### Shell for

### Shell select in

### Shell break和continue

## Shell函数

### Shell函数参数

### Shell函数返回值精讲



# Shell高级

1.[Shell重定向](http://c.biancheng.net/view/942.html)

2.[Linux中的文件描述符到底是什么？](http://c.biancheng.net/view/vip_3240.html)

3.[结合文件描述符谈重定向，彻底理解重定向的本质！](http://c.biancheng.net/view/vip_3241.html)

4.[使用exec命令操作文件描述符](http://c.biancheng.net/view/vip_3242.html)

5.[Shell代码块重定向](http://c.biancheng.net/view/vip_3243.html)

6.[Shell Here Document](http://c.biancheng.net/view/vip_3244.html)

7.[Shell Here String](http://c.biancheng.net/view/vip_3245.html)

8.[Shell组命令](http://c.biancheng.net/view/vip_3246.html)

9.[Shell进程替换](http://c.biancheng.net/view/vip_3247.html)

10.[Linux管道](http://c.biancheng.net/view/3131.html)

11.[Shell过滤器](http://c.biancheng.net/view/3472.html)

12.[子Shell和子进程到底有什么区别？](http://c.biancheng.net/view/vip_3248.html)

13.[如何检测子Shell和子进程？](http://c.biancheng.net/view/vip_3249.html)

14.[Linux中的信号是什么](http://c.biancheng.net/view/vip_3520.html)

15.[Bash Shell中的信号](http://c.biancheng.net/view/vip_3522.html)

16.[Linux进程简明教程](http://c.biancheng.net/view/vip_3521.html)

17.[使用什么命令查看进程](http://c.biancheng.net/view/vip_3495.html)

18.[Shell向进程发送信号](http://c.biancheng.net/view/vip_3497.html)

19.[使用trap命令获取信号](http://c.biancheng.net/view/vip_3499.html)

20.[trap命令捕获信号实例演示](http://c.biancheng.net/view/vip_3506.html)

21.[移除（重置）信号捕获](http://c.biancheng.net/view/vip_3507.html)

22.[关于进程、信号和捕获的总结](http://c.biancheng.net/view/vip_3508.html)

23.[Shell模块化（把代码分散到多个脚本文件中）](http://c.biancheng.net/view/vip_3250.html)

# Bash Shell快捷键

1.[Bash Shell快捷键大全](http://c.biancheng.net/view/vip_3509.html)

2.[Bash Shell命令自动补全功能](http://c.biancheng.net/view/vip_3510.html)

3.[Bash Shell历史命令](http://c.biancheng.net/view/vip_3512.html)
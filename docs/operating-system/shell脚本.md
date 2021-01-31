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

1. Shell变量

2.Shell变量的作用域

3.Shell命令替换

4.[Shell位置参数](http://c.biancheng.net/view/789.html)

5.[Shell特殊变量](http://c.biancheng.net/view/806.html)

6.[Shell $*和$@之间的区别](http://c.biancheng.net/view/vip_4559.html)

7.[Shell $?](http://c.biancheng.net/view/808.html)

8.[Shell字符串详解](http://c.biancheng.net/view/821.html)

9.[Shell字符串拼接](http://c.biancheng.net/view/1114.html)

10.[Shell字符串截取](http://c.biancheng.net/view/1120.html)

11.[Shell数组](http://c.biancheng.net/view/810.html)

12.[Shell获取数组长度](http://c.biancheng.net/view/812.html)

13.[Shell数组拼接](http://c.biancheng.net/view/818.html)

14.[Shell删除数组元素](http://c.biancheng.net/view/819.html)

15.[Shell关联数组](http://c.biancheng.net/view/vip_3234.html)

16.[Shell内建命令](http://c.biancheng.net/view/1136.html)

17.[Shell alias命令](http://c.biancheng.net/view/1138.html)

18.[Shell echo命令](http://c.biancheng.net/view/1142.html)

19.[Shell read命令](http://c.biancheng.net/view/2991.html)

20.[Shell exit命令](http://c.biancheng.net/view/1145.html)

21.[Shell declare和typeset命令](http://c.biancheng.net/view/2709.html)

22.[Shell数学计算](http://c.biancheng.net/view/1169.html)

23.[Shell (())](http://c.biancheng.net/view/2480.html)

24.[Shell let命令](http://c.biancheng.net/view/2504.html)

25.[Shell $[\]](http://c.biancheng.net/view/vip_3235.html)

26.[Shell expr命令](http://c.biancheng.net/view/vip_3236.html)

27.[Linux bc命令](http://c.biancheng.net/view/vip_3237.html)

28.[Shell declare -i](http://c.biancheng.net/view/vip_3238.html)

29.[Shell if else](http://c.biancheng.net/view/1262.html)

30.[Shell退出状态](http://c.biancheng.net/view/2735.html)

31.[Shell test命令](http://c.biancheng.net/view/2742.html)

32.[Shell [[\]]](http://c.biancheng.net/view/2751.html)

33.[Shell case in](http://c.biancheng.net/view/2767.html)

34.[Shell while](http://c.biancheng.net/view/1006.html)

35.[Shell until](http://c.biancheng.net/view/1007.html)

36.[Shell for](http://c.biancheng.net/view/2804.html)

37.[Shell select in](http://c.biancheng.net/view/2829.html)

38.[Shell break和continue](http://c.biancheng.net/view/1011.html)

39.[Shell函数](http://c.biancheng.net/view/1009.html)

40.[Shell函数参数](http://c.biancheng.net/view/2860.html)

41.[Shell函数返回值精讲](http://c.biancheng.net/view/vip_3239.html)



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
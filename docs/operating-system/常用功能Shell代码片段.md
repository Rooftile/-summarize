# 文本处理

##  统计词频

```shell
cat words.txt |tr -s ' ' '\n' |sort|uniq -c|sort -r|awk '{print $2,$1}'
```

1. 首先cat命令查看words.txt
2. tr -s ' ' '\n'将空格都替换为换行 实现分词
3. sort排序 将分好的词按照顺序排序
4. uniq -c 统计重复次数（此步骤与上一步息息相关，-c原理是字符串相同则加一，如果不进行先排序的话将无法统计数目）
5. sort -r 将数目倒序排列
6. awk '{print $2,$1}' 将词频和词语调换位置打印出来

```shell
cat words.txt | xargs -n 1 | sort | uniq -c | sort -nr | awk '{print $2" "$1}'
```

xargs 分割字符串 -n 1表示每行输出一个 可以加-d指定分割符

要使用uniq统计词频需要被统计文本相同字符前后在一起，所以先排序 uniq -c 表示同时输出出现次数

sort -nr 其中-n表示把数字当做真正的数字处理(当数字被当做字符串处理，会出现11比2小的情况)

```shell
cat words.txt | awk '{ 
    for(i=1;i<=NF;i++){
        count[$i]++
    } 
} END { 
    for(k in count){
        print k" "count[k]
    } 
}' | sort -rnk 2
```

先用cat命令和管道命令|将文件内容传给awk。

在awk中我们用一个字典(?)count储存每个单词的词频，先遍历每一行(awk自身机制)的每一个字段(i<=NF)，然后用该字段本身作为key,将其value++；最后用一个for循环输出count数组中的每个元素的key(词)及其value(词频)。

最后用|管道命令传给sort命令：

- -r是倒序排序，相当于DESC
- -n是将字符串当作numeric数值排序
- -k则指定用于排序的字段位置，后跟2指将第二位的count[k] (词频)作为排序的key

```shell
cat words.txt | sed 's/[ ][ ]*/\n/g' | egrep -v "^$"|sort | uniq -c | sort -nr | awk '{print $NF,$1}'
```

## 转置文件

假设 file.txt 文件内容如下：

```
name age
alice 21
ryan 30
```


应当输出：

```
name alice ryan
age 21 30
```

```shell
awk '{
    for (i=1;i<=NF;i++){
        if (NR==1){
            res[i]=$i
        }
        else{
            res[i]=res[i]" "$i
        }
    }
}END{
    for(j=1;j<=NF;j++){
        print res[j]
    }
}' file.txt
```



# 远程运行

# 组件安装
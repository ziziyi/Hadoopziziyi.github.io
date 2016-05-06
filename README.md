# Hadoopziziyi.github.linux
目前学习的参数
|命令参数|参数用法|
|:---|:---|
|echo $LANG env|查看linux字符编码   |
|cat student1.text, 敲:?student1定位到那个位置|快速查找文本文件里面的内容  编辑文件时候 :?查找内容|
|cat -n 文件名|grep 名称 |根据这个文件夹，找到名称，打印行号|
|tar -zxvf archive.tar -C /temp|将解压包到 /tmp目录下|
|tar -xvf  archive.tar -C /temp|将解压包到 /tmp目录下|
|tar -cvfj archive.tar.bz2 dir1|创建一个bzip2格式的压缩包 |
|tar -xvfj archive.tar.bz2|解压一个bzip2格式的压缩包|
|tar -cvfz archive.tar.gz dir1|创建一个gzip格式的压缩包|
|tar -xvfz archive.tar.gz| 解压一个gzip格式的压缩包|
|rpm -qa | grep httpd |显示所有名称中包含 "httpd" 字样的rpm包|

1.head (取出前面几行)
```
head -n 1 filename 取出前面多少行= head -n -3 filename 显示第一行的，后面的不显示
head -n -1 filename //取出前3行的，最后一行看不到
tail  n  3 filename 取最后3条 =tail  n -3 filename 显示倒数最后3条
tail  n +3 filename //从3开始显示数据
*设计到管线命令：取出这4条数据的中间2条数据，2和3
*首先取出这4条数，在取后3条数据，在去前2条数据
head -n 4 /opt/datas/student.csv | tail -n 3| head -n 2
*取出这4条数据的中间2条数据，3和4 
*在数据目录下查看总共条目数
wc -l ip_location.csv
*查看文件里面的内容
hdfs dfs -cat /usr/local/hbaseout/hfileoutput3/_SUCCESS | wc -l 
*查看文件条目数
 bin/hdfs dfs -cat /user/beifeng/hbaseout/ip_location.csv | head -20
* 查看硬盘大小
 hadoop fs -df -h
* 查看文件大小
  ls  -lht
```
2.cd (变换目录)
```
cd [相对路径或绝对路径]
cd .. 表示去到目前的上一级目录
 cd /var/spool/mail 这个就是绝对路径的写法
cd ../mqueue 这个是相对路径的写法
```

3.find [PATH] [option] [action]
```
find /jar路径 -name hadoop*hdfs*.jar
find /jar路径 -name hadoop*hbase*.jar	
-name filename：搜寻文件名称为 filename 的文件；
-size [+-]SIZE：搜寻比 SIZE 还要大(+)或小(-)的文件。这个 SIZE 的规格有：
                   c: 代表 byte， k: 代表 1024bytes。所以，要找比 50KB
                   还要大的文件，就是『 -size +50k 』
find /opt/datas/ -size +1k //例子
-type TYPE    ：搜寻文件的类型为 TYPE 的，类型主要有：一般正规文件 (f),
                   装置文件 (b, c), 目录 (d), 连结档 (l), socket (s), 
                   及 FIFO (p) 等属性。			
find /opt/datas/ -type f	//例子

```
4.读取文件：cat  [-AbEnTv]
```
-A  ：相当於 -vET 的整合选项，可列出一些特殊字符而不是空白而已；
-b  ：列出行号，仅针对非空白行做行号显示，空白行不标行号！
-E  ：将结尾的断行字节 $ 显示出来；
-n  ：列印出行号，连同空白行也会有行号，与 -b 的选项不同；
-T  ：将 [tab] 按键以 ^I 显示出来；
-v  ：列出一些看不出来的特殊字符
``` 
5.读取文件查看行号：nl  [-bnw] 文件
```
-b  ：指定行号指定的方式，主要有两种：
      -b a ：表示不论是否为空行，也同样列出行号(类似 cat -n)；
      -b t ：如果有空行，空的那一行不要列出行号(默认值)；
-n  ：列出行号表示的方法，主要有三种：
      -n ln ：行号在萤幕的最左方显示；
      -n rn ：行号在自己栏位的最右方显示，且不加 0 ；
      -n rz ：行号在自己栏位的最右方显示，且加 0 ；
-w  ：行号栏位的占用的位数。
```

####二.磁盘阵列
磁盘阵列全名是『 Redundant Arrays of Inexpensive Disks, RAID 』,
容错式廉价磁盘阵列.RAID可以透过一个技术(软件或硬件)，将多个较小的磁碟整合成为一个较大的磁碟装置；而这个较大的磁碟功能可不止是储存而已，他还具有数据保护的功能.

其实你的系统如果需要磁盘阵列的话，其实重点在於：
```
1.数据安全与可靠性：指的并非资讯安全，而是当硬件 (指磁碟) 损毁时，数据是否还能够安全的救援或使用之意；
2.读写效能：例如 RAID 0 可以加强读写效能，让你的系统 I/O 部分得以改善；
3.容量：可以让多颗磁碟组合起来，故单一文件系统可以有相当大的容量。
```   

    

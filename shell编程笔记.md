### 基础语法
* `#!/bash/bin` 开头指定解释器
* `#`用于注释
* 定义变量时不加`$`，且变量可以重复定义
* 使用变量 `${变量名} `，花括号可选，用来指定变量边界
* 单引号内的任意字符都会被原样输出，也就是值变量无效
* 双引号内可以有变量和转义字符， 例： ` \"  \"` 为转义的双引号
### 程序逻辑
#### 分支
#####  if
```
if condition
	then 
	command1
	command2
else-if	
	command3
else
	commadn4
fi
```
##### case
>case的语法和C family语言差别很大，它需要一个esac（就是case反过来）作为结束标记，每个case分支用右圆括号，用两个分号表示break
```
case "${opt}" in
	"install" )
		command1
		exit
		;;

	"uninstall" )
		command2
		exit
	;;

	"Exit" )
		exit
	;;

	* ) echo "Bad option, please choose again"
esac
```
#### 循环
##### for
```
for var in item1 item2 item3
do
	command1
	command2
done
```
##### while
```
while condition
do
	command1
	command2
done 
```

### 常见命令
#### select 
生成菜单
```
select DRINK in tea cofee water juice appe all none
do
   case $DRINK in
      tea|cofee|water|all) 
         echo "Go to canteen"
         ;;
      juice|appe)
         echo "Available at home"
      ;;
      none) 
         break 
      ;;
      *) echo "ERROR: Invalid selection" 
      ;;
   esac
done
```
 #### stdin/stdout 
输入输出重定向
`command1 < file1` 输入重定向
`command1 > file1` 输出重定向 
 #### ps 
 进程管理
`ps aux` 列出目前所有的正在内存当中的程序
#### grep/egrep 
过滤
`egrep -v` 显示除了匹配特定模式的行以外的所有行。
 #### awk 
 文本处理
`-F fs`   fs指定输入分隔符，fs可以是字符串或正则表达式
`$n ` 当前记录的第n个字段，比如n为1表示第一个字段，n为2表示第二个字段
#### sed 
文本文件编辑
[http://www.runoob.com/linux/linux-comm-sed.html](http://www.runoob.com/linux/linux-comm-sed.html)
#### curl 
网络工具
`curl http://www.codebelief.com > index.html `下载文件
`curl -O http://www.codebelief.com/page/2/ -O http://www.codebelief.com/page/3/`  同时下载多个文件
`curl -d "userName=tom&passwd=123456" -X POST http://www.example.com/login `发送POST请求



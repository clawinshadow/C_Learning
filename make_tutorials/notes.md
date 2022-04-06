# Notes of make tutorials
记录make学习过程中的一些笔记
## Makefile Syntax
Makefile
## demo1
`some_file`这个target没有任何依赖，它也没有生成任何文件，无法校验时间戳，所以它的command每次都会被执行
```C
some_file:
	echo "This line will always print"
```
## demo2
与demo1不同的是，它的target每次执行完了后会生成文件`some_file`，所以再次编译时会提示 `up to date`
```C
some_file:
	echo "This will just print once"
	touch some_file
```
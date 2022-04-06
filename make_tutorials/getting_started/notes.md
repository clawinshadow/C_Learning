## Beginning Examples
以下是一些demo
### demo1
`some_file`这个target没有任何依赖，它也没有生成任何文件，无法校验时间戳，所以它的command每次都会被执行
```C
some_file:
	echo "This line will always print"
```
### demo2
与demo1不同的是，它的target每次执行完了后会生成文件`some_file`，所以再次编译时会提示 `up to date`
```C
some_file:
	echo "This will just print once"
	touch some_file
```

### demo3
下面 some_file 依赖 other_file, 但是因为other_file没有生存任何文件，所以每次都需要重新编译
```C
some_file: other_file
	echo "Build some_file"
	touch some_file

other_file:
	echo "Build other_file"
```

### demo4
与demo3不同，demo4中因为每次生成了 `other_file` 文件，所以再次执行`make some_file`时两者均不用重新编译。

如果此时我手动修改了 `other_file` 的内容，比如 `echo "123" > other_file`

那么再次`make some_file`时，`other_file`这个target不会重新编译，`some_file`会重新编译

```C
some_file: other_file
	echo "Build some_file"
	touch some_file

other_file:
	echo "Build other_file"
	touch other_file
```

### demo5
`clean`是个约定俗成的target，一般用来清理各个target文件，以便后面进行全量编译。`clean`不是make的一个关键字，只是一种target命名的传统而已

```C
some_file: 
	echo "Building some_file"
	touch some_file

clean:
	rm -f some_file
```
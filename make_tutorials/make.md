# Notes of make tutorials
记录make学习过程中的一些笔记
## Makefile Syntax
使用make需要当前目录下存在一个Makefile，它由一个或多个 _`rules`_ 组成。每个 _`rule`_ 的格式大体如下：
```C
targets: prerequisites
	command
	command
	command
```
- The __targets__ are file names, separated by spaces. Typically, there is only one per rule.
- The __commands__ are a series of steps typically used to make the target(s). These need to start with a ___tab___ character, not spaces.
- The __prerequisites__ are also file names, separated by spaces. These files need to exist before the commands for the target are run. These are also called __dependencies__

其中依赖是个很重要的概念，在大型程序中，make不仅用来组织各个文件的编译，更重要的功能是根据每个target的依赖文件来校验时间戳，以便只有依赖文件有更新时，才做增量的编译，节省项目编译时间。

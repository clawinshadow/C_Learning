#  Notes of Chapter 2: C Fundamentals
关于C语言代码中的注释，要注意只有C99之后才支持`//...`这种写法, 比如gcc会给出这种报警信息
```C
main.c:1:1: warning: // comments are not allowed in this language [-Wcomment]
//
```
C99之前所有的变量声明必须在语句之前，两者不能混在一起
```C

int a = 1;
printf("a = %d\n", a);

int b = 2;
printf("b = %d\n", b);

--gcc compiling with -pedantic 
main.c:14:9: warning: ISO C90 forbids mixing declarations and code [-Wdeclaration-after-statement]
    int b = 2;
```
在定义宏的时候如果值是一个表达式，需要用括号括起来
```C
#define RECIPROCAL_OF_PI (1.0f / 3.1415926)
```

在`main`函数中，如果没有写`return`语句，那么在C89中，返回给操作系统的值将会是`unspecified value`；在C99之后，如果`main`函数的返回值类型被声明为`int`，则默认返回0，否则一样返回`unspecified value`

在C标准中注释会被替换为一个空格字符，所以下面的语句是非法的
```C
int a/*invalid comment*/b = 0;

-- equals to 

int a b = 0; // invalid statement
```

Old-style comments (using /* .. */) cannot be nested, 像下面这样会导致编译器报错

```C
/* 1111
    /*** 2222 ***/
*/
```


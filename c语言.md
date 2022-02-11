# C语言

 C 语言所产生的代码运行速度与汇编语言编写的代码运行速度几乎一样。

另一种是不需要建立存储空间的，通过使用**extern**关键字声明变量名而不定义它。 例如：extern int a 其中变量 a 可以在别的文件中定义的。

## 关键字

| 关键字   | 说明                                                        |
| -------- | ----------------------------------------------------------- |
| auto     | 声明自动变量                                                |
| break    | 跳出当前循环                                                |
| case     | 开关语句分支                                                |
| const    | 定义常量，如果一个变量被const修饰，那么它的值就不能再被改变 |
| continue | 结束当前循环，开始下一轮循环                                |
| default  | 开关语句中的“其他”分支                                      |
| do       | 循环语句的循环体                                            |
| double   | 声明双精度浮点型变量或函数返回值类型                        |
| else     | 条件语句否定分支（与if连用）                                |
| enum     | 声明枚举类型                                                |
| extern   | 声明变量或函数是在其他文件或本文件的其他位置定义            |
| float    | 声明浮点型变量或函数返回值类型                              |
| for      | 一种循环语句                                                |
| goto     | 无条件跳转语句                                              |
| if       | 条件语句                                                    |
| int      | 声明整型变量或函数                                          |
| long     | 声明长整型变量或函数返回值类型                              |
| register | 声明寄存器变量                                              |
| return   | 子程序返回语句（可以带参数，也可不带参数）                  |
| short    | 声明有符号类型变量或函数                                    |
| signed   | 声明有符号类型变量或函数                                    |
| sizeof   | 计算数据类型或变量长度（即所占字节数）                      |
| static   | 声明静态变量                                                |
| struct   | 声明结构体类型                                              |
| switch   | 用于开关语句                                                |
| typedef  | 用以给数据类型取别名                                        |
| unsigned | 生命无符号类型变量和函数                                    |
| union    | 声明共用体类型                                              |
| void     | 声明函数为返回值或无参数，声明无类型指针                    |
| volatile | 说明变量在程序执行中可被隐含的改变                          |
| while    | 循环语句的循环条件                                          |

## sizeof

```c
#include <stdio.h>
#include <limits.h>

int main()
{
    printf("char 存储大小：%lu\n", sizeof(char));   //1
    printf("short 存储大小：%lu\n", sizeof(short)); //2
    printf("int 存储大小：%lu\n", sizeof(int));     //4
    printf("long 存储大小：%lu\n", sizeof(long));                   //8
    printf("unsigned long 存储大小：%lu\n", sizeof(unsigned long)); //8
    return 0;
}
```



## 变量

```c
#include <stdio.h> //预处理指令，告诉c编译器在实际编译之前要包含的文件

// 函数外定义变量x和y
int x, y;
int addTowNum()
{
    // 函数内声明变量x和y为外部变量
    extern int x, y;
    // 给外部变量（全局变量）x和y赋值
    x = 1;
    y = 2;
    return x + y;
}

int main()
{
    int result;
    // 调用函数 addTwoNum
    result = addTowNum();
    printf("result = %d \n", result);
    return 0;
}

//gcc var.c
//result = 3
```



addtwonum.c

```c
#include <stdio.h>

// 外部变量声明
extern int x, y;
int addtwonum()
{
    return x + y;
}
```

test.c

```c
#include <stdio.h>

// 定义两个全局变量
int x = 1, y = 2;
int addtwonum();
int main(void)
{
    int result;
    result = addtwonum();
    printf("result = %d \n", result);
    return 0;
}

//gcc addtwonum.c test.c -o main
```



## 常量

整数常量可以使十进制、八进制、或十六进制的常量。前缀指定基数：0x或0X表示十六进制，0表示八进制，不带前缀则默认表示十进制。

整数常量也可以带一个后缀，后缀是U和L的组合，**U表示无符号整数，L表示长整数**。后缀可以是大写，也可以是小写，U和L的顺序任意。

浮点常量，带符号的指数使用**e或E**引入的。

### 定义常量

```c
#include <stdio.h>

// 子贡问曰：“有一言可以终身行之者乎？”子曰：“其‘恕’乎！已所不欲，勿施于人。”
#define LENGTH 10
#define WIDTH 5
#define NEWLINE '\n'
#define KONG "子贡问曰：“有一言可以终身行之者乎？”子曰：“其‘恕’乎！已所不欲，勿施于人。”"

void main()
{
    int area;

    area = LENGTH * WIDTH;
    printf("value of area:%d", area);
    printf("%c", NEWLINE);
    printf("%s", KONG);
    printf("%c", NEWLINE);

    // -------------------------------------------

    const int LENGTH2 = 10;
    const int WIDTH2 = 10;
    const char NEWLINE2 = '\n';

    area = LENGTH2 * WIDTH2;
    printf("value of area:%d", area);
    printf("%c", NEWLINE);
    printf("%s", KONG);
    printf("%c", NEWLINE);
}

```

## 存储类

### static

```c
#include <stdio.h>

// 函数声明
void func1(void);

static int count = 10; //全局变量

int main(int argc, char const *argv[])
{
    while (count--)
    {
        func1();
    }

    return 0;
}

void func1(void)
{
    static int thingy = 5;
    thingy++;
    printf("thingy 为 %d , count为 %d \n",thingy,count);
}

```



### extern

```c
//support.c
#include <stdio.h>

extern int count;

void write_extern(void){
    printf("count is %d \n",count);
}

//main.c
#include <stdio.h>

int count;
extern void write_extern();

int main(int argc, char const *argv[])
{
    count = 5;
    write_extern();
    return 0;
}

```

## 运算符s







## 函数

```c
#include <stdio.h>
#include <float.h>

// 函数声明
float max(int num1, int num2);

void main()
{
    float a = 100.1, b = 200.22;
    float ret;

    ret = max(a, b);
    printf("Max = %f\n", ret);
}

// 函数返回两个数中较大的那个数
float max(int num1, int num2)
{
    // 局部变量声明
    float result;

    if (num1 > num2)
    {
        result = num1;
    }
    else
    {
        result = num2;
    }
    return result;
}
```



## 枚举

*没有指定值的枚举元素，其值为前一元素加 1*



## 指针

指针也就是内存地址，指针变量是用来存放内存地址的变量。就像其它变量或常量一个，必须在使用指针存储其他变量地址之前，对其进行声明。

星号* 是用来制定一个变量的指针。

每一个变量都有一个内存位置，每一个内存位置都定义了可使用&运算符访问地址，它表示了在内存中的一个地址。



## 函数指针与回调函数

https://www.runoob.com/w3cnote/c-callback-function.html

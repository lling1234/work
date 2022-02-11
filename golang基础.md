# 1.环境搭建

## 1.1 Go 语言环境安装

如果打不开可以使用这个地址：<https://golang.google.cn/dl/>。

VMware中Ubuntu18.04安装 VMware Tools  

Ubuntu18.04.3虚拟机安装步骤（图文教程，非常详细！！！）

https://blog.csdn.net/qq_42372031/article/details/100588245?utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-10.base&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-10.base

linux安装go

[]: https://blog.csdn.net/weixin_42031162/article/details/107190041?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522162572775816780262561696%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&amp;request_id=162572775816780262561696&amp;biz_id=0&amp;utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-107190041.first_rank_v2_pc_rank_v29_1&amp;utm_term=ubuntu%E5%AE%89%E8%A3%85go&amp;spm=1018.2226.3001.4187

sudo tar -C /usr/local -xzf go1.16.5.linux-amd64.tar

windows安装目录   D:\ling\Go  工作目录 D:\ling\Go_WorkSpace

```go
package main

import "fmt"

func main(){
    fmt.Println("hello,ling")
}
```

开发工具使用vscode

## 1.2语言结构

当标识符（包括常量、变量、类型、函数名、结构字段等等）以一个大写字母开头，如：Group1，那么使用这种形式的标识符的对象就可以被外部包的代码所使用（客户端程序需要先导入这个包），这被称为导出（像面向对象语言中的 public）；标识符如果以小写字母开头，则对包外是不可见的，但是他们在整个包的内部是可见并且可用的（像面向对象语言中的 protected ）。



# 2.基础语法

每个语句不需要以分号;结尾，go编译器自动完成。

若果将多个语句写在同一行，必须使用；区分，实际开发不鼓励，定义变量、更改变量值、输出语句等后面加上；结尾也不报错。

```go
package main

import (
	"fmt"
)

func main(){
	//%d 表示整型数字，%s表示字符串
	var stockcode=123
	var enddate="2021-7-7 15:17:52"
	var url="Code=%d&endDate=%s"
	var target_url=fmt.Sprintf(url,stockcode,enddate)
    fmt.Println(target_url)
}

//输出结果为：
//Code=123&endDate=2021-7-7 15:17:52

```

单行注释// 多行注释/*   */

无效的标识符：

- 1ab(以数字开头)
- case(个语音的关键字)
- a+b(运算符是不允许的)

字符串用 + 拼接   fmt.Println("Google" + "Runoob")

Go 语言中变量的声明必须使用空格隔开 var age int;

## 2.1 格式化字符串 Sprintf（字符串拼接）

```go
   // %d 表示整型数字，%s 表示字符串
    var stockcode=123
    var enddate="2020-12-31"
    var url="Code=%d&endDate=%s"
    var target_url=fmt.Sprintf(url,stockcode,enddate)
    fmt.Println(target_url)
```



# 3.数据类型

## 3.1 数字类型

| 序号 | 类型和描述                                                   |
| ---- | ------------------------------------------------------------ |
| 1    | uint8 无符号8位整型（0到255）                                |
| 2    | unit16 无符号16位整型（0到65535）                            |
| 3    | unit32 无符号32位整型(0 到 4294967295)                       |
| 4    | unit64 无符号64位整型(0 到 18446744073709551615)             |
| 5    | int8 有符号8位整型（-128到127）                              |
| 6    | int16 有符号16位整型(-32768 到 32767)                        |
| 7    | int32 有符号 32 位整型 (-2147483648 到 2147483647)           |
| 8    | int64 有符号 64 位整型 (-9223372036854775808 到 9223372036854775807) |

## 3.2 浮点型

| 序号 | 类型和描述                    |
| ---- | ----------------------------- |
| 1    | float32 IEEE-754 32位浮点型数 |
| 2    | float64 IEEE-754 64位浮点型数 |
| 3    | complex64 32位实数和虚数      |
| 4    | complex128 64位实数和虚数     |

实数包括：

- 整数 ： 像 0、1、2、3、-1、-2 等等。
- 有理数： 像 3/4、0.125、0.333……、1.1 等等。
- 无理数：想 **π** , √2 等等。

虚数的定义：虚数的平方是负数。如：

![img](https://gitee.com/ling66611/picgo-image/raw/master/master/20201204164934668.png)

但是，正数的平方是正数、负数的平方也是正数，也就是一个数的平方永远是正数或零。

复数是实数和虚数的组合：

![img](https://gitee.com/ling66611/picgo-image/raw/master/master/20201204164708410.gif)

如： 1 + i、 39 + 3i、 0.8 − 2.2i、  −2 +  π i、  √2 + i/2

注意：复数是两个数加起来的，一个是实数部分，一个是虚数部分。 但这两部分都可以是  0 ，所以所有实数和虚数都是复数。


## 3.3其他数字类型



| 序号 | 类型和描述                           |
| ---- | ------------------------------------ |
| 1    | byte 类似uint8                       |
| 2    | rune 类似int32                       |
| 3    | uint 32或64位                        |
| 4    | int 与uint一样大                     |
| 5    | uintptr 无符号整型，用于存放一个指针 |



但是全局变量是允许声明但不使用的

如果你想要交换两个变量的值，则可以简单地使用 **a, b = b, a**，两个变量的类型必须是相同。

空白标识符 _ 也被用于抛弃值，如值 5 在：_, b = 5, 7 中被抛弃。



# 4.变量

- 以下几种类型为 **nil**：

  ```go
  var a *int
  var a []int
  var a map[string] int
  var a chan int
  var a func(string) int
  var a error // error 是接口
  ```

## 4.1声明全局变量

全局变量允许声明但不使用的。

```go
// 这种因式分解关键字的写法一般用于声明全局变量
var (
    vname1 v_type1
    vname2 v_type2
)
```

## 4.2值类型和引用类型

 值类型包括：int、float、bool 、string 、数组和结构体；

值类型：变量直接存储值，内存通常在栈中分配；

引用类型包括：指针、slice切片、map、管道chan、interface等；

引用类型：变量存储一个地址，地址对应的空间才真正存储数据（值），内存通常在堆上分配。当没有任何变量引用这个地址时，该地址对应的数据空间就成为一个垃圾，由GC来回收；

![4.4.2_fig4.1](https://www.runoob.com/wp-content/uploads/2015/06/4.4.2_fig4.1.jpgrawtrue)

当使用等号 `=` 将一个变量的值赋值给另一个变量时，如：`j = i`，实际上是在**内存中将 i 的值进行了拷贝**：

![4.4.2_fig4.2](https://www.runoob.com/wp-content/uploads/2015/06/4.4.2_fig4.2.jpgrawtrue)

定义的变量、导入的包如果没有使用会报错。

空白标识符 _ 也被用于抛弃值，如值 5 在：_, b = 5, 7 中被抛弃。

# 5.常量

常量中的数据类型只可以是布尔型、数字型（整数型、浮点型和复数）和字符串型。

- 显式类型定义： `const b string = "abc"`
- 隐式类型定义： `const b = "abc"`

常量还可以用作枚举：

```go
const (
    Unknown = 0
    Female = 1
    Male = 2
)
```

## 5.1 iota

ota，特殊常量，可以认为是一个可以被编译器修改的常量。

iota 在 const关键字出现时将被重置为 0(const 内部的第一行之前)，const 中每新增一行常量声明将使 iota 计数一次(iota 可理解为 const 语句块中的行索引)。

第一个 iota 等于 0，每当 iota **在新的一行被使用时，它的值都会自动加 1**；所以 a=0, b=1, c=2 可以简写为如下形式：

```go
const (
    a = iota
    b
    c
)
```



# 6.运算符

## 6.1 位运算符

![1625800862350](https://gitee.com/ling66611/picgo-image/raw/master/master/1625800862350.png)



## 6.2 其他运算符

| 运算符 | 描述             | 实例                     |
| ------ | ---------------- | ------------------------ |
| &      | 返回变量储存地址 | &a；将给出变量的实际地址 |
| *      | 指针变量         | *a;是一个指针变量        |







## Go语言的格式化输出中%d%T%v%b等的含义

![1625651429541](https://gitee.com/ling66611/picgo-image/raw/master/master/1625651429541.png)

![在这里插入图片描述](https://gitee.com/ling66611/picgo-image/raw/master/master/20181108105759217.png)

![在这里插入图片描述](https://gitee.com/ling66611/picgo-image/raw/master/master/20181108105900423.png)

Printf会把%d转义，Println不会。



operator3 	c = 200; 后面加分号了没有报错，编译器会删除或自动补充；分号。





# 7.条件语句

if 

if……else

if嵌套语句

switch语句

select语句

**select**是Go中的一个控制结构，类似于用于通信的 **switch** 语句。每个case必须是一个通信操作，要么是发送要么是接收。

select**会随机执行一个可运行的case**。如果没有case可运行，它将阻塞，直到有case可运行。一个默认的子句应该总是可运行的。

*注意：Go 没有三目运算符，所以不支持* **?:** *形式的条件判断。*

# 8.循环语句

syntax error: non-declaration statement outside function body

语法错误:函数体外的非声明语句

## 8.1 for

```go
func main() {
        sum := 0
        for i := 0; i <= 10; i++ {
                sum += i
        }
        fmt.Println(sum)
}
```



## 8.2 For- range 循环

```go
package main
import "fmt"

func main() {
        strings := []string{"google", "runoob"}
        for i, s := range strings {
                fmt.Println(i, s)
        }


        numbers := [6]int{1, 2, 3, 5}
        for i,x:= range numbers {
                fmt.Printf("第 %d 位 x 的值 = %d\n", i,x)
        }  
}
```

以上实例运行输出结果为:

```
0 google
1 runoob
第 0 位 x 的值 = 1
第 1 位 x 的值 = 2
第 2 位 x 的值 = 3
第 3 位 x 的值 = 5
第 4 位 x 的值 = 0
第 5 位 x 的值 = 0
```

# 9.函数

## 9.1 函数参数

函数如果使用参数，该变量可称为函数的形参。

形参就像定义在函数体内的局部变量。

调用函数，可以通过两种方式来传递参数：

| 传递类型 | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| 值传递   | 值传递是指在调用函数时将实际参数复制一份传递到函数中，这样**在函数中如果对参数进行修改，将不会影响到实际参数。** |
| 引用传递 | 引用传递是指在调用函数时将实际参数的地址传递到函数中，那么**在函数中对参数所进行的修改，将影响到实际参数。** |

默认情况下，go语言使用的是值传递，即在调用过程中不会影响到实际参数。

值传递浅拷贝，引用传递会影响到实际参数。

```go
func main() {
   /* 定义局部变量 */
   var a int = 100
   var b int= 200

   fmt.Printf("交换前，a 的值 : %d\n", a )
   fmt.Printf("交换前，b 的值 : %d\n", b )

   /* 调用 swap() 函数
   * &a 指向 a 指针，a 变量的地址
   * &b 指向 b 指针，b 变量的地址
   */
   swap(&a, &b)

   fmt.Printf("交换后，a 的值 : %d\n", a )
   fmt.Printf("交换后，b 的值 : %d\n", b )
}

func swap(x *int, y *int) {
   var temp int
   temp = *x    /* 保存 x 地址上的值 */
   *x = *y      /* 将 y 值赋给 x */
   *y = temp    /* 将 temp 值赋给 y */
}
```

## 9.2 函数作为实参？

看不懂

```go
package main
import "fmt"

// 声明一个函数类型
type cb func(int) int
//函数作为参数传递，实现回调。
func main() {
    testCallBack(1, callBack)
    testCallBack(2, func(x int) int {
        fmt.Printf("我是回调，x：%d\n", x)
        return x
    })
}

func testCallBack(x int, f cb) {
    f(x)
}

func callBack(x int) int {
    fmt.Printf("我是回调，x：%d\n", x)
    return x
}
//我是回调，x：1
// 我是回调，x：2
```



# 10.变量作用域

作用域为已声明标识符所表示的常量、类型、变量、函数或包在源代码中的作用范围。

Go 语言中变量可以在三个地方声明：

- 函数内定义的变量称为局部变量
- 函数外定义的变量称为全局变量
- 函数定义中的变量称为形式参数

局部变量

```go
//声明局部变量
var a, b, c int

//初始化参数
a = 20
b = 11
c = a + b
```

全局变量

在函数体外声明的变量，可以在整个包甚至外部包使用。

```go
package main

import "fmt"

/* 声明全局变量 */
var g int

func main() {

   /* 声明局部变量 */
   var a, b int

   /* 初始化参数 */
   a = 10
   b = 20
   g = a + b

   fmt.Printf("结果： a = %d, b = %d and g = %d\n", a, b, g)
}
```



```go
package main

import "fmt"

//声明全局变量
var g int = 20

func main() {
    //声明局部变量
    var g int = 10
     fmt.Printf ("结果： g = %d\n",  g)
}
```

以上实例执行输出结果为：

```
结果： g = 10
```



形式参数

形式参数会作为函数的局部变量来使用。

```go
package main

import "fmt"

//声明全局变量
var a int = 20

func main() {
    //main函数中声明局部变量
    var a int = 10
    var b int = 20
    var c int = 0
    
   fmt.Printf("main()函数中 a = %d\n",  a);
   c = sum( a, b);
   fmt.Printf("main()函数中 c = %d\n",  c);
}

//函数定义-两数之和
func sum(a,b int) int {
   fmt.Printf("sum() 函数中 a = %d\n",  a);
   fmt.Printf("sum() 函数中 b = %d\n",  b);

   return a + b;
}
```

a=

初始化局部变量和全局变量

| 数据类型 | 初始化默认值 |
| -------- | ------------ |
| int      | 0            |
| float    | 0            |
| pointer  | nil          |





# 11.数组

float32默认精度为6（ 后面保留6位小数）   balance2[0] = 1000.000000

```go
package main

import "fmt"

func main() {
	var i,j,k int
	//声明数组的同时快速初始化数组
	balance := [5]float32{1000.0, 2.0, 3.4, 7.0, 55.12}

	//输出数组元素
	for i = 0; i < 5; i++ {
		fmt.Printf("balance[%d] = %f\n", i, balance[i])
	}
	fmt.Println("--------------")

	balance2 := [...]float32{1000.02, 20.22, 3.33, 7.11, 50.00}
	//输出每个数组元素的值
	for j = 0; j < 5; j++ {
		fmt.Printf("balance2[%d] = %f\n", j, balance2[j] )
	}
	fmt.Println("--------------")
	
	//将索引为1和3的元素初始化
	balance3 := [5]float32{1:2.22,3:4.04}
	for k = 0; k < 5; k++ {
		fmt.Printf("balance3[%d] = %f\n", k, balance3[k] )
	}
}
```

## 二维数组

```go
package main

import "fmt"

func main() {
	// //创建二维数组
	// sites := [2][2]string{}

	// //向二维数组添加元素
	// sites[0][0] = "hello"
	// sites[0][1] = "google"
	// sites[1][0] = "ling"
	// sites[1][1] = "yunjivision"

	// fmt.Println(sites)

	//--------------------------------------------

	// //数组5行2列
	// var a = [5][2]int{{0,0},{1,2},{2,4},{3,6},{4,8}}
	// var i, j int

	// //输出数组元素
	// for i = 0; i < 5; i++ {
	// 	for j = 0; j < 2; j++ {
	// 		fmt.Printf("a[%d][%d] = %d\n", i, j, a[i][j] )
	// 	}
	// }

	//--------------------------------------------
	//创建监控的二维数组
	animals := [][]string{}

	//创建三个一维数组，各数组长度不同
	row1 := []string{"fish", "shark", "eel" }
	row2 := []string{"bird" }
	row3 := []string{"google", "ling" }

	//使用append()函数将一维数组添加到二维数组中
	animals = append(animals, row1 )
	animals = append(animals, row2 )
	animals = append(animals, row3 )

	//循环输出
	for i := range animals {
		fmt.Printf("row: %v\n", i)
		fmt.Println(animals[i])
	}

}
```

for i := range animals { ... } 和java的foreach（增强for循环 for(int x:arr){...}）有点相似。



数字可以用_下划线分割    fmt.Println(float64(c) / 1_000_000 ) 



# 12.指针

一个指针变量指向一个值的内存地址。

```go
int a int = 20 //声明实际变量
var ip *int //声明指针变量

ip = &a
fmt.Printf("a 变量的地址是：%x\n", &a)

//指针变量的储存地址
fmt.Printf("ip 变量存储的指针地址：%x\n", ip)

//使用指针访问值
fmt.Printf("ip 变量的值：%d\n", *ip)

```

以上实例执行输出结果为：

```
a 变量的地址是: 20818a220
ip 变量储存的指针地址: 20818a220
*ip 变量的值: 20
```

go指针不能进行偏移和运算，是安全指针。

3个概念：指针地址、指针类型和指针取值

go语言中的函数传参都是值拷贝，传递数据使用指针，而无须拷贝数据。2个符号：&（取地址）和*（根据地址取值）。

值类型：int、float、bool、string、array、struct

### 空指针

- 当一个指针被定义后没有分配到任何变量时，它的值为 nil

```go
	var p *string
	fmt.Println(p)
	fmt.Printf("p的值是%v\n", p)
	if p != nil {
		fmt.Println("非空")
	} else{
		fmt.Println("空值")
```

## 指向指针的指针

```go
package main

import "fmt"

func main() {

	var a int
	var ptr *int
	var pptr **int

	a = 3000

	// 指针 ptr 地址
	ptr = &a

	//指向 ptr 地址
	pptr = &ptr

	fmt.Printf("变量 a = %d\n", a )
	fmt.Printf("指针变量 *ptr = %d\n", *ptr )
	fmt.Printf("指向指针的指针变量 *pptr = %d\n", **pptr )


}
```



## new和make

## new

内建函数，用于分配内存，第一个参数是类型，返回值是**类型的指针**（返回值是一个指向新分配类型零值的指针），其值被初始化为“零”

```go
package main
import "fmt"
 
func main() {
	id := new(int)
	name := new(string)
	flag := new(bool)
	fmt.Printf("id type: %T  value: %v\n", id, *id)
	fmt.Printf("name type: %T  value: %v\n", name, *name)
	fmt.Printf("flag type: %T  value: %v\n", flag, *flag)
}
```

输出：

```Go
id type: *int  value: 0
name type: *string  value: 
flag type: *bool  value: false
```

从上述例子可以看到，初始化的“零”值根据类型不同而不同，整数初始化为 0，字符串初始化为空，bool类型初始化为 false。 

## make

内建函数，仅用于分配和初始化slice、map以及channel类型的对象，三种类型都是结构。返回值为类型（具体传入的类型），而不是指针。

```go
package main

import (
	"fmt"
)

func main() {

	// new（） 用于分配内存，返回值是类型的指针
	id := new(int)
	name := new(string)
	flag := new(bool)
	fmt.Printf("id type: %T value: %v\n", id, *id)
	fmt.Printf("name type: %T value: %v\n", name, *name)
	fmt.Printf("flag type: %T value: %v\n", flag, *flag)

	// make()仅用于分配和初始化slice、map以及channel类型的对象，
	// 三种类型都是结构。返回值为类型，而不是指针
	//map
	fmt.Println("map:")
	var nameId = make(map[string]int, 0)
	fmt.Printf("nameId \ntype:%#v\n", nameId)
	nameId["golang"] = 1
	nameId["cpp"] = 2
	nameId["java"] = 3

	for name, id := range nameId {
		fmt.Printf("name = %v,id = %v\n", name, id)
	}

	// slice
	var hobby = make([]string, 2, 100) //其中2是长度，100是容量
	hobby[0] = "打篮球"
	hobby[1] = "羽毛球"
	fmt.Println("\nslice:")
	fmt.Printf("length = %v caps = %v\n", len(hobby), cap(hobby))
	for _, name := range hobby {
		fmt.Println(name)
	}

	// chan
	ch := make(chan int, 3)
	ch <- 1
	ch <- 33
	ch <- 12
	close(ch)
	fmt.Println("\nchannel:")
	for v := range ch {
		fmt.Println(v)
	}
}

```

输出

```go
[root@localhost test]# go run main.go 
map:
nameId 
type: map[string]int{}
name = Golang, id = 1
name = C++, id = 2
name = PHP, id = 3
 
slice:
length = 2  caps = 100
打篮球
乒乓球
 
channel:
1
2
8
[root@localhost test]#
```

## new和make的区别

2. 都是在**堆上分配内存**；
2. new对指针类型分配内存，返回值是分配类型的指针，new不能直接对slice、map、channel分配内存；
3. make仅用于slice、map和channel的初始化，返回值为类型本身，而不是指针；

# 13.结构体

%d就是普通的输出了
%2d是将数字按宽度为2，采用右对齐方式输出，若数据位数不到2位，则左边补空格
%02d，和%2d差不多，只不过左边补0
%.2d没见过，但从执行效果来看，和%02d一样



# 14.切片？

### 1.1.5. 超出原 slice.cap 限制，就会重新分配底层数组，即便原数组并未填满。？

```go
package main

import (
    "fmt"
)

func main() {

    data := [...]int{0, 1, 2, 3, 4, 10: 0}
    s := data[:2:3]

    s = append(s, 100, 200) // 一次 append 两个值，超出 s.cap 限制。

    fmt.Println(s, data)         // 重新分配底层数组，与原数组无关。
    fmt.Println(&s[0], &data[0]) // 比对底层数组起始指针。

}
```

输出结果:

```
    [0 1 100 200] [0 1 2 3 4 0 0 0 0 0 0]
    0xc4200160f0 0xc420070060
```

从输出结果可以看出，append 后的 s 重新分配了底层数组，并复制数据。如果只追加一个值，则不会超过 s.cap 限制，也就不会重新分配。 通常以 2 倍容量重新分配底层数组。在大批量添加数据时，建议一次性分配足够大的空间，以减少内存分配和数据复制开销。或初始化足够长的 len 属性，改用索引号进行操作。及时释放不再使用的 slice 对象，避免持有过期数组，造成 GC 无法回收。



`len()`可以用来查看数组或slice的长度

`cap()`可以用来查看数组或slice的容量

### 1.1.6. slice中cap重新分配规律：？

```go
package main

import (
    "fmt"
)

func main() {

    s := make([]int, 0, 1)
    c := cap(s)

    for i := 0; i < 50; i++ {
        s = append(s, i)
        if n := cap(s); n > c {
            fmt.Printf("cap: %d -> %d\n", c, n)
            c = n
        }
    }

}
```

输出结果:

```
    cap: 1 -> 2
    cap: 2 -> 4
    cap: 4 -> 8
    cap: 8 -> 16
    cap: 16 -> 32
    cap: 32 -> 64
```

英文字符byte 中间字符rune

```go
 str := "Hello world"
    s := []byte(str) //中文字符需要用[]rune(str)
```

```go
 str := "你好，世界！hello world！"
    s := []rune(str) 
```



golang slice data[:6:8] 两个冒号的理解

常规slice , data[6:8]，从第6位到第8位（返回6， 7），长度len为2， 最大可扩充长度cap为4（6-9）

另一种写法： data[:6:8] 每个数字前都有个冒号， slice内容为data从0到第6位，长度len为6，最大扩充项cap设置为8

a[x:y:z] 切片内容 [x:y] 切片长度: y-x 切片容量:z-x



# 15.map

底层哈希表

 key := fmt.Sprintf("stu%02d", i) //生成stu开头的字符串



# 16.异常处理

Recover 是一个Go语言的内建函数，可以让进入宕机流程中的 goroutine 恢复过来，recover 仅在延迟函数 defer 中有效，在正常的执行过程中，调用 recover 会返回 nil 并且没有其他任何效果，如果当前的 goroutine 陷入恐慌，调用 recover 可以捕获到 panic 的输入值，并且恢复正常的执行。



# 17.网络编程





# 18.并发编程

## 18.1  goroutine

进程---》线程---》协程

协程：**独立**的**栈空间**，**共享堆空间**，调度由用户自己控制，本质上有点类似于用户级线程，这些用户级线程的调度也是自己实现的。
线程：一个**线程**上可以跑**多个协程**，**协程是轻量级的线程**，占用CPU资源少。

并发：在一个CPU上，比如有10个线程，每个线程执行10毫秒（进行轮询操作），从人的角度看，好像这10个线程都在运行，但是从微观上看，在某一个时间点看，其实只有一个线程在执行。

并行：在多个CPU上（10个），比如有10个线程，每个线程执行10毫秒（各自在不同CPU上执行），从人的角度看，这10个线程都在运行，但是从微观上看，在某个时间点看，也同时有10个线程在执行。

go协程特点：

1. 有独立的栈空间
2. 共享程序的堆控件
3. 调度由用户控制
4. 协程是轻量级的线程

goroutine

runtitme.Gosched() 让出CPU时间片，重新等待安排任务

runtime.Goexit() 退出当前协程

### runtime.GOMAXPROCS

Go运行时的调度器使用GOMAXPROCS参数来确定需要使用多少个OS线程来同时执行Go代码。默认值是机器上的CPU核心数。例如在一个8核心的机器上，调度器会把Go代码同时调度到8个OS线程上

Go语言中的操作系统线程和goroutine的关系：

- 1.一个操作系统线程对应用户态多个goroutine。
- 2.go程序可以同时使用多个操作系统线程。
- 3.goroutine和OS线程是多对多的关系，即m:n。

## 18.2 goroutine的调度模型---MGP

- M:操作系统的主线程（物理线程）
- P:协程执行需要的上下文
- G：协程

## 18.3 管道channel

介绍

1. 协程之间的通信
2. 本质是数据结构-队列，FIFO
3. 线程安全，多个goroutine访问时，不需要加锁，就是说channel本身就是线程安全的
4. channel有类型的，int类型的只能存放int数据类型
5. 引用类型，必须初始化才能写入数据，make后才能使用

管道读写，只读，只写

- 读写：var chan1 chan int
- 只读：var chan2 chan<- int
- 只写：var chan3 <-chan int

<- 前只写，后只读

## 18.4 协程安全

once       sync.Once
uartMtx    sync.Mutex 互斥锁（自旋锁）

cfgCurrentMutex sync.RWMutex                 //当前配置文件读写锁

# 19.面对对象

## 结构体

- Go语言的结构体(struct)和其它编程语言的类(class)有同等的地位
- 基于struct来实现OOP特性的
- 继承是通过匿名字段来实现

结构体是值类型，默认为值拷贝。

.的优先级比*高。

继承

```go
type A struct { }
type B struct {
    A
}

```

### 结构体使用的注意事项

1. 结构体的所有字段在内存中是连续的。

2. 结构体是用户单独定义的类型，和其它类型进行转换时需要有完全相同的字段（名字、个数和类型）。

3. 结构体进行type重新定义（相当于取别名），golang认为是新的数据类型，但是相互间可以强转。

   ```go
   type integer int
   func main(){
       var i integer = 10
       var j int 20
       j=int(i)
   }
   ```


## 方法

Default方法和ImageTarget类型绑定

```go
// ImageTarget 热成像图像目标参数
type ImageTarget struct {
	Enable         bool    `description:"使能"`
	Emissivity     float32 `description:"发射率"`
	ReflectedTemp  float32 `description:"反射温度"`
	AtmosphereTemp float32 `description:"大气温度"`
	Distance       float32 `description:"目标距离"`
	Transmittance  float32 `description:"大气透过率"`
}

// (it *ImageTarget)  
// 1.Default方法和ImageTarget类型绑定
// 2.类的实现方法
func (it *ImageTarget) Default() {
	it.Enable = false
	it.AtmosphereTemp = 298.2
	it.Emissivity = 1
	it.Distance = 0.5
	it.ReflectedTemp = 298.2
	it.Transmittance = 1
}
```

函数和方法的区别：

1. 调用方式不同

   函数的调用方式：	函数名（实参列表）

   方法的调用方式：	变量.方法名（实参列表）

2. 对于普通函数，接受者为值类型时，不能将指针类型的数据直接传递，反之亦然。

3. 对于方法（如struct的方法），接受者为值类型时，可以直接用指针类型的变量调用方法，反之亦然。

总结：

1. 不管调用形式如何，真正决定是值拷贝还是地址拷贝，看这个方法是和那个类型绑定。
2. 如果是值类型，比如（p Person），则是值拷贝；如果是指针类型，比如是（p *Person）则是地址拷贝。

## 工厂模式

没有构造函数，使用场景：当结构体开头为小写，在别的地方要调用。

model student.go

```go
type student struct {
    Name string
    Score float64
}

//因为student结构体首字母小写，因此是只能在model十三
//我们通过工厂模式来解决
func NewStudent(n string, s float64) *student{
    return &student{
        Name:n,
        Score:s,
    }
}
```

main.go

```go
func main(){
        var stu = model.NewStudent("tom~", 88.8)
    
    fmt.Println(*stu) //&{...}
    fmt.Println("name=",stu.Name,"score=", stu.Score)
}
```

如果字段Score小写，score，私有方法公有属性。

 ```go
 func (s *student) GetScore() float64{
     reture s.score
 }
 ```

## 封装

封装把抽象出的字段和字段的操作封装在一起，数据被保护在内部；程序的其他包只有通过被授权的操作（方法），才能对字段进行操作。

### 理解和好处：

隐藏实现细节，可以对数据进行验证，保证安全合理。

### 如何体现封装

1. 对结构体中的属性进行封装
2. 通过方法，包 实现封装



## 继承

如果一个struct嵌套了另一个匿名结构体，那么这个结构体可以直接访问匿名结构体的字段和方法，从而实现了继承的特性。

```go
type Goods struct{
    Name string
    Price int
}
type Book struct{
	Goods //这里就是嵌套匿名结构体Goods
    Writer string
}
```



模糊（ambiguous）不能确定值

```go
type A struct{
    Name string
    age int
}
type B struct{
    Name string
    Score float64
}
type C struct{
    A
    B
    //Name string   c.Name 可以直接找到
}

func main(){
    var c C
    c.A.name = "ling"//如果不A会报错
}
```





没有重载

# 20.interface

把所有的具有共性的方法定义在一起，任何其他类型只要实现了这些方法就是实现了这个接口。

高内聚低耦合，体现**多态**。接口更加灵活。

多态参数，多态数组。

继承是满足is-a的关系，接口满足like-a的关系。

## 注意事项和细节：

1. 接口本身不能创建实例，但是可以指向一个实现了该接口的自定义类型的变量（实例）
2. 接口中所有的方法都没有方法体，即都是没有实现的方法。
3. 空接口interface{}没有任何方法，所有所有类型都实现了空接口，即我们可以把任何一个变量付给空接口。



# 类型断言

 类型断言，由于接口是一般类型，不知道具体类型，如果要转成具体类型，就需要使用类型断言。

![image-20210802200548433](https://gitee.com/ling66611/picgo-image/raw/master/master/image-20210802200548433.png)

```go
var x interface{}
var b float32 = 1.1
x=b //空接口可以接受任意类型
//x=》float32 [使用类型断言]
y := x.(float32)
fmt.Printf("y的类型是%T 值是 %v",y,y)
```

对上面代码的说明：在进行类型断言时，如果类型不匹配就会报panic，因此进行类型断言是，要确保原来的空接口指向的就是断言的类型。



## 类型断言（带判断的）

```go
	var x interface{}
	var b float32 = 1.1
	x = b //空接口可以接受任意类型
	//x=》float32 [使用类型断言]

	if y, ok := x.(float32); ok {
		fmt.Println("convert success")
		fmt.Printf("y的类型是%T 值是 %v", y, y)
	} else {
		fmt.Println("convert fail")
	}

```

items... interface{}  可变参数

func TypeJudge(items... interface{}){

}

# nil

可以理解为空指针错误信息，error类型，指向error的指针，但是实际没有指向。

强类型语言，golang中有多种引用类型：pointer、interface、slice、map，channel, function；



Failed to build the application: go: finding module for package github.com/astaxie/beego/server/web

这个是因为最新版的go启用了go.mod模式，也就是包管理工具，而管理包的目录未安装相应的模块

解决方案，关掉go.mod

```
go env -w GO111MODULE=off
```

Kind代表Type类型值表示的具体分类。零值表示非法分类。

# Golang的逗号OK模式

即："**, OK**"

使用场景：在一个表达式返回2个参数的时候使用，第一个参数是一个值或者`nil`，第二个参数是`true`/`false`或者一个错误`error`

# 深拷贝浅拷贝

深拷贝 内容一样，改变其中一个对象的值时，另一个不会变化。

浅拷贝 内容和内存地址一样，改变其中一个对象的值时，另一个同时变化。

```go
package deepCopy

import (
	"fmt"
)

// 定义一个Robot结构体
type Robot struct {
	Name  string
	Color string
	Model string
}

func main() {
	fmt.Println("深拷贝 内容一样，改变其中一个对象的值时，另一个不会变化。")
	robot1 := Robot{
		Name:  "小白-X型-V1.0",
		Color: "白色",
		Model: "小型",
	}
	robot2 := robot1
	fmt.Printf("Robot 1：%s\t内存地址：%p \n", robot1, &robot1)
	fmt.Printf("Robot 2：%s\t内存地址：%p \n", robot2, &robot2)

	fmt.Println("修改Robot1的Name属性值")
	robot1.Name = "小白-X型-V1.1"

	fmt.Printf("Robot 1：%s\t内存地址：%p \n", robot1, &robot1)
	fmt.Printf("Robot 2：%s\t内存地址：%p \n", robot2, &robot2)

}

```

深拷贝：robot2 := robot1	

浅拷贝：robot2 := &robot1

fmt.Println("浅拷贝 使用new方式")  

 robot1 := new(Robot)

```go
package main

import (
	"fmt"
)

// 定义一个Robot结构体
type Robot struct {
	Name  string
	Color string
	Model string
}

func main() {

	fmt.Println("浅拷贝 内容和内存地址一样，改变其中一个对象的值时，另一个同时变化。")
	robot1 := Robot{
		Name:  "小白-X型-V1.0",
		Color: "白色",
		Model: "小型",
	}
	robot2 := &robot1
	fmt.Printf("Robot 1：%s\t内存地址：%p \n", robot1, &robot1)
	fmt.Printf("Robot 2：%s\t内存地址：%p \n", robot2, robot2)

	fmt.Println("在这里面修改Robot1的Name和Color属性")
	robot1.Name = "小黑-X型-V1.1"
	robot1.Color = "黑色"

	fmt.Printf("Robot 1：%s\t内存地址：%p \n", robot1, &robot1)
	fmt.Printf("Robot 2：%s\t内存地址：%p \n", robot2, robot2)

}

```

# 21.日期

```go
//godate工具类，go get github.com/kofoworola/godate
//https://github.com/kofoworola/godate
t := time.Now()
date, _ := godate.Parse("2006-01-02", "2019-05-01")
date.Year(int(t.Year())).Month(int(t.Month())).Day(int(t.Day())).
	Hour(int(t.Hour())).Minute(int(t.Minute())).Second(int(t.Second()))
fmt.Println(date.Format("20060102150405")) //2008-10-30 11:03:12

t2 := time.Now()
t2.Format("20060102150405")
fmt.Printf("当前年月日---- %d%d%d%d%d%d \n", t2.Year(),
	t2.Month(), t2.Day(), t2.Hour(), t2.Minute(), t2.Second())
fmt.Println("1111111111111111111")
fmt.Println(t2.Format("20060102150405"))

fmt.Println("t3--------------")
t3 := time.Now()
fmt.Println(t3.Format("20060102150405"))
```





# 22.json

```go
func (c *TimeController) Get() {
	t := time.Now()
	fmt.Println(t.Format("20060102150405"))
	//从配置文件中读取VIIDServerID
	VIIDServerID := beego.AppConfig.String("VIIDServerID")

	time := SystemTimeObject{
		VIIDServerID: VIIDServerID,
		TimeMode:     "22222",
		LocalTime:    t.Format("20060102150405"),
		TimeZone:     "TimeZone时区",
	}
	mapData := make(map[string]interface{})
	mapData["SystemTimeObject"] = time
	c.Data["json"] = mapData
	c.ServeJSON()

	// c.Ctx.WriteString("api接口---------" + t.Format("20060102150405"))

}
```

golang解析json数据，去传入参数	https://studygolang.com/articles/15882


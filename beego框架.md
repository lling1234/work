

# beego安装

beego 安装及部署    http://www.dingyucong.cn/article/4

```bash
$ cd ~
$ vim ./bashrc

export GOROOT="/usr/local/go" # 引号内设置为你自己的go安装目录
export GOBIN=$GOPATH/bin
export GOPATH="/home/ling/goproject" #// 引号内设置为自己的go项目的工作区间
export PATH=$PATH:$GOPATH/bin    #// 原路径后用冒号连接新路径

$ source .bashrc
```



conf文件夹:放的是项目有关的配置文件
Controllers:存放主要的**业务代码**
main.go:项目的入口文件****
**Models:存放的是**数据库有关内容
routers:存放路由文件，路由作用是**根据不同的请求指定不同的控制器**
static：存放静态资源，包括图片，html页面，css样式，js文件等
tests:测试文件
Views：存放视图有关内容

创建项目bee new 项目名

初始化项目模块：go mod init 项目名

运行项目 ：bee run



# 控制器

## get

```go
c.Data["name"] = "ling"	//绑定数据
c.Data["age"] = 11
c.TplName = "goods.tpl"	//跳转到指定界面，也可以是html，右下角改格式
```

直接给页面返回数据	c.Ctx.WriteString("执行增加操作")	

访问控制器里默认的Get方法：beego.Router("/article", &controllers.ArticleController{})   

访问自定义方法：beego.Router("/article/add", &controllers.ArticleController{}, "get:AddArticle")

Get传值获取值：

```go
id := c.GetString("id")

id, err := c.GetInt("id")
	if err == nil {
		beego.Info(err)
	}
```

## post

定义一个结构体

```go
type User struct {
	Username string   `form:"username" json:"username"`
	Pwd      string   `form:"pwd" json:"password"`
	Hobby    []string `form:"hobby" json:"hobby"`
}
func (c *UserController) DoEditUser() {
	u := User{}
//获取post传过来的值
	if err := c.ParseForm(&u); err != nil {
		c.Ctx.WriteString("post提交失败")
		return
	}
	fmt.Printf("%#v", u)
	c.Ctx.WriteString("解析post数据成功")
}
func (c *UserController) GetUser() {
	u := User{
		Username: "接啊外",
		Pwd:      "493fdsjh",
		Hobby:    []string{"1", "2"},
	}
	// 返回一个json数据
	c.Data["json"] = u
	c.ServeJSON()
}
```

## xml

在配置文件里面：	copyrequestbody = true

```go
func (c *GoodsController) Xml() {

	P := Product{}
	var err error
	str := string(c.Ctx.Input.RequestBody)
	beego.Info(str)
	c.Ctx.WriteString(str)

	if e := xml.Unmarshal(c.Ctx.Input.RequestBody, &P); e != nil {
		c.Data["json"] = err.Error()
		c.ServeJSON()
	} else {
		c.Data["json"] = P
		c.ServeJSON()
	}
}
```

## 动态路由/正则路由

beego.Router("/api/:id", &controllers.ApiController{})

伪静态正则路由

beego.Router("/cms_:id([0-9]+).html", &controllers.CmsController{})



## 重定向

	方式一
	// 执行跳转
	// c.Redirect("/", 302)
	// c.Ctx.Redirect(302, "success.html")
	
	方式二
	中间页面进行跳转
	<meta http-equiv="refresh" content="3; url=/">

# models

封装公共的功能，和数据库交互。

封装md5方法

models/tools.go

```go
package models

import (
	"crypto/md5"
	"fmt"
)

func Md5Str(str string) string {
	data := []byte(str)
	return fmt.Sprintf("%x\n", md5.Sum(data))
}

```

api.go

```go
package controllers

import (
	"crypto/md5"
	"encoding/hex"
	"fmt"

	"github.com/astaxie/beego"
)

type ApiController struct {
	beego.Controller
}

func (c *ApiController) Get() {
	//获取动态路由的值
	// id := c.Ctx.Input.Param(":id")
	// c.Ctx.WriteString("api接口---------" + id)

	// fmt.Println(models.Md5Str("123456"))
	id := c.Ctx.Input.Param(":id")
	data := []byte(id)
	m := md5.Sum(data)
	fmt.Printf("%X\n", md5.Sum(data))

	encodedStr := hex.EncodeToString(m[:])
	c.Ctx.WriteString("api接口---------" + encodedStr)

}
```

配置路由

beego.Router("/api/:id", &controllers.ApiController{})

```go
package routers

import (
	"beegodemo01/controllers"

	"github.com/astaxie/beego"
)

func init() {
	beego.Router("/", &controllers.MainController{})

	beego.Router("/article", &controllers.ArticleController{})
	beego.Router("/article/add", &controllers.ArticleController{}, "get:AddArticle")
	beego.Router("/article/edit", &controllers.ArticleController{}, "get:EditArticle")

	beego.Router("/user", &controllers.UserController{})
	beego.Router("/user/add", &controllers.UserController{}, "get:AddUser")
	beego.Router("/user/doAdd", &controllers.UserController{}, "post:DoAddUser")
	beego.Router("/user/edit", &controllers.UserController{}, "get:EditUser")
	beego.Router("/user/doEdit", &controllers.UserController{}, "post:DoEditUser")
	beego.Router("/user/getUser", &controllers.UserController{}, "get:GetUser")

	beego.Router("/goods", &controllers.GoodsController{})
	beego.Router("/goods/edit", &controllers.GoodsController{}, "put:DoEdit")
	beego.Router("/goods/delete", &controllers.GoodsController{}, "delete:DoDelete")
	beego.Router("/goods/add", &controllers.GoodsController{}, "delete:DoDelete")
	beego.Router("/goods/xml", &controllers.GoodsController{}, "post:Xml")

	// beego.Router("/api", &controllers.ApiController{})
	beego.Router("/api/:id", &controllers.ApiController{})
	beego.Router("/cms_:id([0-9]+).html", &controllers.CmsController{})

	beego.Router("/login", &controllers.LoginController{})
	beego.Router("/doLogin", &controllers.LoginController{}, "post:DoLogin")
}

```

# 线程安全

Golang1.9版本后，增加了并发安全的sync.Map。相比原生map加互斥锁的解决方案，性能稍微高一点。去读下代码，就知道这个东西虽然也用了锁，但还是做了一些优化。

至于原生map为什么不是并发安全，这个很好理解。并发安全是有代价的。如果原生map保证并发安全，那么一些不需要并发的场景，会有不小的性能损耗。

# cookie

![image-20210826151619508](https://gitee.com/ling66611/picgo-image/raw/master/master/image-20210826151619508.png)

## 加密cookie（建议用这个）

![image-20210826152014701](https://gitee.com/ling66611/picgo-image/raw/master/master/image-20210826152014701.png)

# session

分布式存到redis mysql里面，防止session过期

key加密 

## 设置session

bee.controller    c.SetSession("username","张三")

## 获取session

1.  c.GetSession("username")
2. c.Ctx.Input.Session("username")



# swagger

生成swagger文档

 ```go
 bee run -gendoc=true -downdoc=true
 ```

需要把生成的swagger目录所有文件，复制到挂载的目录里面


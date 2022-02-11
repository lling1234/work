# 备忘

528 tpc-b-nt   19a tpc-b

Z:\03-公共资料\02-docs  

VLC 网络串流  rtsp://192.168.1.120:554/live?channel=1&subtype=1

# onvif

https://www.onvif.org/ch/profiles/whitepapers/

H.265是和H.26x/MPEG-x AVC一样是一种编码压缩的技术，其具体高效率的编码方式，设备支持H.264和H.265。

MJPEG是**网络摄像机的压缩格式**。也是现在主流压缩格式。几乎所有的视频监控设备厂商都以这两种产品为主。想让图像像素更高，画质更清晰，那就必须依靠压缩技术来优化。

MPEG4编码标准,mp4和avi

SVAC《安全防范监控数字视音频编解码技术标准》是国家规范化的编码方式，安全防范监控行业独特要求的技术标准协议，也是一种编码技术。

GB/T28181是《安全防范视频监控联网系统信息传输、交换、控制技术要求》一部国家标准。

ONVIF和PSIA是国际的通用接口协议、标准

摄像头相当于一个服务器，监控平台相当于客户端

infray:艾睿摄像头  海康、大华

Profiles [A](https://www.onvif.org/ch/profiles/profile-a/)、[C](https://www.onvif.org/ch/profiles/profile-c/)、[D](https://www.onvif.org/ch/profile-d/)和[M](https://www.onvif.org/ch/profiles/profile-m/) 适用于门禁控制，Profiles [G](https://www.onvif.org/ch/profiles/profile-g/)、[Q](https://www.onvif.org/ch/profiles/profile-q/)、[M](https://www.onvif.org/ch/profiles/profile-m/)、[S](https://www.onvif.org/ch/profiles/profile-s/)与[T](https://www.onvif.org/ch/profiles/profile-t/) 适用于视频系统。

***\*视频流\****  RTSP/RTP协议

# Profile S

#### 用于基本视频流

- 视频流和配置

Profile S专为基于IP的视频系统而设计。 Profile S设备（例如，IP网络摄像机或视频编码器）是可以通过IP网络将视频数据发送到Profile S客户端的设备。 Profile S客户端（例如，视频管理软件）是可以从Profile S设备配置，请求和控制IP网络上的视频流的设备。 Profile S还涵盖了用于PTZ控制，音频输入，多播和继电器输出的ONVIF规范，适用于符合此类功能的设备和客户端。

*PTZ* 在安防监控是 Pan/Tilt/Zoom 简写，代表云台全方位（上下、左右）移动及镜头变倍、变焦控制。

RTMP(实时消息传输协议)，Adobe的私有协议，协议基于TCP，是一个协议族。是一种设计用来进行实时数据通信的网络协议，支持RTMP协议的流媒体、交互服务器之间进行音视频和数据通信。RTMP与HTTP一样，都属于TCP/IP四层魔性的应用层。

直播Nginx-rmtp-module：音视频（或桌面）采集---》OBS推流---》视频服务器（美颜、鉴黄等处理）---》拉流

元数据：描述数据属性的信息，人物特征性格，电影演员信息。

**RTSP实时流传输协议**

（1）是流媒体协议。

（2）RTSP协议是公有协议，并有专门机构做维护。.

（3）RTSP协议一般传输的是 **ts**、**mp4** 格式的流。

（4）RTSP传输一般需要 **2-3** 个通道，命令和数据通道分离。

RTSP，拉的模式

RTMP 可以用在双端，但 HLS 只能用在拉流端，记住这层关系。

![img](https://gitee.com/ling66611/picgo-image/raw/master/master/238151-6b9f5a7f9b6bd12d.png)

# 国标28181

\192.168.1.200\public\01-技术文档\04-协议文档\国标文档

国标28181，应用层协议，**解决平台与平台对接（通信）问题**，**推**的模式，可以实现视频流出外网。基于SIP协议，视频流出外网。

SIP：会话发起协议，基于文件的应用层控制协议，用于创建、修改和释放一个或多个参与者的会话。

RTP：网络传输协议，在互联网上传递音频和视频的标准数据包格式，多播协议用于单播；RTP协议和RTP控制协议RECP一起使用，船舰在UDP协议上。  

![img](https://gitee.com/ling66611/picgo-image/raw/master/master/20200616084823887.png)

SIP服务器和媒体服务器可以是同一个设备
媒体流接受者：摄像机推给媒体服务器，媒体服务器再推给媒体设备接受者，媒体服务器相当于分发,中转(也可以直接推给媒体流接受者)然后提供RTSP、RTMP、FLV、HLS多种格式进行分发，实现web浏览器、手机浏览器、微信、PC客户端等各终端无插件播放。

常见的GB28181报文，包括注册（REGISTER）、注销（REGISTER）、心跳（Keepalive）、INVITE、云台控制（PTZ）；并且针对海康、大华品牌的IPC分别在同网和跨网（跨路由器）的情况下进行分析。

get请求比较多。

# NVR

NVR，全称Network Video Recorder，即**网络视频录像机**，是[网络视频监控系统](https://baike.baidu.com/item/网络视频监控系统/7854452)的[存储转发](https://baike.baidu.com/item/存储转发/9763136)部分，NVR与[视频编码器](https://baike.baidu.com/item/视频编码器/10483427)或[网络摄像机](https://baike.baidu.com/item/网络摄像机/1154233)协同工作，完成视频的[录像](https://baike.baidu.com/item/录像/9940589)、存储及转发功能。

# VSR

​          XX-VSR-AS1608AP-V100 

192.168.1.145 智能分析平台，

AI预览，多通道预览，回放管理，智能检索

智能管理（智能预案配置、算法配置、授权）

相机管理，储存管理，流量统计

预警布防，预警查询

系统设置、日志、重启、对讲、关机

1.添加布控告警相关接口

# SVR

提升画质，可以让1080p的显示器呈现4K分辨率的画质。

# onvifserver

鉴权 Authentication 获取unvif鉴权、设置鉴权方式、crud用户

blp业务逻辑处理

http.HandleFunc 函数类型（用这个） 这个第二个参数是一个方法，参数是ResponseWriter, 和 *Request 所以使用的时候需要传方法。

http.Handle	第二个参数是Handler这个接口, 这个接口有一个ServeHTTP()的方法，所以这个方法使用的时候需要自己去定义struct实现这个**Handler**接口。

ListenAndServe使用指定的监听地址和处理器启动一个HTTP服务端。处理器参数通常是nil，这表示采用包变量

## SOAP（简答对象访问协议）

使用XML作为序列化编码格式的RPC调用

xml.Marshal  Marshal函数返回v的XML编码。

Unmarshal解析XML编码的数据并将结果存入v指向的值。v只能指向结构体、切片或者和字符串。良好格式化的数据如果不能存入v，会被丢弃。

message...  不定长切片

## log

​	log.Info("RequestName:", requestName)

​	log.Warn("Write response error:", err)

​	log.Errorf("Message marshal error:", err)

## uuid序列化？

## BuildDiscoverMessage  设备发现

NTP网络时间协议，同步时间

## SDP

**SDP**全称是Session Description Protocol，翻译过来就是描述会话的协议。主要用于两个会话实体之间的媒体协商。

什么叫会话呢，比如一次网络电话、一次电话会议、一次视频聊天，这些都可以称之为一次会话。

那为什么要去发这个描述文本呢，主要是为了解决参与会话的各成员之间能力不对等的问题，如果参加本次通话的成员都支持高质量的通话，但是我们没有去进行协议，为了兼容性，使用的都是普通质量的通话格式，这样就很浪费资源了。所以SDP的作用还是很有必要的。

# 19A

## 1.功能

登录

go.mod go.sum 依赖管理

golang的time.Format方法一定要用2006-01-02 15:04:05作参数

dev mgr文件：数据方法写到dev里面，mgr调用dev

​	dev         DevTemp                //测温分析设备

图片存在哪里，存在sdk卡里面

# thermaltemp

## arch

开尔文(K)=273.15+摄适度(T)

arch:硬件差异层，屏蔽硬件体系结构差异，实现业务组件跨平台运行

arch_amd64.go 空实现 	return true

## blp

### temp_data 获取温度数据

获取点线面框架温度，存到切片

两个全局变量 	result TempResult	mtx    sync.RWMutex

## router

restful API规范，get获取数据，post提交数据，put修改数据，delete删除数据

```golang
beego.GlobalControllerRouter["neuron/function/thermal/thermaltemp/http:Controller"] = 

append(beego.GlobalControllerRouter["neuron/function/thermal/thermaltemp/http:Controller"],

    beego.ControllerComments{

        Method: "GetTempDifference",//方法名

        Router: "/difference",

        AllowHTTPMethods: []string{"get"},

        MethodParams: param.Make(),

        Filters: nil,

        Params: nil})
```

cmd.go 启动和停止，获取配置，初始化数据，开始执行。

rune

- `rune`是`int32`的别名，在所有方面都等同于`int32`
- 按惯例，它用于区分**字符值**和**整数值**。

http://192.168.1.140/v1/thermal/temp/tempFrame/temp  GetTempFace 每秒获取人脸温度

# 感兴趣区域报警联动事件

设置-相机设置 视频   感兴趣区域   物体温度超过80摄氏度，声音报警

目前已实现的功能：使能、图像质量、可见光和测温两个通道、绘制区域（四个区域）、删除绘制区域。

![image-20210726101635088](https://gitee.com/ling66611/picgo-image/raw/master/master/image-20210726101635088.png)

1. 前端获取绘制区域xy轴坐标（对角线），传给后端，500毫秒获取一次温度；

   摄氏度 = （华氏度 - 32） * 5/9℃
   华氏度 = 摄氏度 * 9/5 + 32℉
   开尔文 = 摄氏度+273.15K

   tempRegion     [arch.MaxTempAreas]dsd.TempData //当前区域测温数据

   cfgRegion      conf.TempRegionConfigs          //当前区域测温配置

2. 温度异常报警：最高温（TempRangeMax float32     `description:"温宽:最高温,用于整帧测温"`）、最低温，调温度和区域接口

   ![image-20210726102856639](https://gitee.com/ling66611/picgo-image/raw/master/master/image-20210726102856639.png)

3. 温度超过80触发 channel 01拍照，拍照存在SD卡里面



代码

http.go

```go
// @Title 获取测温区域配置
// @Summary 获取测温区域配置
// @Description 获取测温区域配置
// @Param	 default  query	    bool   false	 "默认配置"
// @Success  200      {object}  []conf.TempRegionConfig
// @Failure  400300   获取配置失败
// @router   /tempRegion [get]
func (c *Controller) GetTempRegion() {
	var err error
	rsp := apis.Response{}
	c.Data["json"] = &rsp
	defer c.ServeJSON()

	dft, _ := c.GetBool("default", false)
	cfg := conf.TempRegionConfigs{}
	if dft {
		err = config.GetDefault(&cfg)
	} else {
		err = config.GetConfig(&cfg)
	}
	if err != nil {
		rsp.Error(errors.ErrGetCfgFailed, err.Error())
		return
	}
	cfg.ConvTemp2Std()
	rsp.Success(cfg)
}

// @Title 设置测温区域配置
// @Summary 设置测温区域配置
// @Description 设置测温区域配置
// @Param	 cfg    body	 []conf.TempRegionConfig  true	"测温区域配置"
// @Success  200
// @Failure  400000   操作失败
// @router   /tempRegion [put]
func (c *Controller) SetTempRegion() {
	rsp := apis.Response{}
	c.Data["json"] = &rsp
	defer c.ServeJSON()

	tmpcfg := conf.TempRegionConfigs{}
    //将数据解码 Marshal将数据编码成json字符串
	err := json.Unmarshal(c.Ctx.Input.RequestBody, &tmpcfg)
	if err != nil {
		rsp.Error(errors.ErrBadRequest, err.Error())
		return
	}

	tmpcfg.ConvTemp2K()
	//非使能项需要恢复到默认值,使能项判断是否是区域
	if !tmpcfg.Verify() {
		rsp.Error(errors.ErrBadRequest, "Param verification failed")
		return
	}

	err = config.SetConfig(tmpcfg)
	if err != nil {
		rsp.Error(errors.ErrOprFailed, err.Error())
		return
	}

	rsp.Success()
}

// @Title 获取测温区域温度值
// @Summary 获取测温区域温度值
// @Description 获取测温区域温度值，当id>0时获取指定规则ID的温度值
// @Param	 id       query     uint32     false	"区域测温序号ID"
// @Success  200      {object}  []dsd.TempData
// @Failure  400300   获取配置失败
// @router   /tempRegion/temp [get]
func (c *Controller) GetTempRegionTemp() {
	rsp := apis.Response{}
	c.Data["json"] = &rsp
	defer c.ServeJSON()

	data := blp.GetIns().GetRegionTempData()
	id, _ := c.GetUint32("id", 0)
	if id > 0 {
		tmpdata := data[id-1]
		tmpdata.ConvTemp2Std()
		rsp.Success(tmpdata)

	} else {
		data.ConvTemp2Std()
		rsp.Success(data)
	}
}
```



# I帧，P帧，B帧

I帧是关键帧，属于帧内压缩，和AVI的压缩是一样的。P是向前搜索，B是双向搜索，它们都是基于I帧来压缩数据。

I帧表示关键帧，你可以理解为这一帧画面的完整保留；解码时只需要本帧数据就可以完成（因为包含完整画面）



P帧表示的是这一帧跟之前的一个关键帧（或P帧）的差别，解码时需要用之前缓存的画面叠加上本帧定义的差别，生成最终画面。（也就是差别帧，P帧没有完整画面数据，只有与前一帧的画面差别的数据）


B帧是双向差别帧，也就是B帧记录的是本帧与前后帧的差别（具体比较复杂，有4种情况），换言之，要解码B帧，不仅要取得之前的缓存画面，还要解码之后的画面，通过前后画面的与本帧数据的叠加取得最终的画面。B帧压缩率高，但是解码时CPU会比较累~。


从上面的解释看，我们知道I和P的解码算法比较简单，资源占用也比较少，I只要自己完成就行了，P呢，也只需要解码器把前一个画面缓存一下，遇到P时就使用之前缓存的画面就好了，如果视频流只有I和P，解码器可以不管后面的数据，边读边解码，线性前进，大家很舒服。
但网络上的电影很多都采用了B帧，因为B帧记录的是前后帧的差别，比P帧能节约更多的空间，但这样一来，文件小了，解码器就麻烦了，因为在解码时，不仅要用之前缓存的画面，还要知道下一个I或者P的画面（也就是说要预读预解码），而且，B帧不能简单地丢掉，因为B帧其实也包含了画面信息，如果简单丢掉，并用之前的画面简单重复，就会造成画面卡（其实就是丢帧了），并且由于网络上的电影为了节约空间，往往使用相当多的B帧，B帧用的多，对不支持B帧的播放器就造成更大的困扰，画面也就越卡。

一般平均来说，I的压缩率是7（跟JPG差不多），P是20，B可以达到50，可见使用B帧能节省大量空间，节省出来的空间可以用来保存多一些I帧，这样在相同码率下，可以提供更好的画质。
————————————————
版权声明：本文为CSDN博主「Rachel-Zhang」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/abcjennifer/article/details/6577934

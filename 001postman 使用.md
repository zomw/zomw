## 一、介绍
#### 1、什么是接口
API( application program interface)允许不同软件之间进行通信的规范
鉴权码（token 、key、appkey）
接口包括：内部接口、外部接口
- 内部接口： 开发人员自己开发的对自身系统提供的接口。组件之间的接口 
- 外部接口：开发系统调用外部的（微信支付宝等）
总结:接口是软件提供给外部的一种服务。用于做数据传输。
####  2、软件为什么需要接口
因为接口能让内部的数据被外部进行修改。
#### 3、为什么要做接口测试
- 很多系统前后端分离，开发进度不一样，需要把一开始开发出来的接口进行测试。mock（模拟接口）
- 基于安全考虑，前端有验证很容易绕过，直接请求接口。（例如，身份证信息，银行密码）
- 测试推崇测试左移，测试尽早的介入。
- 微信提现手续费示意图![](file:///C:/Users/201810/Downloads/screenshot20230725.png?lastModify=1690341970)
    

> **接口测试本质，就是测试接口是否能正常交互数据,权限控制以及异常场景。**

###  二、接口返回数据和Json详解

> json是一种数据类型

- json 由两种数据组成
    - Map对象，键值对，{key,value,key}
    - 数组[]
    [www.bejson.com](www.bejson.com) 校验json格式，接口加密（常用MD5）
- json格式 三组数据
    - {error_code：0，msg:"提现成功"，data:[]}
    error_code:0 错误码，0代表成功，code
    msg 错误码的中文说明
    data 真正的返回数据
- html格式
```
<html>  
    <title></title>  
    <body>  
        <error_code>0</error_code>  
        <msg></msg>  
        <data></data>  
    </body>  
</html>    
```
- xml格式
```<?xml? version="1.0" encoding="utf-8">  
        <error_code>0</error_code>  
        ......  
</xml>
```

### 接口测试协议

1、webservice协议：接口地址：http://..................................?wsdl

soap协议，wsdl

restful规则，get获取数据，post提交数据，put修改数据，delete删除数据

2、dubbo协议 接口地址以dubbo://开头

适用于少量数据传输，大并发。

不适合传输大量数据

3、http协议：接口地址http：//

https=http + ssl安全传输协议 端口:443

http端口80

> ==http协议超文本传输协议，主要用于服务器与浏览器交互数据。交互分为请求与响应。==

请求：get post put delete

响应：1xx信息，2xx成功、3xx重定向（跳转不传值），4xx客户端错误，5xx服务端错误


![image-20230725230317728](file:///C:/Users/201810/AppData/Roaming/Typora/typora-user-images/image-20230725230317728.png?lastModify=1690341970)
空一行
请求正文

响应部分：
响应行：协议，响应码，响应信息
http/1.1 200 OK
![[Pasted image 20230726175753.png]]
响应的内容

### 四、企业接口测试流程与方案
1、拿到接口api文档 ，熟悉接口业务、接口地址、鉴权、入参、出参、错误码。
2、接口的计划和方案
思路：
正例输入正常入参，产看接口是否返回成功
反例：鉴权反例：鉴权为空，鉴权码错误，鉴权码过期
		参数反例：参数空、参数类型异常、参数长度异常、错误码覆盖
其他场景：分页异常
3、编写用例和评审
4、执行接口测试
5、输出接口测试报告

### 五、接口测试工具以及postman介绍
接口测试工具：postman jmeter soupui apipost fiddler charles

postman 网页调试与发送 HTTP请求的Chrome 插件，专用于接口




## 一、 接口测试

> 接口测试测试系统组件接口之间的一种测试

分类:

- 测试外部接口:测试被测系统和外部系统之间的接口。（只需要测试正例）
    
- 测试内部接口：
    
    - 1、内部接口只提供给内部系统使用（预算系统，承保系统）测试正例
        
    - 2、内部接口提供给外部系统使用。（测试必须全面，正例，各种异常场景，权限控制）
        

## 二、接口测试的流程以及用例测试

1、拿到接口api文档（抓包工具获取），熟悉接口业务，接口地址，鉴权方式，入参，出参，错误码。

2、编写接口用例以及评审。

> 思路：正例：正常入参，接口能够成功返回数据。

- 反例：
    
    - 鉴权反例：鉴权码，鉴权码错误，鉴权码过期，其他鉴权码失效。
        
    - 参数反例：参数为空，参数类型异常，参数长度异常
        
    - 错误码覆盖：根据业务而定
        
    - 其他错误场景：接口是否列入接口黑名单，接口调用次数有限制，分页场景。
        

示例![image-20230724215039962](file:///C:/Users/201810/AppData/Roaming/Typora/typora-user-images/image-20230724215039962.png?lastModify=1690341970)

3、使用接口postman执行接口测试

4、postman+Newman+jenkins实现持续继承，并输出测试报告并发送邮件

## 三、接口介绍

获取权限：

appid(ID): secret(秘钥)：

## 四、安装

postman.com/download

workspace

collection 集合

apis api文档

enviromments 环境变量

mock server 虚拟服务

monitors 监听器

historty

![image-20230725192944933](file:///C:/Users/201810/AppData/Roaming/Typora/typora-user-images/image-20230725192944933.png?lastModify=1690341970)

> params get请求传参
> 
> Authorization 鉴权
> 
> Headers 请求头
> 
> Body post请求传参
> 
> none 没有参数
> 
> form-data既可以传键值对参数，也可以传文件。
> 
> x-www-from-urlencoded 只可以传键值对
> 
> raw json,text,xml,html,javascript
> 
> binary 把文件以二进制方式传参
> 
> ![image-20230725194200961](file:///C:/Users/201810/AppData/Roaming/Typora/typora-user-images/image-20230725194200961.png?lastModify=1690341970)
> 
> Pre-request Script 请求之前的脚本
> 
> tests :请求之后的断言。

#cookie [[cookie]]用于管理cookie信息。

测试思路-测试大纲-测试用例

构建请求
1、请求方式
2、url地址 (只支持ASCII码，其他需要转码，右键)
3、header Content-type
4、body
右键，转为ASCII码
![[Pasted image 20230803220543.png]]


![[Pasted image 20230803221817.png]]
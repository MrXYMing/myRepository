
#### 利用js，实现禁用浏览器后退
包括键盘、鼠标手势等产生的后退动作

```
 history.pushState(null, null, document.URL);
 window.addEventListener('popstate', function () {
     history.pushState(null, null, document.URL);
});
```

#### 一些date相关的方法
```
/**解决某些浏览器new Date()不能直接设置参数的兼容性问题 */
$S.NewDate = function (str) {
    str = str.split('-');
    var date = new Date();
    date.setUTCFullYear(str[0], str[1] - 1, str[2]);
    date.setUTCHours(0, 0, 0, 0);
    return date;
}
[链接](http://blog.csdn.net/u010321537/article/details/52274831)

//翻译unix时间戳
$S.UnixToDate = function (unixTime, isFull) {
    var time = new Date(Number(unixTime));
    var ymdhis = {};
    var _date = "";
    _date += time.getFullYear() + "-";
    _date += (time.getMonth() + 1) + "-";
    _date += time.getDate();
    ymdhis.date = _date;
    if (isFull === true) {
        var _time = ""
        _time += " " + $S.checkTime(time.getHours()) + ":";
        _time += $S.checkTime(time.getMinutes()) + ":";
        _time += $S.checkTime(time.getSeconds());
        ymdhis.time = _time;
    }
    return ymdhis;
}
```

[其他方法](http://www.jb51.net/article/80599.htm)

---

#### angular2+node 跨域问题  <font color=gray > --2017.12.26</font>
补充：[JSON的原理与实现](https://www.jianshu.com/p/81efb4d188d7)
- angular2反向代理
    
    1. 项目根目录下创建一个`proxy.config.json`文件;
        ```
            {
                "**": {
                    "target": "http://localhost:3000", // 指向需要代理的api地址
                    "secure":false
                }
            }

            或者：
            "/api":{
                "target":"http://localhost:3000",
                "secure":false
            }
        ```
        http://localhost:3000 是连接机器的ip地址，或者需要请求的接口域名，这个就是需要被代理的。
        /api 是代理的名称，一般都是接口请求的ip地址后面的第一个参数名。
        比如：http://localhost:3000/api/front/frontUserController，反响代理后写接口请求时，只需要这样写：
        ```
        let url = "/api/front/frontUserController";
        this.http.post(url,{name:'xxx'}, this.options).subscribe((res: Response) => {
            //http成功
            console.log(res);
        },
        (err: any) => {
            //http失败
            console.log("网络连接错误,连接服务器失败:"+ err.message);
        },
        () => {
            //complete
        })
        ```
        
    2. 修改`package.json`文件
        ```
            "start": "ng serve --proxy-config proxy.config.json"
        ```
        **注意：**启动服务的时候，必须用`npm run start`启动，代理才生效，如果用ng serve启动代理不生效。

- Node中跨域配置

```
    var express = require("express");
    var app = express();
    //设置跨域访问
    app.all('*', function (req, res, next) {
        res.header("Access-Control-Allow-Origin", "*");
        res.header("Access-Control-Allow-Headers", "Content-Type, Content-Length, Authorization, Accept, X-Requested-With , yourHeaderFeild");
        res.header("Access-Control-Allow-Methods", "PUT,POST,GET,DELETE,OPTIONS");
        res.header("Content-Type", "application/json;charset=utf-8");
        next();
    });
    app.all('/get/*', function (req, res, next) {
        res.header('Access-Control-Allow-Methods', 'GET,OPTIONS');
        if (req.method == 'OPTIONS') {
            res.send(200);
            console.log(req.method);
        }
    });
    app.all('/post/*', function (req, res, next) {
        res.header('Access-Control-Allow-Methods', 'POST,OPTIONS');
        if (req.method == 'OPTIONS') {
            res.send(200);
            console.log(req.method);
        }
    });
```

#### 减少if的深层嵌套

[链接](http://blog.csdn.net/qq_34986769/article/details/62041345)
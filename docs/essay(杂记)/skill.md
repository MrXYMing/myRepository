
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
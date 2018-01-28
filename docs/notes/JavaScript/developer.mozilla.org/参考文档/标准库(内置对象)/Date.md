**Date对象基于`1970年1月1日`（世界标准时间）起的毫秒数**
[链接](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date)

#### 构造函数
```
    new Date();
    new Date(value);
    new Date(dateString);
    new Date(year, month[, day[, hour[, minutes[, seconds[, milliseconds]]]]]);
```

**注意：**只能通过调用Date构造函数来实例化日期对象：以常规函数调用它（即不加 new 操作符）将会返回一个字符串，而不是一个日期对象。
```
>> new Date()
<- Date 2018-01-20T13:10:29.576Z
>> Date()
<- "Sat Jan 20 2018 21:10:34 GMT+0800"
```

##### 参数说明

**注意1：**当Date作为构造函数调用并传入多个参数时，如果数值大于合理范围时（如月份为13或者分钟数为70），相邻的数值会被调整。比如new Date(2013,13,1)等于 new Date(2014,1,1)，他们都表示日期2014-02-01（`月份从0开始`）。

**注意2：**当Date作为构造函数调用并传入多个参数时，所定义参数代表的是当地时间。如果需要世界协调时，使用`new Date({{jsxred("Date.UTC","Date.UTC(...)")}})`和相同参数。

- value：代表自1970年1月1日00:00:00起经过的毫秒数；
- dateString：表示日期的字符串值。该字符串应该能被`Date.parse()`方法识别；
- year：代表年份的整数值，为避免2000年问题最好指定4位数的年份；使用1998，而不是用98；
- month：代表月份的整数值从`0(1月)`到`11(12月)`；
- day：代表一个月中的第几天的整数值，从1开始；

#### 方法：
- [Date.now()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/now)

    返回自1970-1-1 00:00:00 UTC至今所经过的毫秒数，类型为number。因为now()是Date的一个静态函数，必须以Date.now()形式来使用；
    
    IE9以下不支持，兼容方式：
    ```
    if(!Date.now){
        Date.now = function now(){
            return new Date().getTime();
        }
    }
    ```

- [Date.parse()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/parse)
    
    解析一个日期的字符串，并返回从1970-1-1 00:00:00所经过的毫秒数；如果该字符串无法识别，或者一些情况下，包含了不合法的日期数值（如：2015-02-31），则返回值为NaN。

    1. 符合RFC2822/IETF日期语法的字符串："`Mon, 25 Dec 1995 13:30:00 GMT`";
    2. 时区偏移："`Mon, 25 Dec 1995 13:30:00 +0430`";
    3. ES5 IOS-8601日期格式:"`2011-10-10`"(仅日期)或"`2011-10-10T14:48:00`"(日期和时间);

- [Date.UTC()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/UTC)

    接受的参数同日期构造函数接受最多参数时一样，返回从1970-1-1 00:00:00 UTC到指定日期的毫秒数；参数以`逗号 , `隔开。

    UTC方法与Date有两点不同：

    1. Date.UTC方法使用协调世界时代替本地时间；
    2. Date.UTC方法返回一个时间数值，而不是一个日期对象。

    如果有一个指定的参数超出其合理范围，则UTC方法会通过更新其他参数直到该参数在合理范围内，例如，月份指定15，则年份将加1，月份将会是3.

    Example:
    ```
        var utcDate = new Date(Date.UTC(96, 11, 1, 0, 0, 0));
    ```

---

#### Date实例

- [Date.prototype.getDate()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/getDate)

    根据本地时间，返回一个指定的日期对象为一个月中的第几天，返回时一个1到31的整数值。

    Example：
    ```
    var Xmas95 = new Date("December 25, 1995 23:15:00");
    var day = Xmas95.getDate();

    alert(day); // 25
    ```



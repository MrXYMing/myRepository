*这里将会记录一些碰到bug、兼容性问题、小技巧等内容*

#### css background-img :hover 状态下切换背景图片会闪烁一下的问题：
[链接](http://www.jb51.net/css/234744.html)

- 成因：第一次hover时，会去服务器请求图片，故此可能会造成闪烁；
- 解决：
    1. 预先加载；
    2. 将hover前后两张图片做成一张，靠`background-position`来控制图片位置 
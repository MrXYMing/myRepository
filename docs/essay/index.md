*这里将会记录一些碰到bug、兼容性问题、小技巧等内容*

#### css background-img :hover 状态下切换背景图片会闪烁一下的问题：
[链接](http://www.jb51.net/css/234744.html)

- 成因：第一次hover时，会去服务器请求图片，故此可能会造成闪烁；
- 解决：
    1. 预先加载；
    2. 将hover前后两张图片做成一张，靠`background-position`来控制图片位置 

---

#### Git用户名邮箱的全局配置和但仓库配置
[链接](http://blog.csdn.net/u011535508/article/details/53056976)

- 全局：
    - $git config --global user.name "xxxx"
    - $git config --global user.email "xxxx@xx.com"
    - $git config --list

- 单仓库：
    - $git config user.name "gitlab's Name"
    - $git config user.email "gitbal@xx.com"
    - $git config --list

*git config --list 查看当前配置，在当前项目下查看的配置是全局配置+当前项目的配置，使用的时候会优先使用当前项目的配置*
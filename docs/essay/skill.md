
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

---

#### 利用js，实现禁用浏览器后退
包括键盘、鼠标手势等产生的后退动作

```
 history.pushState(null, null, document.URL);
 window.addEventListener('popstate', function () {
     history.pushState(null, null, document.URL);
});
```

#### git分支
git branch  查看分支

git checkout dev 切换到dev分支






#### 小伙子，再接再厉

（Base杭州城西古墩路）高级前端开发工程师 
1、负责各产品线的前端开发以及系统架构设计及优化
2、分享工作心得、 带领团队共同成长
3、负责各产品线前端日常维护
4、高强度抗压能力

岗位技术要求：
1、掌握各种前端技术， 包括 HTML/CSS/JavaScript等；
2、具备跨终端的前端开发能力，在Web(PC+Mobile)/Node.js
二个方向上至少精通一个方向， 具备多个的更佳， 鼓励在 Native 和 Web技术融合上的探索；

2.1 Web(PC+Mobile)
·至少熟练运用一种前端开发框架如:Backbone.js/AngularJS/React.js等；
·能使用原生JavaScript进行无框架、类库依赖的开发；
2.2 Node.JS
·熟悉Express.js或Koa.js最佳；
·性能调优以及故障分析处理；

3、熟悉css预编译、后编译等工具，如 less / sass / postcss等；
4、对前端工程化与模块化开发有一定了解，并有实践经验如Broserify/Webpack/Gulp等；
5、具备良好的团队协作精神，能利用自身技术能力提升团队整体研发效率，提高团队影响力；
6、对前端技术有持续的热情，个性乐观开朗，逻辑性强，具有合作意识。

符合以下任一条件者优先：
* CoffeeScript或ECMAScript 2015(Babel.js)使用者；
* 参与开源项目并贡献过代码， 附上Github链接；
* 熟悉一门非前端的语言 如:Java/PHP/Python/Ruby等， 并有实践经验

核心点：
1、React项目经验，对源码有过研究；
2、从零开始架构产品经验；
3、至少三年以上工作经验, 都做过ReactNative项目的优先。

`react+webpack+es6`

##### 蚂蚁金服电面 
![蚂蚁金服电面](imgs/蚂蚁金服电面.png)

##### 阿里面试 
基础加原理。。。还有就是解决问题的思路

1. es6转换为es5的原理；
2. vue的双向绑定的原理；
3. webpack的原理；
4. css3的动画这种基础；
5. 卡在某个问题上以后，你的解决思路；
6. localstorae和cookis的区别和使用场景等；
7. dom的类型、dom操作效率这些；
8. http协议；
9. 如何释放闭包的内存；
10. 事件响应的步骤和如何优化

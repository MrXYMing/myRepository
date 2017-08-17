
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
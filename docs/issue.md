1. [] 发布过的版本不可编辑（管理--》查看，并跳转至另一个只读页面[通过action判断版本状态来控制跳转页面]；   删除--》下架；   编辑去掉）；提交后不许做任何更改；
2. [] 发布插件页：发布输入框，带单位； 是否必输项； 搜索关键字最小为3个字符，商城的搜索功能实现；
3. 发布插件页预览（优先级靠后）；
4. cdkey可重复激活bug？；
5. 新增插件版本时，用户需重新发布插件；管理员审核插件时，需提示管理员哪里做了更改；
6. 插件只有一个版本时，下架的话，给提示：“将会是插件下架”；
7. 版本下架后，资源下载列表中，需要标识下架的版本；
8. 插件下架后，页面可能会定制（优先级靠后）；



2. 发布插件页，PL000077会没有插件名称；
4. 用户输入cdkey后，激活时若已有该插件，需提示用户以拥有，但仍可继续激活；
6. 后台资源下载列表中，数据按版本号倒序显示；  增加列表收起/展示功能，尝试js的实现；


## 20170926
1. [] edge上传资源时，会有问题； ---- 已下载缺失的`circular-progress.min.map`文件，待服务器再次测试
2. [x] 资源下载列表中， 内核版本号改为 设计器版本号；
3. [x] UEditor图片有问题，需查找api；----经查实，图片是百度的链接，图片加载失败的原因不在我们；
4. 商城支付操作逻辑是否优化？
6. 邮箱中，cdkey最好给个序号标识；
7. [x] 报错的提示，过长字符需自动换行；
8. [] webconfig配置项，需重新配置；
9. [x] 查询出cdkey信息时，增加一条用户已有该插件的提示；
10. 分红比例 10/0；
11. [x] 更新上传资源时，添加上传按钮；
12. [] 修改上传资源时，需要做一次保存操作？【延后】 (检查代码确实是做了保存操作，)
13. [x] 补全下架成功提示；
14. [x] 打包的时候，选择插件时，下架过的插件，给提示，在select中的option中（已下架）；
15. [x] 下架插件时，提示是“已删除？？？”；
16. [] 找时间节点，将管理员的功能，进行整合；
17. 商城中点插件大分类，直接进入没有筛选的那一类，点左侧小分类，直接进入条件筛选后的分类；
18. 商城中已下架的插件，加入购物车变为已下架；或者图片上加幕布，标识已下架；
19. 商城中已下架的插件，是否排序靠后；
20. 商城中主页无用内容，去除；是否考虑主页放热门插件信息？【优先级靠后】目前要求看的过去就行；



## 20170928
1. edge上传图片有问题；
2. 默认模板 google高版本出不来；
3.  a.发布时，新增一个商品名；b.商城商品上显示商品名；c.版本下载之上增加一个“商品名称：xxx,打包请认准该商品名”
4. 账单中，若状态不成功，新增一个刷新按钮；

## 20171024
1. 模板说明；
2. [x] 商品价格说明；
3. [x] cdkey说明；
4. [x] 应用价格>用户价格 比较前没转类型

## 20171026
1. [x]上传过程中可以点击其他按钮，    -----------------禁用当前行的所有按钮
2. [x]图片重新上传后，应显示重新上传；
3. 保存成功后弹窗两次；     ------成因已找到，弹窗的toogle改为对应的open和close；
4. [x]新增版本后，一连点击多次，会出现多个相同主版本；
5. [x]下载模板，手机端点击生成模板，生成速度很慢，然后生成中，点击其他模块（假如说功能模块，再点击回来，又是生成模块了，能否切换到企业模块的时候，这里也继续生成）
6. [x]默认主版本为1.0.0，删除当前版本，再添加一个主版本，版本号默认为2.0.0，是否不太科学；----------修改为：请求后台，没有版本则直接添加并刷新；否则弹出版本类别选择框；
7. [x]添加修订版本，有时，界面卡住，会没有反应，点击多次情况下，可能会显示如下错误界面    ----------- 同4 已解决，待再次测试；
8. [x]在上传资源过程中，我将资源删除后，过几秒还会弹出这个提示     ---------------------同1
9. [x]插件发布那边，信息保存后，建议提示下“商城的相关信息会在发布并审核后更新”，不然有些用户发布插件后，从这里再次保存插件信息（没有再次发布），可能会疑惑为什么商城的信息没刷新


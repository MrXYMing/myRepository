# Angular2 知识点

## 1.Angular2应用程序的生命周期hooks（特殊事件）是什么？

适用于组件/指令的事件：

1. ngOnChanges：当Angular设置其接收当前和上一个对象值得数据绑定属性时响应；
2. ngOnInit：在第一个ngOnChange触发之后，初始化组件/指令；
3. ngDoCheck：检测并在Angular上下文发生变化时执行，每次更改检测运行时，会被调用；
4. ngOnDestory：在Angular销毁指令/组件之前清除，取消订阅可观察的对象并脱离事件处理程序，以避免内存泄漏。

组件特定hooks：

1. ngAfterContentInit：组件内容已初始化完成；
2. ngAfterContentChecked：在Angular检查投影到其视图中的绑定的外部内容之后；
3. ngAfterViewInit：Angular创建组件的视图后；
4. ngAfterChecked：在Angular检查组件视图的绑定之后。

## 2.使用Angular 2，和使用Angular 1相比，有什么优势？

1. Angular 2是一个平台，不仅是一种语言
2. 更好的速度和性能
3. 更简单的依赖注入
4. 模块化，跨平台
5. 具备ES6和Typescript的好处。
6. 灵活的路由，具备延迟加载功能
7. 更容易学习
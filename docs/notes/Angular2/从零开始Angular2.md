### 架构概览

用`Angular拓展语法`编写HTML模板，用`组件类`管理这些模板，用`服务`添加应用逻辑，用`模块`打包发布组件与服务。

#### Angular模块（无论根模块还是特性模块），都是一个带有@NgModule装饰器的类
NgModule是一个装饰器函数，接收一个用来描述模块属性的元数据对象。最重要的属性：
- declarations：声明本模块中拥有的视图类。`组件`,`指令`,`管道`；（声明一下这个模块内部成员）。
- exports：declarations的子集，可用于其他模块的组件模板。用来控制将哪些内部成员暴露给外部使用。导入一个module并不意味着将会导入这个module内部导入的module所暴露出的公共成员，除非导入的这个module把它内部导入的module写到exports中。
- imports：本模块声明的组件模板需要的类所在的其他模块。导入其他module，其他module暴露的Components、Directives、Pipes等可以在本module的组件中被使用。
- providers：服务的创建者，并加入到全局服务列表中，可用于应用任何部分。
- bootstrap：指定应用的主视图（称为根组件），它是所有其他视图的宿主。`只有根模块`才能设置bootstrap属性。


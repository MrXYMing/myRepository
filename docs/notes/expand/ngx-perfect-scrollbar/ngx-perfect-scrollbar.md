# 一、ngx-perfect-scrollbar（基于angular的滚动条） [原API](https://github.com/zefoy/ngx-perfect-scrollbar)

### 1.COMPONENT USAGE（使用组件的方式）

- 例子

```
<perfect-scrollbar class="container" [config]="config">
  <div class="content">Scrollable content</div>
</perfect-scrollbar>
```

- 属性

|Name               |    描述    |
|:---:|:----:|
|[config]           | 自定义配置文件重写全局默认值|
|[disabled]         | 初始化是否禁用 |
|[usePSClass]       | 使用ps提供的class（需要ps的主题style） |
|[autoPropagation]  | 自动刷新和滚动控制 |
|[scrollIndicators] | 启用渐消边缘滚动显示 |
|(< ps-event-name>) | 所有的事件绑定 |

### 2.DIRECTIVE USAGE（使用指令的方式）

- 例子

```
@import '~perfect-scrollbar/css/perfect-scrollbar.css';

<div [perfect-scrollbar]="config"></div>
```

- 属性

|Name               |    描述    |
|:---:|:----:|
|[perfect-scrollbar]| 可以用来提供可选的自定义配置|
|[disabled]         | 初始化是否禁用 |
|[usePSClass]       | 使用ps提供的class（需要ps的主题style） |
|[psPosStyle]       | 位置style(控制滚动条的位置) |
|(< ps-event-name>) | 所有的事件绑定 |

### 3.Available configuration options (custom / global configuration): (可用配置选项（自定义/全局配置）：)

|Name                    |    描述    |
|:---:|:----:|
|wheelSpee               | 鼠标滚轮事件滚动速度（默认值：1）|
|wheelPropagation        | 在滚动条滚动事件结束时（默认：false） |
|swipePropagation        | 在滚动条滑动事件结束时（默认：true） |
|minScrollbarLength      | 最小尺寸的滚动条（Default: null） |
|maxScrollbarLength      | 最大尺寸的滚动条（Default: null） |
|useBothWheelAxes        | 始终使用两个轮轴（默认：false） |
|suppressScrollX         | 禁用X轴在所有情况下（默认：false） |
|suppressScrollY         | 禁用Y轴在所有情况下（默认：false） |
|scrollXMarginOffset     | X轴上的偏移量（默认：0） |
|scrollYMarginOffset     | Y轴上的偏移量（默认：0） |
|stopPropagationOnClick  | 停止点击事件的传播（默认：true） |

### 4.Available control / helper functions (provided by the directive): (可用的控制/辅助函数（由指令提供）)

|Name                              |    描述    |
|:---:|:----:|
|ps()                              | 返回对ps实例的引用|
|update()                          | 更新滚动条的大小和位置|
|geometry(property)                | 返回指定属性的几何图形 |
|scrollable(direction)             | 检查给出的方向滚动,Direction can be: 'any','both','x','y' |
|scrollTo(x, y, speed)             | 滚动条移动到指定的横纵坐标(x,y) |
|scrollToY(position, speed)        | 滚动条移动到指定的纵坐标 |
|scrollToX(position, speed)        | 滚动条移动到指定的横坐标 |
|scrollToTop(offset, speed)        | 滚动条移动到最顶部 |
|scrollToLeft(offset, speed)       | 滚动条移动到最左边 |
|scrollToRight(offset, speed)      | 滚动条移动到最右边 |
|scrollToBottom(offset, speed)     | 滚动条移动到最底部 |

# 二、使用说明

参照demo源码中的使用方法即可。

[demo](https://zefoy.github.io/ngx-perfect-scrollbar/)

[源码](https://github.com/zefoy/ngx-perfect-scrollbar/tree/master/example/src/app)
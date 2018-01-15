[scss是sass3引入新的语法](http://sass.bootcss.com/docs/scss-for-sass-users/)

[官网入门](http://sass.bootcss.com/docs/guide/)
[中文网入门](https://www.sass.hk/guide/)

#### 1.变量(Variables)

使用`$`符号来定义变量，
```
    $highlight-color: #F90;
    .selected {
        border: 1px solid $highlight-color;
    }
```
*ps*:用中划线声明的变量可以使用下划线的方式引用。
```
    $link-color: blue;
    a {
        color: $link_color;
    }
```

#### 2.嵌套(Nesting)

- 嵌套选择器
```
    #sidebar{
        a {
            text-decotation:none;
        }
    }
```

- 嵌套属性
```
    #footer{
        border: {
            width:1px;
            color:#ccc;
            style:solid;
        }
    }
```

#### 3.局部模板(Patrials)

我们可以创建一个包含在其他sass文件中的含有小片段css的部分sass文件，这可以很好的模块化我们的css。只需要在文件名前带有`_`即可，例如`_partial.scss`，下划线会让sass知道该文件只是一个部分文件，它应该生成一个css文件。Sass partials 与`@import`指令一起使用。

#### 4.导入(Import)

当我们要导入`_reset.scss`到`base.scss`，我们只需要在`base.scss`文件中使用`@import 'reset';`即可。不需要包括文件拓展名`.scss`，sass自己会明白。

#### 5.混合(Mixins)

- 定义一个声明
```
    @mixin rounded($amount){
        -moz-border-radius:$amount;
        -webkit-border-radius:$amount;
        border-radius:$amount;
    }
```

- 使用这个声明
```
    .box{
        border:3px solid #777;
        @include rounded(0.5em);
    }
```

#### 6.扩展/继承(Extend/Inheritance)

使用`@extend`可以将一组css属性从一个选择器共享到另一个。
```
    .input-0{
        padding:0;
    }

    .input-group-0 {
        @extend .input-0;
    }
```
# 说明

此文档旨在提出一些javascript程序的注意事项。

## 语法规则

1. var

    - 始终使用 var 声明；
    - 没有指定var时，变量会被放置在全局上下文中;并且很难说出变量的生存范围。

2. 常量

    - 使用大写： NAMES_LIKE_THIS；
    - ie11以下不支持 const，所以不使用这个关键字；

3. 分号

    以下几种情况后需加分号：

    - 变量声明；
    - 表达式；
    - return；
    - throw；
    - break；
    - continue；
    - do-while

4. 块内函数声明

    - 不允许使用块内函数声明；
    - 可以使用用函数表达式初始化的变量来定义块内的函数；
    - 例如：
    ```js
        //Do not do this:

        if (x) {
            function foo() {}
        }

        //can do this

        if (x) {
            var foo = function() {};
        }
    ```

5. 异常处理

    - 使用 `try-catch(e)`；
    - 自定义异常，从返回值的函数返回错误信息可能会非常棘手。

6. 标准功能

    - 标准功能始终优先于非标准功能-为了获得最大的可移植性和兼容性；
    - 例如，string.charAt(3)就要优先于 string[3]。

7. 原始类型的包装对象

    - 不要对原始类型使用包装对象：
        ```js
        //Do not do this:

        var x = new Boolean(false);
        if (x) {
            alert('hi');  // Shows 'hi'.
        }
        ```
    - 但是可以使用类型转换：
        ```js
        var x = Boolean(0);
        if (x) {

            alert('hi');  // This will never be alerted.

        }

        typeof Boolean(0) == 'boolean';
        typeof new Boolean(0) == 'object';
        ```

8. 
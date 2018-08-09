# 兼容性

## 1.Array.prototype.includes()

[链接](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)
判断数组中是否包含一个指定的值，includes具有兼容性问题，IE并未实现，其他浏览器低版本也未实现。 

![兼容性](imgs/includes.png)

## 2.for...of

[链接](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of)

ie不支持数组的for...of

![兼容性](imgs/for_of.png)

## 3.border属性不指定全的情况

```css
    border-top: 0.45em inset;
```

- firefox || edge || ie11：`border-top-color: currentcolor;` 会默认为 currentcolor：当前颜色。css3拓展的颜色值关键字，具体是指`使用值是color属性值的计算值`，如果currentColor关键字被应用在color属性自身，则相当于color:inherut。
- chrome：`border-top-color: initial;` 会默认为 initial：`用于设置css属性为他的默认值`，可用于任何html元素上的任何css属性，除ie和opera15之前的版本，其他主流浏览器都支持,
    ```css
        border-top: 0.45em;
    ```
- firefox || edge || ie11：`border-top-style: none;` 会默认为 none,
- chrome：`border-top-color: initial;` 会默认为 initial,

- 拓展-border：
    1. border-width:
        1. thin:定义细的边框;
        2. medium:默认。定义中等的边框。
        3. thick:定义粗的边框;
        4. length:允许您自定义边框的宽度;
        5. inherit:规定应该从父元素继承边框宽度;
    2. border-style:
        1. none:定义无边框;
        2. hidden:与 "none" 相同。不过应用于表时除外，对于表，hidden 用于解决边框冲突;
        3. dotted:定义点状边框。在大多数浏览器中呈现为实线;
        4. dashed:定义虚线。在大多数浏览器中呈现为实线;
        5. solid:定义实线;
        6. double:定义双线。双线的宽度等于 border-width 的值;
        7. groove:定义 3D 凹槽边框。其效果取决于 border-color 的值;
        8. ridge:定义 3D 垄状边框。其效果取决于 border-color 的值;
        9. inset:定义 3D inset 边框。其效果取决于 border-color 的值;
        10. outset:定义 3D outset 边框。其效果取决于 border-color 的值;
        11. inherit:规定应该从父元素继承边框样式;
    3. border-color:
        1. color_name:规定颜色值为颜色名称的边框颜色（比如 red）;
        2. hex_number:规定颜色值为十六进制值的边框颜色（比如 #ff0000）;
        3. rgb_number:规定颜色值为 rgb 代码的边框颜色（比如 rgb(255,0,0)）;
        4. transparent:默认值。边框颜色为透明;
        5. inherit:规定应该从父元素继承边框颜色;

## 4.研究下不同浏览器的 line-height

## 5. remove节点

ie不支持remove()删除节点，但是有removeNode()，然而，ff不支持这个方法。

万幸，js有一个操作DOM节点的方法：`removeChild()`；我们通过要删除的子节点找到父节点，然后用父节点来removeChild。

```js
function removeElement(_element){
    var _parentElement = _element.parentNode;
    if(_parentElement){
         _parentElement.removeChild(_element);  
    }
}
```
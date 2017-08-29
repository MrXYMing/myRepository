# bootstrap-select（基于bootstrap的下拉选框） API翻译

|Name|Type|默认值|描述|
|:---:|:----:|:----:|:----|
|actionsBox|boolean|false|当设置为true时，在下拉菜单的顶部添加两个按钮（全部选择和取消选择所有）|
|container|string/false|false|当设置为一个字符串，将选择一个特定的元素或选择器，如,`container: 'body' | '.main-body'`|
|countSelectedText|string/function|function|设置文本显示的格式，当selectedtextformat是`count` or `count > #`。{0}是选定的数量。{1}可供选择。当设置为函数时，第一个参数是所选选项的数量，第二个参数是选项总数。函数必须返回一个字符串。|
|deselectAllText|string|'Deselect All'|当`actionsbox`启用时，清除所有的选择的按钮上的文字|
|dropdownAlignRight|boolean/'auto'|false|将菜单设置为true时，左对齐。如果设置为'auto'，菜单将自动对齐，如果菜单的全宽度不足时将向左对齐|
|dropupAuto|boolean|true|检查上下空间是否充足，如果向上弹出（dropup）有足够的空间就完全正常开启，但有更多的房间，dropup仍然正常打开的。否则，它就变成了一个dropup。如果dropupauto设置为false，dropups必须手动调用。|
|header|string|false|在菜单顶部添加一个页眉；默认情况下包括一个关闭按钮。|
|hideDisabled|boolean|false|删除从菜单中禁用的选项和optgroups :`data-hide-disabled: true`|
|iconBase|string|'glyphicon'|设置不同的基础图标字体代替glyphicons。如果改变iconbase，你也可能想改变tickicon，新图标字体使用不同的命名方案|
|liveSearch|boolean|false|当设置为true时，在下拉列表的顶部添加一个搜索框selectpicker|
|liveSearchNormalize|boolean|false|设置livesearchnormalize为true时，允许搜索不区分重音（accent-insensitive searching）|
|liveSearchPlaceholder|string|null|当设置为一个字符串时，一个占位符属性字符串将被添加到智能搜索输入框中|
|liveSearchStyle|string|'contains'|设置为`contains`时，搜索将显示包含搜索文本的选项。For example, searching for pl with return both Apple, Plum, and Plantain. When set to 'startsWith', searching for pl will return only Plum and Plantain.|
|maxOptions|integer/false|false|当设置为整数和多个选择时，所选选项的数量不能超过给定值.这个选项也可以作为数据属性为`<optgroup>`的存在，在这种情况下，它只适用于`<optgroup>`|
|maxOptionsText|string/array/function|function|文本显示出来时，maxoptions启用，对于给定的情况下选择的最大数目已选定。如果使用一个函数，它必须返回一个数组。数组[ 0 ]是文本时使用的maxoptions应用到整个选择元素。数组[ 1 ]是文本时使用的maxoptions用于OPTGROUP。如果使用一个字符串，用的都是相同的文本元素与OPTGROUP|
|mobile|boolean|false|设置为true时，启用设备的“本地菜单”以选择菜单。|
|multipleSeparator|string|', '|设置分隔选定选项的按钮中显示的字符|
|noneSelectedText|string|'Nothing selected'|当多个选择没有选定选项时显示的文本|
|selectAllText|string|'Select All'|actionsbox启用时，选择所有选项按钮上的文字|
|selectedTextFormat|'values'/'static'/'count'/'count > x' (where x is an integer)|'values'|指定如何用多个选择显示选择。`'values'`显示一个列表选项（分离multipleseparator。`'static'`只显示select元素的标题。`'count'`显示所选选项的总数。`'count > x'`的行为类似于`'values'`，直到选定选项的数目大于x；在此之后，它的行为类似于`'count'`。 |
|selectOnTab|boolean|false|当设置为true，在selectpicker dropdown中将制表符像回车或空格字符对待|
|showContent|boolean|true|设置为true时，在按钮中显示与选定选项关联的自定义HTML。当设置为false时，将显示选项值。 |
|showIcon|boolean|true|设置为true时，在按钮中显示与选定选项相关联的图标|
|showSubtext|boolean|false|当设置为true时，在选项旁显示此副标题|
|showTick|boolean|false|显示选定的选项标记（没有多属性的子项）|
|size|'auto'/integer/false|'auto'|显示选项的数目。When set to 'auto', the menu always opens up to show as many items as the window will allow without being cut off.When set to an integer, the menu will show the given number of items, even if the dropdown is cut off.When set to false, the menu will always show all items. |
|style|string/null|null|设置为字符串时，将值添加到按钮的样式中|
|tickIcon|string|'glyphicon-ok'|设置用于显示选定选项旁边的"tick"的图标|
|title|string/null|null|The default title for the selectpicker.|
|width|'auto'/'fit'/css-width/false (where css-width is a CSS width with units, e.g. 100px)|false|当设置为自动，这selectpicker宽度自动调整以适应最宽的选项。当设置为一个CSS宽度，宽度的selectpicker强行内联到给定值。设置为false时，将删除所有宽度信息。 |
|windowPadding|integer/array|0|当窗口有下拉菜单不能覆盖的区域时，这是非常有用的，例如一个固定的页眉。当设置为整数时，将向所有边添加相同的padding.或者，也可以使用整数数组:`[top, right, bottom, left]`|
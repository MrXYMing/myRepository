# webpack 性能优化

## [打包优化之速度](https://www.jianshu.com/p/3b9a19e5cead)

1. 减小文件搜索范围；
2. 配置`resolve.modules`;
3. 设置`test`&`include`&`exclude`；
4. 增强代码打包压缩工具：`webpack-parallel-uglify-plugin`&`optimize-css-assets-webpack-plugin`;
5. 用`Happypack`来加速代码构建；
6. 设置babel的`cacheDirectory`为true；
7. 设置`noParse`；
8. 拷贝静态文件；

## [打包优化之体积篇](https://jeffjade.com/2017/08/06/124-webpack-packge-optimization-for-volume/)

1. 避免类库引而不用，尽量使用模块化引入；
2. 按需异步加载模块；
3. 生产环境，压缩混淆并移除console；
4. 使用`Scope Hoisting`；
5. 引入`babel runtime`作为一个独立模块，避免重复引入。
# CommonJS

    CommonJS是nodejs也就是服务器端广泛使用的模块化机制。 
    该规范的主要内容是，模块必须通过module.exports 导出对外的变量或接口，
    通过 require() 来导入其他模块的输出到当前模块作用域中。
    
根据这个规范，每个文件就是一个模块，有自己的作用域，文件中的变量、函数、类等都是对其他文件不可见的。

如果想在多个文件分享变量，必须定义为global对象的属性。（不推荐）

- 定义模块
在每个模块内部，module变量代表当前模块。它的exports属性是对外的接口，将模块的接口暴露出去。
其他文件加载该模块，实际上就是读取module.exports变量。

- 入口文件
一般都会有一个主文件（入口文件），在index.html中加载这个入口文件，然后在这个入口文件中加载其他文件。
可以通过在package.json中配置main字段来指定入口文件。

- 模块缓存
第一次加载某个模块时，Node会缓存该模块。以后再加载该模块，就直接从缓存取出该模块的module.exports属性。

- 加载机制
CommonJS模块的加载机制是，输入的是被输出的值的拷贝。也就是说，一旦输出一个值，模块内部的变化就影响不到这个值。
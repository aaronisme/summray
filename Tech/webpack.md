# Webpack的总结
1. 4个核心的概念。
- The entry is the start point which the js file start to be processed.
entry can be mutiple, mutiple entry will have mutile output?

entry是webpack开始分析的起点，webpack从entry开始分析js文件，但他遇到import 或者是require的时候就把相应的依赖加载进来。同样entry可以是多个entry，一个entry里可以是多个文件，用数组的方式表示。

- and output is the output file which the final output is.

output是webpack的输出的地方，当分析加载完成后，webpack讲所有的js文件（或者是CSS，image等等）打包到一个bundle的JS里。输出出来，同样的output可以定义出多个输出的文件出来，一般来说，有几个entry就有几个output，具体的方式可以使用不同的plugin来定义。

- loaders are the loader to loader file. since the webpack only know js. so when they meet css, image, and other file you should use specific loader to loader that file.
因为webpack只能理解JS文件，所以对于其他类型的文件，或者ES6的JS，会定义不同的loader进行处理。

- plugins are the plugin tools to help you to do some work.
plugin的作用就是引用一些插件来完成一些任务，例如扰码，压缩JS，分离业务JS文件和依赖的库JS文件。

2. 对于老旧library的引用，对于一些没有npm包的库，在webpack 可以使用 shimming mannagment的方式进行使用。在我们项目上因为我不想在代码中显示的require他们，所以就使用了script-loader去处理。但是webpack应该是支持AMD的加载方式的，所以理论上是不需要什么特殊的处理的。至于具体的例子还要进一步的研究。
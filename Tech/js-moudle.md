# node.js 的 module
可以使用exports来对外提供要export的对象, 可以把要exports的对象挂到exports上。如果要export一个函数，可以考虑使用module.exports。如果exports的是arrow fucntion就得使用module.exports。所以这点要特别的注意。

当我们export一个函数作为constructer函数的时候就要使用module.exports。

同一文件只require一次。

```js
// bar.js
let privateValue = 3;

exports.getValue = () => privateValue;

exports.setValue = (value) => privateValue = value;

// foo.js
const bar = require('./bar.js');
console.log(bar.getValue());  // 3
bar.setValue(5);
console.log(bar.getValue()); // 5
const test = require('./bar.js');
console.log(test.getValue()); //5
```

require的顺序：
js 文件，相对路径就在相对路径中找
module，先找module中的package.json的 main下的路径，如果没有就找 index.js
不带相对路径的就在 node_modules里找，如果没找到就找上一层的直到找到顶层。

# ES6 import export
ES6 中定义了import 和 export的方法，但是可惜的是现在还没有js的runtime实现它，所以一般使用babel来进行编译。
import { x } from 'module'
如果是export 出来的 我们使用 { x } 这样的方式来import。

如果是export default 那么 我们 使用 import x from 'module';

可以export多个，其中一个是default。其他的是一般的export。

可以使用 import * as xx from 'module';
注意一点是 这里的 xx 是有包含所有的object，其中 default 是其中的一个key。
```js
   // bar.js
  export const big = 6;
  export const small = 4;
  export default x => x * 4;

  // foo.js
  import * as test from './bar';
  // test = { big: 6, samll:4 default: function}

```
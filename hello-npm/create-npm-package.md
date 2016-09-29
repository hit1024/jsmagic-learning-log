# create-npm-package 实现-greet-命令

## A 试验各种 `export`、`import`

### 1.1 ES6 语法导出
``` Javascript
export function greet(){}

// $node
// > require('./lib/index.js')
// { greet: [Function: greet] }
```

### 1.2 ES6 默认导出
``` Javascript
export default function(){}
// $node
// > require('./lib/index.js')
// { default: [Function] }
```

### 1.3 CommonJS 语法导出
``` Javascript
function greet(){}
module.exports = greet
// $node
// > require('./lib/index.js')
// [Function: greet]
```

### 2.1 导入 ES6 语法的导出

直接导入

``` Javascript
import greet from "./index.js"
console.log(greet);
// $node
// require('./lib/cli.js')
// undefined
// {}
```

使用命名导入

``` Javascript
import {greet} from "./index.js"
console.log(greet);
// $node
// require('./lib/cli.js')
// [Function: greet]
// {}
```

使用通配符导入

``` Javascript
import * as greet from "./index.js"
console.log(greet);
// $node
// require('./lib/cli.js')
// { greet: [Function: greet] }
// {}
```


### 2.2 导入 ES6 默认导出

直接导入

``` Javascript
import greet from "./index.js"
console.log(greet);
// $node
// require('./lib/cli.js')
// [Function]
// {}
```

使用命名导入

``` Javascript
import {greet} from "./index.js"
console.log(greet);
// $node
// require('./lib/cli.js')
// undefined
// {}
```

使用通配符导入

``` Javascript
import * as greet from "./index.js"
console.log(greet);
// $node
// require('./lib/cli.js')
// { default: [Function: greet] }
// {}
```

### 2.3 导入 CommonJS 语法导出（与 ES6 默认导出结果一致）


直接导入

``` Javascript
import greet from "./index.js"
console.log(greet);
// $node
// require('./lib/cli.js')
// [Function]
// {}
```

使用命名导入

``` Javascript
import {greet} from "./index.js"
console.log(greet);
// $node
// require('./lib/cli.js')
// undefined
// {}
```

使用通配符导入

``` Javascript
import * as greet from "./index.js"
console.log(greet);
// $node
// require('./lib/cli.js')
// { default: [Function: greet] }
// {}
```

---


## 结果对照

最终我的 cli.js 大概这样：

``` Javascript
import parseArgs from "minimist";

import greet from "../lib/index.js"
//console.log(greet);

export function main() {
  var args = parseArgs(process.argv);
  console.log(greet(args['_'][args['_'].length - 1], args['drunk']));
}
```

查看老司机的源码，发现老司机是这样做的：

``` Javascript
// index.js
export function greet(){}

// src.js
import { parseArgv } from "minimist";
const args = parseArgv(process.argv);

import { greet } from "./index";

const { drunk } = args;
const name = args._[2];
greet(name, drunk);
```

---

## 结论

多多尝试，总结规律中的原理。

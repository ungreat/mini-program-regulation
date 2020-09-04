# mini-program-regulation
支付宝小程序开发规范
## 开发规范


## 代码规范

### 框架

1. 不能连续`setData`，由于`setData()`是异步的，后面的`setData()`可能不能被成功地执行。
2. 用ajax请求，后端返回的值为`0`或者`false`,前端会接受成为`{}`




### Airbnb前端编码规范总结

1. #### 一直使用const来声明变量（如果不这样做就会产生全局变量）


2. #### 使用字面值创建对象
```
    
    // bad
    const item = new Object();
    // good
    const item = {};
 ```

3. #### 浅拷贝对象的时候最好是使用 `…` 操作符而不是 `Object.assign`
```
    // very bad
    const original = { a: 1, b: 2 };
    const copy = Object.assign(original, { c: 3 }); // this mutates `original`
    delete copy.a; // so does this
```
```
    // bad
    const original = { a: 1, b: 2 };
    const copy = Object.assign({}, original, { c: 3 }); // copy => { a: 1, b: 2, c: 3 }
```
```
    // good
    const original = { a: 1, b: 2 };
    const copy = { ...original, c: 3 }; // copy => { a: 1, b: 2, c: 3 }
    const { a, ...noA } = copy; // noA => { b: 2, c: 3 }
```
4. #### 如果一个函数适合用一行写出并且只有一个参数，那就把花括号、圆括号和 return 都省略掉。如果不是，那就不要省略

```
   // good  
  [1, 2, 3].map(x => x * x);
```
```
  // good  
  [1, 2, 3].reduce((total, n) => {  
    return total + n;
  }, 0);
```

5. #### 优先使用 === 和 !== 而不是 == 和 !=

6. #### 条件表达式例如 if 语句通过抽象方法 ToBoolean 强制计算它们的表达式并且总是遵守下面的规则：
```
     对象 被计算为 true
     Undefined 被计算为 false
     Null 被计算为 false
     布尔值 被计算为 布尔的值
     数字 如果是 +0、-0、或 NaN 被计算为 false, 否则为 true
     字符串 如果是空字符串 ” 被计算为 false，否则为 true
```

7. #### 不要使用通配符 import
```
为什么？这样能确保你只有一个默认 export。
   // bad
  import * as AirbnbStyleGuide from './AirbnbStyleGuide';

  // good
  import AirbnbStyleGuide from './AirbnbStyleGuide';
```

8. #### 不要从 import 中直接 export
```
为什么？虽然一行代码简洁明了，但让 import 和 export 各司其职让事情能保持一致。

  // bad
  // filename es6.js
  export { es6 as default } from './airbnbStyleGuide';

  // good
  // filename es6.js
  import { es6 } from './AirbnbStyleGuide';
  export default es6;
```


9. #### 如果模块有多行的属性， 关闭标签时新建一行.
```
    // bad
    <Foo
     bar="bar"
    baz="baz" />
    
    // good
    <Foo
    bar="bar"
    baz="baz"
    />
```
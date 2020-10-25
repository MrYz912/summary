# this



## 普通函数

- 直接调用的指向`window`， 如`foo()`
- 对象调用的指向该对象，如`obj.foo()`，`foo`函数中的`this`就是`obj`对象
- `new`：`this`永远指向该实例，不会被任何方式改变，如 `const c = new foo()`



## 匿名函数

- 非严格模式下，指向`window`
- 严格模式下，指向`undefined`



## 箭头函数

`this`指向包裹它的第一个普通函数的`this`，箭头函数的`this`无法用`bind`等改变



## 改变`this`指向

- `call`第一个参数为要改变的上下文对象，第二个参数开始以参数列表形式展现，如`Math.max.call(null,1,2,3)`

- `apply`第一个参数为要改变的上下文对象，剩下的放在数组里作为第二个对象，如`Math.max.apply(null,[1,2,3])`

- `bind`参数与`apply`一样，但返回的是一个函数，可以需要的时候再执行，`call`和`apply`都是立即执行

### 1.3.1 undefined与undeclared
- 下例说明了两种情况在字面量使用/typeof探测时候的表现
    - 声明未赋值
    - 未声明
- typeof有安全防护机制

```js
var a;
typeof a; // "undefined"
typeof b; // "undefined"
console.log(a); // undefined
console.log(b); // ReferenceError: b is not defined
```


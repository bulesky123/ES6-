# ES6-
学习ES6的总结
## 暂时是死区：
例子：
```
var a=123;
if(true){
  a = 'abc';//Uncaught ReferenceError: a is not defined
  let a;
  console.log(a);
}
```

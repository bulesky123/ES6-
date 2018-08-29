# ES6-
学习ES6的总结

```
一、暂时是死区：
例1：
var a=123;
if(true){
  a = 'abc';//Uncaught ReferenceError: a is not defined
  let a;
  console.log(a);
}

注：在代码块内，使用let命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区”（temporal dead zone，简称 TDZ）


例2：
typeof x;
let x ; //Uncaught ReferenceError: x is not defined

//暂时性死区的本质就是，只要一进入当前作用域，所要使用的变量就已经存在了，但是不可获取，只有等到声明变量的那一行代码出现，才可以获取和使用该变量。

二、块级作用域

function a(){
  let name = 'xiaomao';
  if(true){
    let name = 'xiaogou';
    console.log(name);//xiaogou
  }
  console.log(name);//xiaomao
}

{{{{
  {let insane = 'Hello World'}
  console.log(insane); // 报错  insane is not defined
}}}};




















```

# ES6
学习ES6的总结

```
一、暂时是死区：
case 1：
var a=123;
if(true){
  a = 'abc';//Uncaught ReferenceError: a is not defined
  let a;
  console.log(a);
}

注：在代码块内，使用let命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区”（temporal dead zone，简称 TDZ）


case 2：
typeof x;
let x ; //Uncaught ReferenceError: x is not defined

//暂时性死区的本质就是，只要一进入当前作用域，所要使用的变量就已经存在了，但是不可获取，只有等到声明变量的那一行代码出现，才可以获取和使用该变量。

二、块级作用域

case 1:
function a(){
  let name = 'xiaomao';
  if(true){
    let name = 'xiaogou';
    console.log(name);//xiaogou
  }
  console.log(name);//xiaomao
}

case 2:
{{{{
  {let insane = 'Hello World'}
  console.log(insane); // 报错  insane is not defined
}}}};

//const实际上保证的，并不是变量的值不得改动，而是变量指向的那个内存地址所保存的数据不得改动。对于简单类型的数据（数值、字符串、布尔值），值就保存在变量指向的那个内存地址，因此等同于常量。但对于复合类型的数据（主要是对象和数组），变量指向的内存地址，保存的只是一个指向实际数据的指针，const只能保证这个指针是固定的（即总是指向另一个固定的地址），至于它指向的数据结构是不是可变的，就完全不能控制了。因此，将一个对象声明为常量必须非常小心

case 3:
const foo = {};
// 为 foo 添加一个属性，可以成功
foo.prop = 123;
foo.prop // 123
// 将 foo 指向另一个对象，就会报错
foo = {}; // TypeError: "foo" is read-only

三、变量的解构赋值



















```

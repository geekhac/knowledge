# Javascript基础

## this关键字
函数的调用栈决定了this的指向，是运行时决定

### this的通用场景
1. 默认绑向
2. 隐含绑定
3. 明确绑定
4. new绑定
5. 特殊的箭头函数

#### 默认绑定
当函数没有在某个特定的容器中执行的时候，默认是指向全局的：
```javascript
function foo() {
	console.log( this.a );
}

var a = 2;

foo(); // 2
```
特别要注意的是：如果严格模式生效，全局对象是不合法的
```javascript
function foo() {
	"use strict";

	console.log( this.a );
}

var a = 2;

foo(); // TypeError: `this` is `undefined`
```

#### 隐含绑定
当函数是被确定的对象所调用的，则this 指向这个对象
```javascript
function foo() {
	console.log( this.a );
}

var obj = {
	a: 2,
	foo: foo
};

obj.foo(); // 2
```
##### 隐含丢失：
当函数被重新赋值之后，绑定的原对象this 会丢失,this 将会为默认绑定
```javascript
function foo() {
	console.log( this.a );
}

var obj = {
	a: 2,
	foo: foo
};

var bar = obj.foo; // 函数引用！

var a = "oops, global"; // `a` 也是一个全局对象的属性

bar(); // "oops, global"

```

```javascript
function foo() {
	console.log( this.a );
}

var obj = {
	a: 2,
	foo: foo
};

var a = "oops, global"; // `a` 也是一个全局对象的属性

setTimeout( obj.foo, 100 ); // "oops, global"
```

#### 明确绑定
使用 call 、apply 和 bind 可以明确指定this指向哪个对象
```javascript
function foo() {
	console.log( this.a );
}

var obj = {
	a: 2
};

var bar = function() {
	foo.call( obj );
};

bar(); // 2
setTimeout( bar, 100 ); // 2

// `bar` 将 `foo` 的 `this` 硬绑定到 `obj`
// 所以它不可以被覆盖
bar.call( window ); // 2
```

```javascript
function foo(something) {
	console.log( this.a, something );
	return this.a + something;
}

var obj = {
	a: 2
};

var bar = function() {
	return foo.apply( obj, arguments );
};

var b = bar( 3 ); // 2 3
console.log( b ); // 5
```

```javascript
function foo(something) {
	console.log( this.a, something );
	return this.a + something;
}

// 简单的 `bind` 帮助函数
function bind(fn, obj) {
	return function() {
		return fn.apply( obj, arguments );
	};
}

var obj = {
	a: 2
};

var bar = bind( foo, obj );

var b = bar( 3 ); // 2 3
console.log( b ); // 5
```

##### 特殊的硬绑定场景：api指定 this 环境
```javascript
function foo(el) {
	console.log( el, this.id );
}

var obj = {
	id: "awesome"
};

// 使用 `obj` 作为 `this` 来调用 `foo(..)`
[1, 2, 3].forEach( foo, obj ); // 1 awesome  2 awesome  3 awesome
```


#### new绑定
new 都干了什么
> 创建一个空对象  
> 空对象被引入原型链  
> 将空对象设置为函数的this  
> 如函数没有返回对象，则空对象将作为返回  

``` javascript
function foo(a) {
	this.a = a;
}

var bar = new foo( 2 );
console.log( bar.a ); // 2
```

### 几种this的执行顺序
new > 明确绑定 > 隐含绑定 > 默认绑定

### 特殊的绑定
箭头函数的绑定走的是词法作用域
``` javascript
function foo() {
  // 返回一个箭头函数
	return (a) => {
    // 这里的 `this` 是词法上从 `foo()` 采用的
		console.log( this.a );
	};
}

var obj1 = {
	a: 2
};

var obj2 = {
	a: 3
};

var bar = foo.call( obj1 );
bar.call( obj2 ); // 2, 不是3!
```


---

## 声明提升

## 继承

## 跨域

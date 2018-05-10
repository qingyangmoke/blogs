# Object.assign 的使用方法

> 通过调用该函数可以拷贝所有可被枚举的自有属性值到目标对象中。

## 第一个例子
 > 第一个参数对象会被重写 并且返回值为第一个参数对象
``` js
  const objA = {
     keyA: 'a'
  };

  const objB = {
    keyB: 'b'
  };

  const newObj = Object.assign(objA, objB);

  console.log(newObj); // {keyA: "a", keyB: "b"}

  console.log(objA); // {keyA: "a", keyB: "b"}

  console.log(objA === newObj); // true

```

## 第二个例子
 > 只拷贝可枚举自有属性

``` js
  const objA = {
    keyA: 'a'
  };

  const objB = {
    keyB: 'b'
  };

  Object.defineProperty(objB, 'age', {
    value: 32,
    enumerable: false // 设置成不可枚举
  });

  const newObj = Object.assign(objA, objB);

  console.log(newObj.age); // undefined

  console.log(objB.age); // 1

```

## 第三个例子
> 覆盖只读属性会抛异常

``` js
  const objA = {
    keyA: 'a'
  };

  Object.defineProperty(objA, 'age', {
    value: 32,
    writable: false // 设置成不可枚举
  });

  const objB = {
    keyB: 'b',
    age: 18
  }; 

  const newObj = Object.assign(objA, objB); // TypeError: Cannot assign to read only property 'age' of object

```


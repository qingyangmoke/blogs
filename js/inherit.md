# 继承

## 方式一

``` js
  function User(name) {
    this.name = name;
  }

  User.prototype.say = function (word) {
    console.log(word);
  };

  function VipUser(name) { 
    // 重点：这里 构造函数 继承自有属性
    User.call(this, name);
    this.balance = 100; 
  }

  // 重点：这里 继承原型属性
  VipUser.prototype = Object.create(User.prototype);
  // 重点：这里 constructor 指向自己
  VipUser.prototype.constructor = VipUser;

  VipUser.prototype.download = function() {
     console.log('vip download');
  }

```

## 方式二：es6

``` js
  class User {
    constructor (name) {
      this.name = name;
    } 
    say (word) {
      console.log(word);
    }
  }

  class  VipUser extends User { 
    constructor (name) {
      super(name);
      this.balance = 100; 
    } 
    download () {
     console.log('vip download');
    }
  } 
```
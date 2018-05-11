
#  慎用 for in 
 > 遍历对象可枚举的实例属性和继承属性
``` js

Array.prototype.say = function () {
  console.log('say');
}

const arr = [1, 2, 3, 4];

let count = 0;
for (const key in arr) {
  count += parseInt(arr[key], 10);
}

console.log(count);  // NaN

```
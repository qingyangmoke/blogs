##  hasOwnProperty 的使用
   > 不要使用obj.hasOwnProperty ,建议改用Object.prototype.hasOwnProperty.call 

   ``` js
    class User {
      constructor() {
          this.name = 'user name';
       }
        hasOwnProperty() {
          return 'what?';
        }
    }
    const user = new User();
    console.log(user.hasOwnProperty('name'),Object.prototype.hasOwnProperty.call(user,'name')); // output what? true
   ```
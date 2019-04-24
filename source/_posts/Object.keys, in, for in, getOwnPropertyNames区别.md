
| 操作                | 返回不可枚举属性 | 继承的属性 | 说明                                                                |
| ------------------- | ---------------- | ---------- | ------------------------------------------------------------------- |
| Object.keys()       | 否               | 否         | 返回自身可枚举属性列表，继承的和不可枚举的不会返回                  |
| in                  | 是               | 是         | 如果属性可访问就返回 true，不管是自身的还是继承的，也不管是否可枚举 |
| for in              | 否               | 是         | 遍历所有可枚举属性，不管是自身的还是继承的，但是不能遍历不可枚举的  |
| getOwnPropertyNames | 是               | 否         | 返回自身的属性列表，不管是否可继承，但是不能列出继承的属性          |

```javascript
function Animal() {}

Animal.prototype.name = "animal";

Animal.prototype.eat = function() {
  console.log("Animal eat");
};

Object.defineProperties(Animal.prototype, {
  type: {
    value: "animal",
    enumerable: true
  },
  fly: {
    value: false,
    enumerable: false
  }
});

function Cat(sex) {
  this.sex = sex;
}

Cat.prototype = Animal.prototype;

Cat.prototype.constructor = Animal;

const cat = new Cat(1);

Object.defineProperties(cat, {
  age: {
    value: 20,
    enumerable: false
  },
  address: {
    enumerable: true,
    value: "cd"
  }
});

// key权限最小，只会返回自身的且可以枚举的属性
console.log(Object.keys(cat)); // [ 'sex', 'address' ]

console.log("==================================");

// in权限最大，可能返回任何属性
console.log(`in sex: ${"sex" in cat}`); // true, 自身的,可枚举
console.log(`in age: ${"age" in cat}`); // true, 自身的,不可枚举
console.log(`in fly: ${"fly" in cat}`); // true, 继承的, 不可枚举
console.log(`in type: ${"type" in cat}`); // true, 继承的,可枚举

console.log("==================================");

// 返回可枚举的属性，不管是自身的还是继承的
// ['sex', 'address', 'name', 'eat', 'type']
for (const key in cat) {
  console.log(key);
}

console.log("==================================");

// 返回自身的属性,不返回继承的
console.log(Object.getOwnPropertyNames(cat)); // [ 'sex', 'age', 'address' ]
```
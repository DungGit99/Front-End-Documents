# Prototype

## Prototype là gì ?
- Prototype là cơ chế mà các object trong javascript kế thừa các tính năng từ một object khác.
- Trong JavaScript, trừ undefined, toàn bộ các kiểu còn lại đều là object. Các kiểu string, number, boolean lần lượt là object dạng String, Number, Boolean. Mảng là object dạng Array, hàm là object dạng Function. Prototype của mỗi object chính là cha của nó, cha của String là String.prototype, cha của Number là Number.prototype, của Array là Array.prototype.
- Array, Number hay String có cha là Object, do đó chúng đều có các hàm như `constructor, hasOwnProperty, toString` thuộc về của Object.prototype.

### Thêm thuộc tính và phương thức cho prototype
```js
const str = 'abc'
String.prototype.hello = 'Hello JavaScript'
String.prototype.print = value => value

console.log(str) // "abc"
console.log(str.hello) // "Hello JavaScript"
console.log(str.print(999)) // 999
```

### Các loại prototype
```js
// Prototype có sẵn
const person = {
  firstName: 'Dai',
  lastName: 'Nguyen',
  showName: function() {
    console.log(`${this.firstName} ${this.lastName}`)
  }
} // object này có prototype là Object.prototype

console.log(person.constructor.name) // "Object"

// Prototype tự định nghĩa
function Person(_firstName, _lastName) {
  this.firstName = _firstName
  this.lastName = _lastName
  this.showName = function() {
    console.log(`${this.firstName} ${this.lastName}`)
  }
}

const otherPerson = new Person('Dai', 'Nguyen')
// object này có prototype là Person.prototype
// Prototype mới: Person.prototype được tạo ra
// Person.prototype kế thừa Object.prototype
console.log(otherPerson.constructor.name) // "Person"
```

## Prototype dùng để làm gì ?
- Kể tử `es5` trở về trước, trong JavaScript không có khái niệm class, do vậy, để kế thừa các thuộc tính/ phương thức của một object, ta phải sử dụng prototype.
- Prototype có phần giống class, được sử dụng để hiện thực việc kế thừa (interitance) trong JavaScript.

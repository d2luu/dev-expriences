## ES6: important syntax

### const, let, var
```javascript
// Không thể thay đổi giá trị của biến được khai báo với const:
const x = 1;
x = 2 // error

// Tuy nhiên, vẫn có thể thay đổi giá trị của properties trong object được khai báo bằng const:
const obj = {a: 1, b: 2};
obj = {c: 1, d: 2}; // error
obj.a = 3; // no error
console.log(obj); // print: {a: 3, b: 2} in console.

// let và var đều tác động vào function block, tuy nhiên, trong trường hợp này, let chỉ tác động vào block ngay sau đó:

function someFunc() {
	for(let i = 0; i <= 9; i++) {
		// Biến i chỉ tồn tại ở đây
	}

	// Gọi biến i ở đây sẽ bị lỗi.
}

function someFunc() {
	for(var i = 0; i <= 9; i++) {
		// Biến i tồn tại ở đây
	}

	// Biến i vẫn còn tồn tại: i = 10
}
```

**Ưu tiên sử dụng let, const trong source code để code chặt chẽ và dễ dự đoán được luồng của chương trình, tránh các lỗi không mong muốn**

---

### Arrow function
*(param1, param2,..., paramN) => {statements};*

Arrow func cũng giống function bình thường, chỉ khác về syntax và binding context.
```javascript
function Animal() {
	this.age = 1;

	function showAge() {
		console.log(`Age is: ${this.age}`); // It will print: Age is: undefine
	}

	const showAgeArrow = () => {
		console.log(`Age in arrow func is: ${this.age}`); // It will print: Age in arrow func is: 1
	}
}
```

Trong react, nên sử dụng arrow function khi khai báo hàm trong class để không phải binding lại function đó trong constructor của class.

---

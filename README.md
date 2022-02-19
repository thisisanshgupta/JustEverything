# SwiftMokey
An interpreter for the Monkey programming language written in Swift.

What is monkey language ?
---------
Monkey is a programming language used in a book ["Writing An Interpreter In Go"](https://interpreterbook.com/) by Thorsten Ball.

Language Features
- C style syntax
- variable bindings
- integers and booleans
- arithmetic expression
- builtin function
- first class and high-order function
- closure
- string , array , hash data structure

Example
---------
variable
```
let price = 100;
let name = "Ter";
let discountPrice = price - 20;
```
arithmetic
```
2 * 3 + 1 // => 7
-2 + 3 // => 1
2 * (5 + 10) // => 30
50 / 2 * 2 + 10 // => 60
```

boolean
```
!true // => false
1 < 2 // => true
1 == 2 // => false
1 != 2 // => true
true == true // => true
```

condition 
```
if ( 1 < 2 ) { 
  return 10 
} else {
  return 20
}
```
implicit return
```
if ( 1 < 2 ) { 
  10 // don't need to write return
}
```

function
```
let add = fn(x , y) { x + y }
add(2, 3) // => 5
```

high-order function
```
let adder = fn(x) { fn(y) { x + y } };
let addTwo = adder(2);
addTwo(3) // => 5

let add = fn(a, b) { a + b };
let sub = fn(a, b) { a - b };
let apply = fn(a, b, func) { func(a,b) };
apply(2, 2, add); // => 4
apply(10, 2, sub); // => 8
```

string and built-in function
```
let a = "Hello"
let b = "World!!"
let helloWorld = a + " " + b // => Hello World!!

len("Hello") // => 5
len(a) // => 5
```

array and built-in function
```
let numArr = [1 + 1, 2 * 2] // => [2, 4]

let index = 1;
let arr = ["one", "two", "three"]

arr[0] // => one
arr[index] // => two
arr[1 + 1] // => three

first(arr) // => one
last(arr) // => three
rest(arr) // => ["two", "three"]
let newArr = push(arr, "four") // => ["one", "two", "three", "four"]
```

hash (int ,string ,boolean as key)

```
let two = "two";
let h = { "one" : 1, 
          two : 1 + 1, 
          "thr" + "ee": 3,
          4 : 4,
          true: 5,
          false: 6
        };
h["one"] // => 1
h["two"] // => 2
h["three"] // => 3
h[4] // => 4
h[true] // => 5
h[false] // => 6

len(h) // => 6
```
Demo Program

```
let map = fn(arr, f) {
 let iterator = fn(arr, accumulated) {
   if (len(arr) == 0) {
     accumulated
   } else {
     iterator(rest(arr) , push(accumulated, f(first(arr))));
   }
 };
 iterator(arr, []);
};

let a = [1, 2, 3, 4];
let doubleValue = fn(x) { x * 2 };
map(a, doubleValue); // => [2, 4, 6, 8]
```

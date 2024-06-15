# Lab-Recreate-Arrays

In this lab you will create a class the mimicks what the built in Array class does. Your array class will be able to show all the elements of the array, show the lenght of the array, and use the following methods: push, includes, unshift, shift, and pop.

To start, let's create the class for our new array. 

``` js
class MyArray {
    
}

const fruits = new MyArray()
console.log(fruits) // MyArray {}
```

This gives us our new class but we don't have any properties set. Let's modify our class

``` js
class MyArray {
    length = 0;
    
    constructor(...data) {
        console.log(data) // ['apple', 'orange', 'peach']
        this.elements = data;
  }
}

const fruits = new MyArray("apple", "orange", "peach");
console.log(fruits) // MyArray {length: 0, elements: Array(3)}
```

Now we get our elements as an array of fruit! Let's break it down a bit

`constructor(...data) {`
Typically, we have to define each paramater on our constructor: `constructor(param1, param2, param3)`. Instead, we can use the spread operator `...` in the paramaters of the contructor. This combines all our arguements in `new MyArray("apple", "orange", "peach");` into a single array: `['apple', 'orange', 'peach']`

But our class is not updating the length property. So our array is still a length of 0; Let's update our constructor to use a method to initalize our array.

```js
class MyArray {
    
}

const fruits = new MyArray()
console.log(fruits) // MyArray {}
This gives us our new class but we don’t have any properties set. Let’s modify our class

class MyArray {
    length = 0;
    
    constructor(...data) {
        console.log(data) // ['apple', 'orange', 'peach']
        this.elements = this.initArray(data);
  }
  
    initArray(arrayData) {
        for (const data of arrayData) {
         this.length++;
        }
    return arrayData;
    }
}

const fruits = new MyArray("apple", "orange", "peach");
console.log(fruits) // MyArray {length: 3, elements: Array(3)}
```

Now we have a working class that can create arrays! From here, you will add more methods to reproduce the functionality of the built in array methods of JavaScript. 
You cannot use built in array methods when making this. So your push method cannot just do `this.elements.push()`. Use vanilla JavaScript to recreate the push method first. Checkout MDN to see what arguements each method accepts and what each method returns.

## Push Method [#]( https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push)


```js
push(// your param(s) here) {
// your code here
}
```

### Solution

<details>
<summary>Click to expand</summary>
```js
    push(...newEl) {
    for (const element of newEl) {
      this.elements = [...this.elements, element];
      this.length++;
    }

    return this.length;
  }
```
</details>

## Includes Method [#](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)

```js
includes( ) {
    // your code here
  }
```

### Solution

<details>
<summary>Click to expand</summary>
```js
    includes(searchElement) {
    for (const element of this.elements) {
      if (element === searchElement) {
        return true;
      }
    }
    return false;
  }
```
</details>

## Unshift Method [#](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)

```js
unshift( ) {
    // your code here
  }
```

### Solution

<details>
<summary>Click to expand</summary>
```js
    unshift(...newEls) {
    for (const element of newEls) {
      this.elements = [element, ...this.elements];
      this.length++;
    }

    return this.length;
  }
```
</details>

## Shift Method [#](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)

```js
shift() {
    // your code here  
}
```

### Solution

<details>
<summary>Click to expand</summary>
```js
    shift() {
    const firstElement = this.elements[0];
    const newArray = new myArray();
    for (let i = 1; i < this.length; i++) {
      newArray.push(this.elements[i]);
    }
    this.elements = newArray.elements;
    return firstElement;
  }
```
</details>

## Pop Method [#](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)

```js
pop() {
    // your code here
  }
```

### Solution

<details>
<summary>Click to expand</summary>
```js
    pop() {
    const lastElement = this.elements[this.length - 1];
    const newArr = new myArray();
    for (let i = 0; i < this.length - 1; i++) {
      newArr.push(this.elements[i]);
    }

    this.elements = newArr.elements;

    return lastElement;
  }
```
</details>

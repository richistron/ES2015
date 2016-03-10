# ES2015

ES2015 cheatsheet by @richistron

![Work work work](http://33.media.tumblr.com/462faedb3dcb2d8ca956fa6ee7a07df7/tumblr_inline_o3a9gg8WYm1raprkq_500.gif)

### Let

```javascript
let foo = true;

if (foo) {
  let bar = true;
  console.log(bar); // true
}

console.log(true); // true
console.log(bar); // undefined
```

### Constanst

```javascript
const PUBLIC_KEY = 'abc123';

new ApiCall({
  url: '/user',
  public: PUBLIC_KEY
});

new ApiCall({
  url: '/posts',
  public: PUBLIC_KEY
});
```

### Strings

```javascript
let version = 'ES2015';

let tpl = `
<h1> Hellow World </h1>
<p> ${ version } rocks! </p>
`
```

### Map

```javascript
let dog = { name: 'dog' };
let cat = { name: 'cat' };
let animalsMap = new Map();

animalsMap.set(dog, 100);
animalsMap.set(cat, 9999);

console.log(animalsMap.get(dog)); // 100
console.log(animalsMap.get(cat)); // 9999
```

### Map

```javascript
let dog = { name: 'dog' };
let cat = { name: 'cat' };
let animalsMap = new WeakMap();

animalsMap.set(dog, 100);
animalsMap.set(cat, 9999);

console.log(animalsMap.get(dog)); // 100
console.log(animalsMap.get(cat)); // 9999
console.log(animalsMap.delete(cat)); // true
console.log(animalsMap.has(cat)); // false
```

### Object.assign

```javascript
let options = Object.assign({ foo: true, bar: true }, {foo: false});

console.log(options); // { foo: false, bar: true }
```

### Array deconstruction

```javascript
let animals = ['dog', 'cat', 'bird'];
let [dog, cat, bird] = animals;

console.log(dog, cat, bird); // dog cat bird
```

### Array deconstruction (first and last value)

```javascript
let animals = ['dog', 'cat', 'bird'];
let [dog, , bird] = animals;

console.log(dog, bird); // dog bird
```

### Array Loops

```javascript
let animals = ['dog', 'cat', 'bird'];
for (let animal of animals) {
  console.log(animal); //  dog cat bird
}
```

### Array.find

```javascript
let animals = [
  { name: 'barkie', isDog: false },
  { name: 'snowBall', isDog: false },
  { name: 'rex', isDog: true }
]

let dog = animals.find (animal) => {
  return animal.isDog;
}

console.log(dog); //   { name: 'rex', isDog: true }
```

### Sets

```javascript
let animals = new Set();

animals.add('dog');
animals.add('cat');
animals.add('dog'); // it will throw an error
console.log(animals.length); // 2
```

### WeakSet

```javascript
let weakAnimals = new WeakSet();

weakAnimals.add({ name: 'dog' });
let cat = { name: 'cat' };
weakAnimals.add(cat);

console.log(weakAnimals.has(cat)); // true
console.log(weakAnimals.delete(cat)); // true
```

### Classes

```javascript
class Animal {
  constructor(){
     this.bark();
   }

  bark(){
    console.log('woof');
  }
}

let dog = new Animal(); // woof
```

### Classes

```javascript
class Human extends Monkey{
  constructor(){
     super();
   }
}

new Human();
```

### Export

```javascript
export default class ApiCall {
  constructor(){
    //
  }
}
```

### Export

```javascript
class ApiCall {
  constructor(){
    //
  }
}

export { ApiCall }
```

### Import

```javascript
import ApiCall from './helpers/api-call'
```

### Generator Objects

```javascript
function *animalsList() {
  yield 'dog';
  yield 'cat';
  yield 'bird';
}

for (let animal of animalsList()) {
  console.log(animal);
}

let animals = [...animalsList()];
console.log(name);

let [first, second] = animalsList();
console.log(first, second);
```

### Creating a custom iterator

```javascript
let animal = {
  name: 'Dog',
  bark: true
};

animal[Symbol.iterator] = *function() {
  let properties = Object.keys(this);
  for (let p of properties) {
    yield this[p];
  }
};
```

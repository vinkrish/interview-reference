# JS Playground

[Refer here for detailed examples](https://github.com/vinkrish/sandbox/tree/master/JavaScript)

```js

const name = "Vinay";
 
console.log(`Hello ${name}!`);
 
var x = 'global';
let y = 'global';
console.log(this.x); // "global"
console.log(this.y); // undefined
 
function varTest() {
   var x = 1;
   {
     var x = 2;  // same variable!
     console.log(x);  // 2
   }
   console.log(x);  // 2   
}
varTest();

function letTest() {
   let x = 1;
   {
     let x = 2;  // different variable
     console.log(x);  // 2
   }
   console.log(x);  // 1
}
letTest();
 
function sayHello(name) {
   let closureText = "hmm";
 
   return {
       yourName: name,
       introduce() {
           console.log(`Hello ${name}, my name in Vinay!`);
           console.log(`Closure says... ${closureText}!`);
       }
   }
}
 
let sh = sayHello('Angel');
sh.introduce();

function outer(param) {
    let x = param
    let inner = function() {
        console.log(x)
    }
    return inner;
}

let func = outer(9)
func()
 
let vinay = {
   job: 'SDE',
   speak() {
       console.log("Hell with Hello World!");
   },
   wave: function() {
       console.log("just wave the hand");
   }
}
 
vinay.speak();
 
let obj1 = { name: 'Vinay' };
let obj2 = { sex: 'Male', Age: 30 };

for (const [key, value] of Object.entries(obj2)) {
    console.log(`${key}: ${value}`);
}
 
let clonedObj = {...obj2};
let mergedObj = {...obj1, ...obj2};
 
//  spread syntax below does not work as one might expect: it spreads an array of arguments into the object literal, due to the rest parameter
const merge = (...objects) => (
   {...objects}
)
 
const mergeFn = (...objects) => {
   return {...objects};
}
 
console.log('Cloned Object:');
console.log(clonedObj);
 
console.log('Merged Object:');
console.log(mergedObj);
 
let copiedObj = obj2;
obj2.sex = 'NA';
 
console.log('Copied Object sex changed:');
console.log(copiedObj);
 
console.log('Cloned Object sex does not change:');
console.log(clonedObj);
 
console.log(merge(obj1, obj2));
 
console.log(mergeFn(obj1, obj2));
 
let log = (name, ...details) => {
   console.log(`Welcome ${name}`);
   console.log(details);
   details.forEach(detail => {
       console.log(detail);
   });
   for (const detail of details) {
       console.log(detail);
   }
}
 
let arr = [{sex: 'Male'}, {Age: 30}];
let details = [{married: 'No'} , ...arr];
 
log("Vinay", ...details);
log("Vinay", details);
 
console.log("Spread:");
// spread(obj1, ...obj2);
// object themselves are not iterable, but they become iterable when used in array or with iterating functions such as map(), reduce() and assign().
log(obj1, obj2);
 
function GreetingService(name) {
   this.name = name;
   this.sayHi = function() {
           console.log(`Hello ${this.name}!`);
       };
   this.sayHiAsync = function() {
       setTimeout(function(){
           console.log(`Hello ${this.name}!`);
       },2000);
   }
   this.sayBye = function() {
           console.log(`Goodbye ${this.name}!`);
       }
}
 
let greeting = new GreetingService('Angel');
console.log(greeting);
console.log(greeting.name);
greeting.sayHi();
 
let { sayHi:hi } = new GreetingService('May Dupee');
hi();
 
greets = (name) => {
   let tempName = name;
   sayHi = () => {
       console.log(`Hello ${name}!`);
   }
   sayBye = () => {
       console.log(`Bye ${name}`);
   }
   return {newName: tempName, sayHi, sayBye};
}
let greet = greets("Ango");
console.log(greet);
greet.sayHi();
 
let { newName, sayBye:bye } = greets("Dupee");
console.log(newName);
bye();

let arr = [1,2,3]
square = (x) => {
    return x*x
}
let squared = arr.map(square)
let squared = arr.map(x => square(x))
console.log(squared)

```
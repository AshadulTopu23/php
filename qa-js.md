২০০টি JavaScript প্রশ্ন ও উত্তর (বাংলায়)
JavaScript বেসিক (প্রশ্ন ১-৩০)
প্রশ্ন ১: JavaScript কি?
উত্তর: JavaScript একটি উচ্চ-স্তরের, ইন্টারপ্রেটেড প্রোগ্রামিং ভাষা যা ওয়েব পেজকে ইন্টারঅ্যাকটিভ করে তোলে। এটি HTML এবং CSS এর সাথে কাজ করে।

প্রশ্ন ২: JavaScript এর ডাটা টাইপগুলো কি কি?
উত্তর:

Primitive: String, Number, Boolean, Undefined, Null, Symbol, BigInt

Non-primitive: Object, Array, Function

প্রশ্ন ৩: var, let, const এর মধ্যে পার্থক্য কি?
উত্তর:

var: function-scoped, hoisting হয়, redeclare করা যায়

let: block-scoped, hoisting হয় কিন্তু initialization এর আগে access করা যায় না (TDZ), redeclare করা যায় না

const: block-scoped, reassign করা যায় না, declaration এর সময় initialize করতে হয়

প্রশ্ন ৪: JavaScript এ comment লেখার নিয়ম কি?
উত্তর:

javascript
// Single line comment

/*
   Multi-line
   comment
*/
প্রশ্ন ৫: == এবং === এর মধ্যে পার্থক্য কি?
উত্তর:

== (loose equality): শুধু value check করে, type coercion করে

=== (strict equality): value এবং type উভয়ই check করে, type coercion করে না

প্রশ্ন ৬: null এবং undefined এর মধ্যে পার্থক্য কি?
উত্তর:

null: ইচ্ছাকৃতভাবে empty value set করা, এটি একটি object

undefined: variable declare করা হয়েছে কিন্তু value assign করা হয়নি

প্রশ্ন ৭: typeof অপারেটর কি রিটার্ন করে?
উত্তর:

javascript
typeof "Hello"     // "string"
typeof 42          // "number"
typeof true        // "boolean"
typeof undefined   // "undefined"
typeof null        // "object" (JavaScript এর bug)
typeof {}          // "object"
typeof []          // "object"
typeof function(){} // "function"
প্রশ্ন ৮: NaN কি?
উত্তর: NaN (Not a Number) একটি সংখ্যা যা valid number নয়। এটি check করতে isNaN() ব্যবহার করা হয়।

প্রশ্ন ৯: isNaN() এবং Number.isNaN() এর পার্থক্য কি?
উত্তর:

isNaN(): value কে number এ convert করার চেষ্টা করে, তারপর check করে

Number.isNaN(): শুধু check করে value টি NaN কিনা (type coercion করে না)

প্রশ্ন ১০: Template literal কি?
উত্তর: Template literal ব্যাকটিক (`) ব্যবহার করে string লিখার একটি পদ্ধতি যা variable embed এবং multi-line string support করে।

javascript
let name = "Rahim";
let greeting = `Hello ${name}`;
প্রশ্ন ১১: JavaScript এ array কিভাবে ডিক্লেয়ার করে?
উত্তর:

javascript
let arr1 = [1, 2, 3];
let arr2 = new Array(1, 2, 3);
প্রশ্ন ১২: Array এর length property কিভাবে কাজ করে?
উত্তর: length array তে কয়টি element আছে তা return করে। এটি writable, মানে আমরা length পরিবর্তন করে array কে truncate বা extend করতে পারি।

প্রশ্ন ১৩: push() এবং pop() মেথড কি করে?
উত্তর:

push(): array এর শেষে এক বা একাধিক element যোগ করে এবং নতুন length return করে

pop(): array এর শেষ element সরিয়ে ফেলে এবং সেটি return করে

প্রশ্ন ১৪: shift() এবং unshift() মেথড কি করে?
উত্তর:

shift(): array এর প্রথম element সরিয়ে ফেলে এবং সেটি return করে

unshift(): array এর শুরুতে এক বা একাধিক element যোগ করে এবং নতুন length return করে

প্রশ্ন ১৫: splice() এবং slice() এর পার্থক্য কি?
উত্তর:

splice(): array থেকে element যোগ/remove করে এবং original array modify করে

slice(): array এর একটি অংশ কপি করে নতুন array return করে, original array অপরিবর্তিত থাকে

প্রশ্ন ১৬: map(), filter(), reduce() এর কাজ কি?
উত্তর:

map(): প্রতিটি element এ function apply করে নতুন array return করে

filter(): নির্দিষ্ট condition পূরণ করে এমন element নিয়ে নতুন array return করে

reduce(): array কে একটি single value এ reduce করে

প্রশ্ন ১৭: forEach() এবং map() এর মধ্যে পার্থক্য কি?
উত্তর:

forEach(): array iterate করে, কিন্তু কিছু return করে না (undefined)

map(): array iterate করে এবং নতুন array return করে

প্রশ্ন ১৮: JavaScript এ object কিভাবে ডিক্লেয়ার করে?
উত্তর:

javascript
let obj1 = { name: "Rahim", age: 25 };
let obj2 = new Object();
obj2.name = "Karim";
প্রশ্ন ১৯: Object এর property access করার উপায় কি?
উত্তর:

Dot notation: obj.name

Bracket notation: obj["name"]

প্রশ্ন ২০: this কীওয়ার্ড কি?
উত্তর: this current execution context কে reference করে। এটি যেখানে ব্যবহৃত হয় তার উপর ভিত্তি করে এর মান পরিবর্তিত হয়।

প্রশ্ন ২১: call(), apply(), bind() এর মধ্যে পার্থক্য কি?
উত্তর:

call(): function টি সাথে সাথে execute করে, arguments কমা দিয়ে পাঠানো হয়

apply(): function টি সাথে সাথে execute করে, arguments array আকারে পাঠানো হয়

bind(): নতুন function return করে যা পরে call করা যায়

প্রশ্ন ২২: function declaration এবং function expression এর পার্থক্য কি?
উত্তর:

Function declaration: hoisting হয়, function নাম থাকে

javascript
function greet() { }
Function expression: hoisting হয় না, variable এ assign করা হয়

javascript
let greet = function() { };
প্রশ্ন ২৩: Arrow function এবং regular function এর পার্থক্য কি?
উত্তর:

Arrow function এর নিজস্ব this থাকে না, এটি lexical scope থেকে this নেয়

Arrow function arguments object support করে না

Arrow function কে constructor হিসেবে ব্যবহার করা যায় না (new দিয়ে call করা যায় না)

প্রশ্ন ২৪: Immediately Invoked Function Expression (IIFE) কি?
উত্তর: IIFE এমন একটি function যা ডিক্লেয়ার করার সাথে সাথে execute হয়।

javascript
(function() {
    console.log("Executed immediately");
})();
প্রশ্ন ২৫: Closure কি?
উত্তর: Closure হল যখন একটি inner function তার outer function এর variable গুলো access করতে পারে, এমনকি outer function return হওয়ার পরও।

প্রশ্ন ২৬: Hoisting কি?
উত্তর: Hoisting হল JavaScript এর একটি mechanism যেখানে variable এবং function declaration কে তাদের scope এর উপরে নিয়ে যাওয়া হয় execution এর আগে।

প্রশ্ন ২৭: Temporal Dead Zone (TDZ) কি?
উত্তর: TDZ হল let এবং const variable initialization এর আগে那段 সময় যখন variable access করা যায় না।

প্রশ্ন ২৮: Scope chain কি?
উত্তর: Scope chain হল যখন JavaScript engine variable খুঁজতে থাকে - প্রথমে current scope, তারপর parent scope, এবং শেষ পর্যন্ত global scope পর্যন্ত।

প্রশ্ন ২৯: Truthy এবং Falsy value কি?
উত্তর:

Falsy values: false, 0, "" (empty string), null, undefined, NaN

Truthy values: falsy ছাড়া সবকিছু

প্রশ্ন ৩০: Type coercion কি?
উত্তর: Type coercion হল যখন JavaScript automatically এক data type কে অন্য data type এ convert করে।

JavaScript ফাংশন ও স্কোপ (প্রশ্ন ৩১-৫০)
প্রশ্ন ৩১: Default parameter কি?
উত্তর: Function parameter এর জন্য default value set করা যায় যা argument না দিলে ব্যবহৃত হয়।

javascript
function greet(name = "Guest") {
    return `Hello ${name}`;
}
প্রশ্ন ৩২: Rest parameter কি?
উত্তর: Rest parameter (...) function এ indefinite number of arguments কে array হিসেবে নেয়।

javascript
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}
প্রশ্ন ৩৩: Spread operator কি?
উত্তর: Spread operator (...) array বা object কে expand করে।

javascript
let arr1 = [1, 2, 3];
let arr2 = [...arr1, 4, 5]; // [1,2,3,4,5]
প্রশ্ন ৩৪: Destructuring কি?
উত্তর: Destructuring হল array বা object থেকে value extract করে variable এ assign করার একটি উপায়।

javascript
let [a, b] = [1, 2];
let {name, age} = {name: "Rahim", age: 25};
প্রশ্ন ৩৫: Higher-order function কি?
উত্তর: Higher-order function হল সেই function যা অন্য function কে parameter হিসেবে নেয় অথবা function return করে।

প্রশ্ন ৩৬: Callback function কি?
উত্তর: Callback function হল একটি function যা অন্য function এ argument হিসেবে পাঠানো হয় এবং পরে execute হয়।

প্রশ্ন ৩৭: Pure function কি?
উত্তর: Pure function হল সেই function যা:

একই input এ সবসময় একই output return করে

কোন side effect (বাইরের state change) করে না

প্রশ্ন ৩৮: Recursion কি?
উত্তর: Recursion হল যখন একটি function নিজেই নিজেকে call করে।

javascript
function factorial(n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}
প্রশ্ন ৩৯: Memoization কি?
উত্তর: Memoization হল expensive function call এর result cache করে রাখার একটি optimization technique।

প্রশ্ন ৪০: Currying কি?
উত্তর: Currying হল একটি technique যেখানে multiple argument বিশিষ্ট function কে sequence of functions এ রূপান্তর করা হয়।

প্রশ্ন ৪১: Function composition কি?
উত্তর: Function composition হল একাধিক function কে combine করে একটি নতুন function তৈরি করা।

প্রশ্ন ৪২: Debouncing এবং Throttling কি?
উত্তর:

Debouncing: নির্দিষ্ট সময়ে function call delay করে, যদি বারবার call হয় তাহলে reset হয়

Throttling: function call কে নির্দিষ্ট সময়ে একবার execute হতে দেয়

প্রশ্ন ৪৩: Generator function কি?
উত্তর: Generator function (function*) একাধিক value yield করতে পারে এবং pause/resume করা যায়।

প্রশ্ন ৪৪: arguments object কি?
উত্তর: arguments একটি array-like object যা function এ passed সব arguments ধারণ করে (arrow function এ কাজ করে না)।

প্রশ্ন ৪৫: function.length property কি return করে?
উত্তর: function.length function এ কতটি parameter ডিফাইন করা আছে তা return করে (default parameter count করা হয় না)।

প্রশ্ন ৪৬: Function নাম্বারিং এবং NFE (Named Function Expression) কি?
উত্তর: Named function expression হল একটি function expression যার একটি নাম আছে, যা function এর ভিতরে নিজেকে reference করতে পারে।

প্রশ্ন ৪৭: new.target কি?
উত্তর: new.target property detect করে function টি new keyword দিয়ে call করা হয়েছে কিনা।

প্রশ্ন ৪৮: eval() কি এবং কেন এটি avoid করা উচিত?
উত্তর: eval() string কে code হিসেবে execute করে। এটি security risk এবং performance issue তৈরি করতে পারে।

প্রশ্ন ৪৯: setTimeout() এবং setInterval() এর পার্থক্য কি?
উত্তর:

setTimeout(): নির্দিষ্ট সময় পর একবার function execute করে

setInterval(): নির্দিষ্ট সময় পর পর বারবার function execute করে

প্রশ্ন ৫০: clearTimeout() এবং clearInterval() কেন ব্যবহার করা হয়?
উত্তর: timer বন্ধ করতে, যাতে scheduled function execute না হয়।

JavaScript অবজেক্ট ও প্রোটোটাইপ (প্রশ্ন ৫১-৭০)
প্রশ্ন ৫১: Object.create() কি করে?
উত্তর: Object.create() একটি নতুন object তৈরি করে যার prototype হিসেবে specified object থাকে।

প্রশ্ন ৫২: Object.assign() কি করে?
উত্তর: Object.assign() এক বা একাধিক source object থেকে target object এ properties কপি করে।

প্রশ্ন ৫৩: Object.freeze() এবং Object.seal() এর পার্থক্য কি?
উত্তর:

Object.freeze(): object কে সম্পূর্ণ immutable করে দেয় (add/update/delete কিছুই করা যায় না)

Object.seal(): নতুন property যোগ বা delete করা যায় না, কিন্তু existing property update করা যায়

প্রশ্ন ৫৪: Object.entries(), Object.keys(), Object.values() কি করে?
উত্তর:

Object.keys(): object এর keys এর array return করে

Object.values(): object এর values এর array return করে

Object.entries(): object এর [key, value] pairs এর array return করে

প্রশ্ন ৫৫: hasOwnProperty() কি চেক করে?
উত্তর: object এর নিজস্ব property আছে কিনা (prototype chain থেকে আসা না) চেক করে।

প্রশ্ন ৫৬: Prototype কি?
উত্তর: Prototype হল একটি mechanism যার মাধ্যমে JavaScript object অন্য object থেকে properties এবং methods inherit করে।

প্রশ্ন ৫৭: Prototype chain কি?
উত্তর: Prototype chain হল object গুলোর একটি chain যার মাধ্যমে property access করা হয়। যদি object এ property না থাকে, তাহলে তার prototype এ খোঁজে, এবং এভাবে chain ধরে যায়।

প্রশ্ন ৫৮: proto এবং prototype এর মধ্যে পার্থক্য কি?
উত্তর:

proto: প্রতিটি object এর property যা তার prototype কে points করে

prototype: শুধু function এর property, যা new keyword দিয়ে তৈরি object এর proto সেট করে

প্রশ্ন ৫৯: Class syntax কিভাবে কাজ করে?
উত্তর: JavaScript এ class হল syntactic sugar over prototype-based inheritance।

javascript
class Person {
    constructor(name) {
        this.name = name;
    }
    
    greet() {
        return `Hello ${this.name}`;
    }
}
প্রশ্ন ৬০: extends keyword কি করে?
উত্তর: extends একটি class কে অন্য class এর child class বানাতে ব্যবহার করা হয় (inheritance)।

প্রশ্ন ৬১: super() keyword কি করে?
উত্তর: super() parent class এর constructor call করে। child class এ this ব্যবহারের আগে super() call করতে হয়।

প্রশ্ন ৬২: Static method কি?
উত্তর: Static method class এর instance না বানিয়েই সরাসরি class নামে call করা যায়।

প্রশ্ন ৬৩: Getter এবং Setter কি?
উত্তর: Getter এবং Setter হল special method যা property এর value access এবং assign করার সময় custom logic প্রয়োগ করে।

প্রশ্ন ৬৪: instanceof operator কি চেক করে?
উত্তর: instanceof check করে একটি object নির্দিষ্ট class বা constructor function এর instance কিনা।

প্রশ্ন ৬৫: Mixin কি?
উত্তর: Mixin হল একটি class যা অন্য class এ ব্যবহারের জন্য methods ধারণ করে, কিন্তু নিজে instantiate হয় না।

প্রশ্ন ৬৬: Object property descriptor কি?
উত্তর: Property descriptor object এর property সম্পর্কে মেটাডেটা ধারণ করে (writable, enumerable, configurable, value, get, set)।

প্রশ্ন ৬৭: Object.defineProperty() কি করে?
উত্তর: Object.defineProperty() একটি object এ নতুন property define করে বা existing property modify করে এবং তার descriptor সেট করে।

প্রশ্ন ৬৮: Object.preventExtensions() কি করে?
উত্তর: Object.preventExtensions() object এ নতুন property যোগ করা বন্ধ করে দেয়, কিন্তু existing property delete বা update করা যায়।

প্রশ্ন ৬৯: Object.is() এবং === এর পার্থক্য কি?
উত্তর: Object.is() strict equality এর মতো, কিন্তু কিছু edge cases এ আলাদা আচরণ করে (NaN, +0, -0)।

প্রশ্ন ৭০: Property enumeration order কিভাবে নির্ধারিত হয়?
উত্তর:

Integer keys ascending order এ

String keys insertion order এ

Symbol keys insertion order এ

JavaScript অ্যারে ও ইটারেশন (প্রশ্ন ৭১-৯০)
প্রশ্ন ৭১: Array.isArray() কেন ব্যবহার করা হয়?
উত্তর: Array.isArray() check করে একটি value array কিনা (typeof [] "object" return করে বলে)।

প্রশ্ন ৭২: find() এবং filter() এর পার্থক্য কি?
উত্তর:

find(): প্রথম element যে condition পূরণ করে, তাকে return করে

filter(): সব element যে condition পূরণ করে, তাদের array return করে

প্রশ্ন ৭৩: some() এবং every() এর পার্থক্য কি?
উত্তর:

some(): অন্তত একটি element condition পূরণ করলে true return করে

every(): সব element condition পূরণ করলে true return করে

প্রশ্ন ৭৪: includes() এবং indexOf() এর পার্থক্য কি?
উত্তর:

includes(): element আছে কিনা boolean return করে (NaN detect করে)

indexOf(): element এর index return করে, না থাকলে -1 (NaN detect করে না)

প্রশ্ন ৭৫: flat() এবং flatMap() কি করে?
উত্তর:

flat(): nested array কে নির্দিষ্ট depth পর্যন্ত flatten করে

flatMap(): প্রথমে map() তারপর flat(1) করে

প্রশ্ন ৭৬: sort() মেথড কিভাবে কাজ করে?
উত্তর: sort() array কে in-place sort করে। সংখ্যার জন্য compare function দিতে হয়, নাহলে string হিসেবে sort করে।

প্রশ্ন ৭৭: reverse() মেথড কি করে?
উত্তর: reverse() array এর element গুলো reverse করে (in-place)।

প্রশ্ন ৭৮: join() মেথড কি করে?
উত্তর: join() array এর সব element কে string এ convert করে নির্দিষ্ট separator দিয়ে যুক্ত করে।

প্রশ্ন ৭৯: concat() মেথড কি করে?
উত্তর: concat() দুই বা ততোধিক array merge করে নতুন array return করে।

প্রশ্ন ৮০: fill() মেথড কি করে?
উত্তর: fill() array এর নির্দিষ্ট অংশ একটি static value দিয়ে fill করে।

প্রশ্ন ৮১: copyWithin() মেথড কি করে?
উত্তর: copyWithin() array এর মধ্যে element কে এক স্থান থেকে অন্য স্থানে copy করে।

প্রশ্ন ৮২: Array.from() কি করে?
উত্তর: Array.from() array-like বা iterable object থেকে নতুন array তৈরি করে।

প্রশ্ন ৮৩: Array.of() কি করে?
উত্তর: Array.of() arguments থেকে নতুন array তৈরি করে (new Array() এর problem এড়াতে)।

প্রশ্ন ৮৪: Iterable এবং Iterator কি?
উত্তর:

Iterable: যে object এর Symbol.iterator method আছে (যেমন: Array, String, Map, Set)

Iterator: { value, done } object return করে এমন object

প্রশ্ন ৮৫: for...of এবং for...in loop এর পার্থক্য কি?
উত্তর:

for...of: iterable এর value নিয়ে iterate করে (Array, String, Map, Set)

for...in: object এর enumerable property keys নিয়ে iterate করে

প্রশ্ন ৮৬: Set কি?
উত্তর: Set হল unique value collection (কোন duplicate value নেই)।

প্রশ্ন ৮৭: Map কি?
উত্তর: Map হল key-value pair collection যেখানে key যেকোনো type হতে পারে (object এ key শুধু string বা symbol)।

প্রশ্ন ৮৮: WeakSet এবং WeakMap কি?
উত্তর:

WeakSet: শুধু object রাখে, weak reference, garbage collected, iterate করা যায় না

WeakMap: শুধু object key রাখে, weak reference, garbage collected, iterate করা যায় না

প্রশ্ন ৮৯: Array destructuring এ default value কিভাবে set করে?
উত্তর: let [a = 10, b = 20] = [5]; // a=5, b=20

প্রশ্ন ৯০: Swapping variables using array destructuring
javascript
let a = 5, b = 10;
[a, b] = [b, a];
JavaScript অ্যাসিনক্রোনাস প্রোগ্রামিং (প্রশ্ন ৯১-১১০)
প্রশ্ন ৯১: Synchronous এবং Asynchronous code এর পার্থক্য কি?
উত্তর:

Synchronous: code line by line execute হয়, এক line শেষ না হলে পরের line যায় না (blocking)

Asynchronous: code execute করতে সময় লাগলে, পরের line চলে যায় (non-blocking)

প্রশ্ন ৯২: Callback hell কি?
উত্তর: Callback hell হল nested callback এর একটি অবস্থা যা code পড়া এবং maintain করা কঠিন করে তোলে।

প্রশ্ন ৯৩: Promise কি?
উত্তর: Promise হল asynchronous operation এর eventual completion (বা failure) প্রতিনিধিত্ব করে।

প্রশ্ন ৯৪: Promise এর state গুলো কি কি?
উত্তর:

pending: initial state, neither fulfilled nor rejected

fulfilled: operation সফলভাবে সম্পন্ন হয়েছে

rejected: operation ব্যর্থ হয়েছে

প্রশ্ন ৯৫: Promise চেইনিং কিভাবে কাজ করে?
উত্তর: .then() একাধিক বার chain করা যায়, প্রতিটি পরের .then() আগেরটির result পায়।

প্রশ্ন ৯৬: Promise.all() কি করে?
উত্তর: Promise.all() সব promise fulfilled হলে তাদের result এর array return করে। একটি reject হলে সব reject হয়।

প্রশ্ন ৯৭: Promise.race() কি করে?
উত্তর: Promise.race() যে promise প্রথমে settle হয় (fulfill/reject) তার result return করে।

প্রশ্ন ৯৮: Promise.allSettled() কি করে?
উত্তর: Promise.allSettled() সব promise settle না হওয়া পর্যন্ত wait করে, প্রতিটির status এবং value/reason সহ array return করে।

প্রশ্ন ৯৯: Promise.any() কি করে?
উত্তর: Promise.any() প্রথম fulfilled promise এর result return করে। সব reject হলে AggregateError throw করে।

প্রশ্ন ১০০: async/await কি?
উত্তর: async/await হল promises নিয়ে কাজ করার syntactic sugar যা asynchronous code কে synchronous এর মতো দেখায়।

প্রশ্ন ১০১: try/catch/finally block কিভাবে কাজ করে?
উত্তর:

try: code যে error throw করতে পারে

catch: error হলে execute হয়

finally: error হোক বা না হোক, সবসময় execute হয়

প্রশ্ন ১০২: Error handling এ throw keyword এর ব্যবহার কি?
উত্তর: throw manually error throw করতে ব্যবহৃত হয়।

প্রশ্ন ১০৩: Custom error কিভাবে তৈরি করে?
উত্তর: class CustomError extends Error { }

প্রশ্ন ১০৪: Event loop কি?
উত্তর: Event loop হল একটি mechanism যা call stack এবং callback queue monitor করে এবং call stack খালি হলে queue থেকে callback গুলো stack এ পাঠায়।

প্রশ্ন ১০৫: Microtask এবং Macrotask এর পার্থক্য কি?
উত্তর:

Microtask: Promise.then, queueMicrotask, MutationObserver (higher priority)

Macrotask: setTimeout, setInterval, I/O, UI rendering

প্রশ্ন ১০৬: setTimeout(fn, 0) কেন ব্যবহার করা হয়?
উত্তর: current stack clear হওয়ার পর function execute করতে, অথবা UI blocking এড়াতে।

প্রশ্ন ১০৭: Web Worker কি?
উত্তর: Web Worker background এ script run করার একটি উপায়, main thread blocking না করে।

প্রশ্ন ১০৮: Service Worker কি?
উত্তর: Service Worker হল network proxy যা offline functionality, push notifications, background sync enable করে।

প্রশ্ন ১০৯: Event delegation কি?
উত্তর: Event delegation হল parent এ event listener attach করে children এর events handle করার technique।

প্রশ্ন ১১০: Debounce function implement করুন
javascript
function debounce(func, delay) {
    let timeoutId;
    return function(...args) {
        clearTimeout(timeoutId);
        timeoutId = setTimeout(() => func.apply(this, args), delay);
    };
}
JavaScript DOM ম্যানিপুলেশন (প্রশ্ন ১১১-১৩০)
প্রশ্ন ১১১: DOM কি?
উত্তর: DOM (Document Object Model) হল HTML document এর tree-like representation যা JavaScript দিয়ে manipulate করা যায়।

প্রশ্ন ১১২: document.getElementById() কি করে?
উত্তর: নির্দিষ্ট id বিশিষ্ট element কে return করে।

প্রশ্ন ১১৩: document.getElementsByClassName() কি রিটার্ন করে?
উত্তর: নির্দিষ্ট class name বিশিষ্ট element গুলোর live HTMLCollection return করে।

প্রশ্ন ১১৪: document.getElementsByTagName() কি রিটার্ন করে?
উত্তর: নির্দিষ্ট tag name বিশিষ্ট element গুলোর live HTMLCollection return করে।

প্রশ্ন ১১৫: document.querySelector() এবং document.querySelectorAll() এর পার্থক্য কি?
উত্তর:

querySelector(): CSS selector এর সাথে match করা প্রথম element return করে

querySelectorAll(): সব matching element এর static NodeList return করে

প্রশ্ন ১১৬: createElement() এবং appendChild() কিভাবে কাজ করে?
উত্তর:

createElement(): নতুন element তৈরি করে

appendChild(): element টি parent এর শেষ child হিসেবে যোগ করে

প্রশ্ন ১১৭: innerHTML এবং textContent এর পার্থক্য কি?
উত্তর:

innerHTML: HTML content set/get করে (HTML parse করে)

textContent: শুধু text content set/get করে (HTML parse করে না, faster)

প্রশ্ন ১১৮: classList property কি করে?
উত্তর: classList element এর class গুলো manipulate করার methods দেয়: add(), remove(), toggle(), contains().

প্রশ্ন ১১৯: setAttribute() এবং getAttribute() কি করে?
উত্তর: element এর attribute set এবং get করতে।

প্রশ্ন ১২০: removeChild() এবং remove() এর পার্থক্য কি?
উত্তর:

removeChild(): parent থেকে child remove করে (parent reference লাগে)

remove(): element নিজেই নিজেকে remove করে

প্রশ্ন ১২১: insertBefore() এবং insertAdjacentElement() এর ব্যবহার কি?
উত্তর: নির্দিষ্ট position এ element insert করতে।

প্রশ্ন ১২২: cloneNode() কি করে?
উত্তর: element clone করে। true argument দিলে deep clone (children সহ) হয়।

প্রশ্ন ১২৩: parentNode, childNodes, firstChild, lastChild property গুলো কি?
উত্তর: DOM tree traverse করার properties।

প্রশ্ন ১২৪: nextSibling এবং previousSibling vs nextElementSibling এবং previousElementSibling এর পার্থক্য কি?
উত্তর:

Sibling versions: text node সহ সব node consider করে

ElementSibling versions: শুধু element nodes consider করে

প্রশ্ন ১২৫: offsetWidth, clientWidth, scrollWidth এর পার্থক্য কি?
উত্তর:

offsetWidth: element width + padding + border + scrollbar

clientWidth: element width + padding (শুধু visible part)

scrollWidth: element width + padding (সম্পূর্ণ content, scrollable part সহ)

প্রশ্ন ১২৬: getComputedStyle() কি করে?
উত্তর: element এর computed style (final applied style) return করে।

প্রশ্ন ১২৭: window.innerWidth এবং document.documentElement.clientWidth এর পার্থক্য কি?
উত্তর:

innerWidth: viewport width including scrollbar

clientWidth: viewport width excluding scrollbar

প্রশ্ন ১২৮: scrollTo(), scrollBy(), scrollIntoView() এর ব্যবহার কি?
উত্তর: page বা element scroll করার methods।

প্রশ্ন ১২৯: dataset property কি?
উত্তর: data-* attributes access করার জন্য।

প্রশ্ন ১৩০: createDocumentFragment() কেন ব্যবহার করা হয়?
উত্তর: performance improve করতে। fragment এ element যোগ করে একবার DOM এ attach করা যায়, multiple reflow avoid করে।

JavaScript ইভেন্ট হ্যান্ডলিং (প্রশ্ন ১৩১-১৫০)
প্রশ্ন ১৩১: addEventListener() এর সিনট্যাক্স কি?
উত্তর: element.addEventListener(event, function, useCapture)

প্রশ্ন ১৩২: removeEventListener() কিভাবে ব্যবহার করে?
উত্তর: একই function reference দিয়ে remove করতে হবে।

প্রশ্ন ১৩৩: Event object কি?
উত্তর: Event ঘটলে browser একটি event object তৈরি করে যাতে event সম্পর্কিত তথ্য থাকে।

প্রশ্ন ১৩৪: preventDefault() কি করে?
উত্তর: element এর default behavior বন্ধ করে (যেমন: link follow করা, form submit করা)।

প্রশ্ন ১৩৫: stopPropagation() কি করে?
উত্তর: event bubbling/capturing বন্ধ করে।

প্রশ্ন ১৩৬: stopImmediatePropagation() কি করে?
উত্তর: event propagation বন্ধ করে এবং একই element এ অন্য কোনো listener execute হতে দেয় না।

প্রশ্ন ১৩৭: Event bubbling এবং capturing এর পার্থক্য কি?
উত্তর:

Bubbling: event target থেকে উপরের দিকে propagate হয়

Capturing: event window থেকে নিচের দিকে target পর্যন্ত propagate হয়

প্রশ্ন ১৩৮: target এবং currentTarget এর পার্থক্য কি?
উত্তর:

target: যে element এ event ঘটেছে

currentTarget: যে element এ listener attach করা আছে

প্রশ্ন ১৩৯: Custom event কিভাবে তৈরি করে?
javascript
let event = new CustomEvent('myEvent', { detail: { data: 'hello' } });
element.dispatchEvent(event);
প্রশ্ন ১৪০: Mouse event গুলো কি কি?
উত্তর: click, dblclick, mousedown, mouseup, mouseover, mouseout, mousemove, mouseenter, mouseleave

প্রশ্ন ১৪১: Keyboard event গুলো কি কি?
উত্তর: keydown, keypress (deprecated), keyup

প্রশ্ন ১৪২: Focus event গুলো কি কি?
উত্তর: focus, blur, focusin, focusout

প্রশ্ন ১৪৩: Form event গুলো কি কি?
উত্তর: submit, change, input, reset

প্রশ্ন ১৪৪: Drag and drop event গুলো কি কি?
উত্তর: dragstart, drag, dragenter, dragleave, dragover, drop, dragend

প্রশ্ন ১৪৫: Touch event গুলো কি কি?
উত্তর: touchstart, touchmove, touchend, touchcancel

প্রশ্ন ১৪৬: Scroll event handle করার best practice কি?
উত্তর: performance এর জন্য scroll event এ debounce বা throttle ব্যবহার করা।

প্রশ্ন ১৪৭: Resize event handle করার উপায়?
উত্তর: window.addEventListener('resize', handler)

প্রশ্ন ১৪৮: Load এবং DOMContentLoaded এর পার্থক্য কি?
উত্তর:

DOMContentLoaded: HTML loaded এবং DOM tree ready (images, stylesheets নাও load হতে পারে)

load: সম্পূর্ণ page (সব resource) loaded

প্রশ্ন ১৪৯: beforeunload এবং unload event কখন ব্যবহার হয়?
উত্তর: page leave করার আগে cleanup বা user confirm নেওয়ার জন্য।

প্রশ্ন ১৫০: Pointer event কি?
উত্তর: Unified way to handle mouse, touch, pen inputs।

JavaScript ES6+ ফিচার (প্রশ্ন ১৫১-১৭০)
প্রশ্ন ১৫১: let এবং const এর block scope কিভাবে কাজ করে?
উত্তর: {} এর ভিতরে ডিক্লেয়ার করা let/const শুধু ঐ block এ accessible।

প্রশ্ন ১৫২: Template literal এ expression embed করার নিয়ম কি?
উত্তর: ${expression}

প্রশ্ন ১৫৩: Tagged template কি?
উত্তর: Function call করে template literal process করার উপায়।

প্রশ্ন ১৫৪: Arrow function এ this কিভাবে কাজ করে?
উত্তর: Arrow function এর নিজস্ব this নেই, এটি lexical scope (যেখানে ডিক্লেয়ার করা হয়েছে) থেকে this নেয়।

প্রশ্ন ১৫৫: Object literal এ shorthand property এবং method
javascript
let name = "Rahim";
let obj = { name, greet() { return "Hello"; } };
প্রশ্ন ১৫৬: Computed property names কি?
উত্তর: Object literal এ dynamic key দিতে [expression] ব্যবহার করা।

প্রশ্ন ১৫৭: Symbol কি এবং কেন ব্যবহার করা হয়?
উত্তর: Symbol unique identifier তৈরি করে, object এ private property তৈরি করতে বা built-in behavior customize করতে (Symbol.iterator)।

প্রশ্ন ১৫৮: BigInt কি?
উত্তর: BigInt হল খুব বড় integer (Number.MAX_SAFE_INTEGER এর চেয়ে বড়) represent করার জন্য।

প্রশ্ন ১৫৯: Nullish coalescing operator (??) কি?
উত্তর: ?? শুধু null বা undefined এর জন্য default value দেয় (|| falsy value এর জন্য দেয়)।

প্রশ্ন ১৬০: Optional chaining (?.) কি?
উত্তর: ?. property access করার সময় যদি null/undefined হয় তাহলে error না দিয়ে undefined return করে।

প্রশ্ন ১৬১: Logical assignment operators (&&=, ||=, ??=) কি?
উত্তর: logical operator এর সাথে assignment combine করে।

প্রশ্ন ১৬২: Promise.allSettled() এর ব্যবহার কি?
উত্তর: সব promise settle হওয়ার পর তাদের result জানতে, চাইলে কেউ reject করলেও।

প্রশ্ন ১৬৩: String.prototype.replaceAll() কি করে?
উত্তর: সব matching substring replace করে (regular expression না দিলেও)।

প্রশ্ন ১৬৪: Array.prototype.at() মেথড কি করে?
উত্তর: positive/negative index দিয়ে array element access করতে (negative শেষ থেকে)।

প্রশ্ন ১৬৫: Object.hasOwn() এবং hasOwnProperty() এর পার্থক্য কি?
উত্তর: Object.hasOwn() is safer (যদি object hasOwnProperty override করে)।

প্রশ্ন ১৬৬: Top-level await কি?
উত্তর: Module এ async function ছাড়া await ব্যবহার করা যায়।

প্রশ্ন ১৬৭: WeakRef এবং FinalizationRegistry কি?
উত্তর: Weak reference এবং garbage collection notification এর জন্য।

প্রশ্ন ১৬৮: Private class fields (#) কিভাবে কাজ করে?
উত্তর: # দিয়ে class এ private field ডিফাইন করা যায়।

প্রশ্ন ১৬৯: Static class fields এবং methods
javascript
class MyClass {
    static count = 0;
    static increment() { this.count++; }
}
প্রশ্ন ১৭০: Import maps কি?
উত্তর: Browser এ module import path map করার জন্য।

JavaScript ব্রাউজার API (প্রশ্ন ১৭১-১৮৫)
প্রশ্ন ১৭১: localStorage এবং sessionStorage এর পার্থক্য কি?
উত্তর:

localStorage: data persistent থাকে, manually clear না করা পর্যন্ত

sessionStorage: tab/browser close করলে data clear হয়

প্রশ্ন ১৭২: Cookie, localStorage, sessionStorage এর মধ্যে পার্থক্য কি?
উত্তর:

Cookie: server/client both access করতে পারে, size limit 4KB, expires set করা যায়

localStorage: client-side only, size 5-10MB, no expiration

sessionStorage: client-side only, tab close এ clear

প্রশ্ন ১৭৩: IndexedDB কি?
উত্তর: Browser এ structured data store করার জন্য low-level API (NoSQL database)।

প্রশ্ন ১৭৪: Geolocation API কিভাবে ব্যবহার করে?
javascript
navigator.geolocation.getCurrentPosition(successCallback, errorCallback);
প্রশ্ন ১৭৫: Notification API কি?
উত্তর: Desktop notification দেখানোর জন্য।

প্রশ্ন ১৭৬: Fetch API কিভাবে কাজ করে?
javascript
fetch(url)
    .then(response => response.json())
    .then(data => console.log(data));
প্রশ্ন ১৭৭: WebSocket কি?
উত্তর: Full-duplex communication protocol, real-time data exchange এর জন্য।

প্রশ্ন ১৭৮: Server-Sent Events (SSE) কি?
উত্তর: Server থেকে client এ real-time data push করার জন্য (HTTP based, one-way)।

প্রশ্ন ১৭৯: Canvas API কি করে?
উত্তর: JavaScript দিয়ে graphics এবং animation draw করার জন্য।

প্রশ্ন ১৮০: WebGL কি?
উত্তর: Browser এ 3D graphics render করার জন্য API।

প্রশ্ন ১৮১: History API কি করে?
উত্তর: Browser history manipulate করার জন্য (pushState, replaceState)।

প্রশ্ন ১৮২: Page Visibility API কি?
উত্তর: Page visible কিনা detect করতে (user অন্য tab এ গেলে pause animation/video)।

প্রশ্ন ১৮৩: Clipboard API কিভাবে ব্যবহার করে?
javascript
navigator.clipboard.writeText('text');
navigator.clipboard.readText();
প্রশ্ন ১৮৪: Battery Status API কি?
উত্তর: Device battery status জানার জন্য (level, charging etc.)।

প্রশ্ন ১৮৫: Vibration API কি?
উত্তর: Mobile device vibrate করার জন্য।

JavaScript এরর হ্যান্ডলিং ও ডিবাগিং (প্রশ্ন ১৮৬-২০০)
প্রশ্ন ১৮৬: try...catch...finally block এর সিনট্যাক্স কি?
javascript
try {
    // code that may throw error
} catch (error) {
    // handle error
} finally {
    // always executes
}
প্রশ্ন ১৮৭: throw statement কিভাবে ব্যবহার করে?
javascript
throw new Error("Something went wrong");
প্রশ্ন ১৮৮: Error object এর properties কি কি?
উত্তর: name, message, stack (non-standard but widely supported)।

প্রশ্ন ১৮৯: Custom error class কিভাবে তৈরি করে?
javascript
class ValidationError extends Error {
    constructor(message) {
        super(message);
        this.name = "ValidationError";
    }
}
প্রশ্ন ১৯০: console.log(), console.error(), console.warn() এর পার্থক্য কি?
উত্তর: console এ বিভিন্ন level এর message দেখানোর জন্য (styling and filtering)।

প্রশ্ন ১৯১: console.table() কি করে?
উত্তর: array/object কে table format এ দেখায়।

প্রশ্ন ১৯২: console.time() এবং console.timeEnd() কি করে?
উত্তর: code execution time measure করার জন্য।

প্রশ্ন ১৯৩: debugger statement কি করে?
উত্তর: debugger breakpoint সেট করে (যদি DevTools open থাকে)।

প্রশ্ন ১৯৪: Source map কি?
উত্তর: Minified code কে original source code এ map করার ফাইল, debugging সহজ করে।

প্রশ্ন ১৯৫: Strict mode ("use strict") কি করে?
উত্তর: JavaScript কে strict mode এ execute করে, common mistakes কে error করে দেয়।

প্রশ্ন ১৯৬: Common runtime errors গুলো কি কি?
উত্তর:

ReferenceError: variable ডিক্লেয়ার করা নেই

TypeError: wrong type এর উপর operation

SyntaxError: syntax ভুল

RangeError: value out of range

প্রশ্ন ১৯৭: Uncaught TypeError: Cannot read property 'x' of undefined এর মানে কি?
উত্তর: undefined/null এর property access করার চেষ্টা করা হয়েছে।

প্রশ্ন ১৯৮: Maximum call stack size exceeded error কেন হয়?
উত্তর: infinite recursion বা খুব গভীর recursion এর কারণে।

প্রশ্ন ১৯৯: Promise এ unhandled rejection handle করার উপায়?
javascript
process.on('unhandledRejection', (reason, promise) => {});
// browser এ
window.addEventListener('unhandledrejection', event => {});
প্রশ্ন ২০০: Performance optimization techniques কি কি?
উত্তর:

Debouncing/throttling

Lazy loading

Code splitting

Memoization

Virtual DOM (React) / Reflow minimize

Web workers for heavy computation

Event delegation

Debouncing scroll/resize events

Debouncing API calls

Using requestAnimationFrame for animations

JavaScript ইন্টারভিউ টিপস
Concept clear রাখুন: Hoisting, closure, prototype, event loop ভালোভাবে বুঝুন

Code লেখার অভ্যাস করুন: নিজে নিজে ছোট ছোট project তৈরি করুন

Problem solving প্র্যাকটিস করুন: LeetCode, HackerRank এ JavaScript দিয়ে সমস্যা সমাধান করুন

Modern features জানুন: ES6+ features ভালোভাবে জানুন

Browser DevTools ব্যবহার করুন: Debugging এ দক্ষ হন

শুভ কামনা! 🚀


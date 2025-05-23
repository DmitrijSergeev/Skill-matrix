В JavaScript существует два основных типа данных:

Примитивные (primitive types)
Ссылочные (reference types)

Давайте разберем их подробнее:

1. Примитивные типы данных:

Примитивные типы — это неизменяемые значения. Когда ты работаешь с ними, 
ты оперируешь непосредственно значением, а не ссылкой на объект.

1.1 number — числовой тип
Примеры: 1, 3.14, -42, Infinity, NaN
Используется для представления как целых чисел, так и чисел с плавающей точкой.

1.2 string — строка
Примеры: "Hello", 'world', `Template string`
Последовательность символов прописана в Unicode. Объявляется в кавычках.

1.3 boolean — логический тип
Примеры: true, false
Используется для логических операций, условий.

1.4 undefined — неопределенное значение
Пример: переменная объявлена, но не инициализирована:

let a;
console.log(a); // undefined

1.5 null — "ничего", явно заданное пустое значение
Пример:

let b = null;

1.6 symbol — уникальный и неизменяемый идентификатор
Используется, например, как уникальный ключ для объекта.
Пример:

const sym = Symbol('id');

1.7 bigint — тип для очень больших целых чисел
Пример:

const big = 1234567890123456789012345678901234567890n;

2. Ссылочные типы данных (объекты)
Это сложные типы, которые хранятся и передаются по ссылке.

2.1 object — базовый тип для хранения коллекций данных
Пример:

const user = {
name: "Alice",
age: 25
};

2.2 array — массив, частный случай объекта
Пример:

const arr = [1, 2, 3];

2.3 function — функция тоже является объектом
Пример:

function greet() {
console.log("Hi!");
}

date, regexp, map, set, и другие — это встроенные объекты, расширяющие функциональность

Встроенный оператор typeof
может быть использован для определения типа:

typeof 42         // "number"
typeof "hi"       // "string"
typeof true       // "boolean"
typeof undefined  // "undefined"
typeof null       // "object" // ← это историческая ошибка
typeof {}         // "object"
typeof []         // "object"
typeof function(){} // "function"

Внимание!!!:
Функции в JavaScript — это объекты, но со специальным подтипом.

🔍 Почему typeof function(){} === "function"?
Когда JavaScript только разрабатывался, было решено, что 
удобнее будет отделять функции от обычных объектов, чтобы 
можно было легко проверять, что значение — именно функция. 
Поэтому оператор typeof для функций возвращает:

typeof function(){}; // "function"
Это единственный "нестандартный" тип, который возвращает typeof, кроме 
семи примитивов и object.

🧠 Под капотом
Функции — это объекты типа Function:

const f = function() {};
f instanceof Object;   // true
f instanceof Function; // true
Они имеют свойства объекта (их можно расширять, у них есть прототипы и методы).

Но в отличие от обычных объектов, они вызываемы:

f(); // это работает
const obj = {};
obj(); // TypeError: obj is not a function
💡 Вывод
typeof возвращает "function" — для удобства.

На самом деле, функция — это объект с вызываемым поведением.

Это специальный подтип объекта в JavaScript.
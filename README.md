# Подборка правил по стилю JavaScript


### **Используйте `const` для объявления переменных; избегайте var.**

>Это гарантирует, что вы не сможете
переопределять значения, т.к. это может привести
к ошибкам и к усложнению понимания кода.
```
// bad
var a = 1;
var b = 2;

// good
const a = 1;
const b = 2;
```

### **Не вызывайте напрямую методы `Object.prototype`, такие как `hasOwnProperty`, `propertyIsEnumerable`, и `isPrototypeOf`.**

>Эти методы могут быть переопределены в свойствах объекта, который мы проверяем { hasOwnProperty: false }, или этот объект может быть null (Object.create(null)).
```
// bad
console.log(object.hasOwnProperty(key));

// good
console.log(Object.prototype.hasOwnProperty.call(object, key));

// excellent
const has = Object.prototype.hasOwnProperty; // Кэшируем запрос в рамках 	модуля.
console.log(has.call(object, key));
```

### **Используйте одинарные кавычки `''` для строк.**
```
// bad
const name = "Capt. Janeway";

// bad - литерал шаблонной строки должен содержать интерполяцию или переводы строк
const name = `Capt. Janeway`;

// good
const name = 'Capt. Janeway';
```

### **Когда вам необходимо использовать анонимную функцию (например, при передаче встроенной функции обратного вызова), используйте стрелочную функцию.**

>Почему? Таким образом создаётся функция, которая выполняется в контексте `this`, который мы обычно хотим, а также это более короткий синтаксис.
>Почему бы и нет? Если у вас есть довольно сложная функция, вы можете переместить эту логику внутрь её собственного именованного функционального выражения.
```
// bad
[1, 2, 3].map(function (x) {
  const y = x + 1;
  return x * y;
});

// good
[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});
```

### **Точка с запятой — ОБЯЗАТЕЛЬНА**

>Каждая инструкция должна заканчиваться точкой с запятой. Использование автоматической вставки точки с запятой запрещено.
```
// bad
let luke = {}
let leia = {}
[luke, leia].forEach(jedi => jedi.father = 'vader')

// good
let luke = {};
let leia = {};
[luke, leia].forEach((jedi) => {
jedi.father = 'vader';
});
```

### **Одна переменная за раз**

>Каждое объявление локальной переменной объявляет только одну переменную: такие объявления, как let a = 1, b = 2; не используются.
```
// bad
let a = 1, b = 2, c = 3;

// good
let a = 1;let b = 2;let c = 3;
```

### **Пробелы**

>Используйте пробелы между параметрами и не используйте между именем функции и скобкой;
```
// bad
function edit (name,age) {
// тело функции
}

// good
function edit(name, age) {
// тело функции
}
```

### **Всегда используйте class**

>Избегайте прямых манипуляций с prototype.
```
// bad
function Queue(contents = []) {
 this.queue = [...contents];
 }
Queue.prototype.pop = function () {
 const value = this.queue[0];
 this.queue.splice(0, 1);
 return value;
};

// good
class Queue {
constructor(contents = []) {
this.queue = [...contents];
}
```

### **Создание массивов**

>Для создания массива используйте квадратные скобки. Не создавайте массивы через конструктор new Array.
```
// bad
 var items = new Array();

// good
 var items = [];  
```

### **Положение скобок**

>Открывающая фигурная скобка располагается на той же строке. Перед скобкой пробел. Закрывающая скобка располагается на новой строке.
```
// bad
let edit = (name, age) =>
{
  if (age < 100) {/*тело цикла*/}
}

// good
let edit = (name, age) => {
  if (age < 100) {
    // тело цикла
  }
}
```

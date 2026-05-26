1. Вывести в консоль строчку "Hello world"
console.log("Hello world");

2. Вывести в консоль "Hello world" 150 раз
for (let i = 0; i < 150; i++) {
  console.log("Hello world");
}

3. Вывести в консоль все чётные числа от 2 до 20
for (let n = 2; n <= 20; n += 2) {
  console.log(n);
}

4. Получить в скрипте аргумент(process.argv) перемножить его на 2 и вывести в консоль результат, в виде:
nodejs script.js 5
результат: 10
// multiply.js
const args = process.argv.slice(2);
const raw = args[0];

if (raw === undefined) {
  console.log("Ошибка: не передан аргумент.");
  process.exit(1);
}

const num = Number(raw);
if (Number.isNaN(num)) {
  console.log("Ошибка: аргумент не является числом.");
  process.exit(1);
}

const result = num * 2;
console.log(`результат: ${result}`);

5. Получить аргумет. Если он больше 0- вывести в консоль "Hello", если меньше - "olleH":
nodejs script.js 1
Hello
nodejs script.js 1
olleH
// checkSign.js
const arg = process.argv[2];

if (arg === undefined) {
  console.log("Ошибка: не передан аргумент.");
  process.exit(1);
}

const n = Number(arg);
if (Number.isNaN(n)) {
  console.log("Ошибка: аргумент не является числом.");
  process.exit(1);
}

if (n > 0) {
  console.log("Hello");
} else if (n < 0) {
  console.log("olleH");
} else {
  console.log("Ноль");
}


6. То же самое, что и в № 4, но если аргумент = 0, вывести в консоль "Zero"
nodejs script.js 1
Hello
nodejs script.js 1
olleH
nodejs script.js 0
Zero
// checkSignZero.js
const raw = process.argv[2];

if (raw === undefined) {
  console.log("Ошибка: не передан аргумент.");
  process.exit(1);
}

const n = Number(raw);
if (Number.isNaN(n)) {
  console.log("Ошибка: аргумент не является числом.");
  process.exit(1);
}

if (n > 0) {
  console.log("Hello");
} else if (n < 0) {
  console.log("olleH");
} else {
  console.log("Zero");
}

7. Калькулятор light. Получить 2 аргумента, перемножить их и вывести результат в консоль:
nodejs script.js 2 3
Result: 6
// calc.js
const [aRaw, bRaw] = process.argv.slice(2);

if (aRaw === undefined || bRaw === undefined) {
  console.log("Ошибка: требуется 2 аргумента.");
  process.exit(1);
}

const a = Number(aRaw);
const b = Number(bRaw);

if (Number.isNaN(a) || Number.isNaN(b)) {
  console.log("Ошибка: аргументы должны быть числами.");
  process.exit(1);
}

console.log(`Result: ${a * b}`);

8. Калькулятор advanced. Получить 3 аргумента: 1 первый аргумент- 1 число, 2ой аргумент- мат. операция, 3ий аргумент - второе число. Выполнить математическую операцию переданную во 2ом аргументе и вывести в консоль результат:
nodejs script.js 2 "*" 3
Result: 6
nodejs script.js 2 "-" 3
Result: -1
nodejs script.js 2 "+" 3
Result: 5
nodejs script.js 2 "/" 3
Result: 0.6666666
// advancedCalc.js
const [aRaw, op, bRaw] = process.argv.slice(2);

if (aRaw === undefined || op === undefined || bRaw === undefined) {
  console.log("Ошибка: требуется 3 аргумента: число операция число");
  process.exit(1);
}

const a = Number(aRaw);
const b = Number(bRaw);
if (Number.isNaN(a) || Number.isNaN(b)) {
  console.log("Ошибка: первый и третий аргументы должны быть числами.");
  process.exit(1);
}

let result;
switch (op) {
  case '+':
    result = a + b;
    break;
  case '-':
    result = a - b;
    break;
  case '*':
  case 'x':
  case 'X':
    result = a * b;
    break;
  case '/':
    if (b === 0) {
      console.log("Ошибка: деление на ноль.");
      process.exit(1);
    }
    result = a / b;
    break;
  default:
    console.log("Ошибка: неизвестная операция. Допустимо: + - * /");
    process.exit(1);
}

console.log(`Result: ${result}`);


9. Вывести в консоль букву Z нарисованную звёздочками. Размер 5Х5 символов:
*****
   * 
  *
 *
*****
// drawZ.js
console.log("*****");
console.log("   * ");
console.log("  *  ");
console.log(" *   ");
console.log("*****");

10. То же самое что и в п.9 но размер буквы передаётся в 1 аргументе:
nodejs script.js 5
*****
   * 
  *
 *
*****
nodejs script.js 3
***
 * 
***
// drawZ.js
const raw = process.argv[2];
const n = Number(raw);

if (!raw || Number.isNaN(n) || !Number.isInteger(n) || n < 3 || n > 10) {
  console.log("Error, argument should be between 3 and 10");
  process.exit(1);
}

console.log("*".repeat(n));

for (let i = 1; i <= n - 2; i++) {
  const pos = n - 1 - i; 
  const line = " ".repeat(pos) + "*" + " ".repeat(n - pos - 1);
  console.log(line);
}

console.log("*".repeat(n));
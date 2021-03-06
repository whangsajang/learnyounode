Напишіть програму, яка надсилає HTTP GET запит на URL, який Ви отримаєте в якості першого аргументу командного рядка. Виведіть вміст **кожної** події "data" з відповіді (response) порядково в консоль (stdout).

----------------------------------------------------------------------
## ІНФОРМАЦІЯ

Для рішення цієї задачі Ви маєте використати вбудований модуль `http`.

Документація до модуля `http` Ви можете знайти, перейшовши в браузері сюди:
  {rootdir:/node_apidoc/http.html}

Метод `http.get()` - це спрощений метод для простого GET-запиту, використовуйте його, щоб спростити ваш розв’язок. Першим аргументом в `http.get()` може бути URL на який вам потрібно надіслати запит, другим - функція зворотнього виклику (сallback).

На відміну від інших функцій зворотнього виклику, ця функція має наступну сигнатуру:

```js
function callback (response) { /* ... */ }
```

Тут об’єкт `response` є об’єктом типу **Stream (Потік)**. Ви можете інтерпретувати потоки як об’єкти, які створюють події. Три з них найбільш цікаві: "data", "error" та "end". Ви можете підписатись на події таким чином:

```js
response.on("data", function (data) { /* ... */ })
```

Подія "data" створюється тоді, коли частина даних стає доступною і може бути опрацьованою. Розмір цих частин переважно залежить від джерела данних.

Об’єкт/потік `response`, який Ви можете отримати з `http.get()` також має метод `setEncoding()`. Якщо Ви передасте методу  "utf8", то подія "data" буде посилати дані рядкового типу, замість стандартного для  Node об’єкту `Buffer`, який Ви змушені постійно конвертувати в рядки.

----------------------------------------------------------------------

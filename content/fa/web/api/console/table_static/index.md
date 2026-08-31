---
title: "console: table() static method"
short-title: table()
slug: Web/API/console/table_static
page-type: web-api-static-method
browser-compat: api.console.table_static
---

{{APIRef("Console API")}} {{AvailableInWorkers}}

متد ایستای **`console.table()`** داده‌های جدولی را به صورت جدول نمایش می‌دهد.

## نحو (Syntax)

```js-nolint
console.table(data)
console.table(data, columns)
```

### پارامترها

- `data`
  - : داده‌ای که باید نمایش داده شود. این داده باید یا یک آرایه باشد یا یک شیء. هر آیتم در آرایه، یا هر ویژگی در شیء، به‌عنوان یک ردیف در جدول نمایش داده می‌شود. ستون اول جدول با برچسب `(index)` مشخص می‌شود و مقادیر آن شامل اندیس‌های آرایه یا نام ویژگی‌ها است.

    اگر عناصر آرایه یا ویژگی‌های شیء، خودشان آرایه یا شیء باشند، آنگاه آیتم‌ها یا ویژگی‌های آن‌ها در ردیف مربوطه، هر کدام در یک ستون جداگانه فهرست می‌شوند.

    توجه داشته باشید که در فایرفاکس، `console.table()` محدود به نمایش ۱۰۰۰ ردیف (شامل ردیف عنوان) است.

- `columns` {{optional_inline}}
  - : آرایه‌ای که می‌تواند برای محدود کردن ستون‌های نمایش داده‌شده در جدول استفاده شود. این آرایه شامل اندیس‌ها است، اگر هر ورودی `data` یک آرایه باشد، یا شامل نام ویژگی‌ها است، اگر هر ورودی `data` یک شیء باشد. جدول حاصل فقط شامل ستون‌هایی می‌شود که با اندیس‌ها یا نام‌های داده‌شده مطابقت دارند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### مجموعه‌هایی از انواع اولیه

آرگومان `data` می‌تواند یک آرایه یا یک شیء باشد.

```js
// یک آرایه از رشته‌ها

console.table(["apples", "oranges", "bananas"]);
```

| (index) | Values    |
| ------- | --------- |
| 0       | 'apples'  |
| 1       | 'oranges' |
| 2       | 'bananas' |

```js
// یک شیء که ویژگی‌های آن رشته هستند

function Person(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}

const me = new Person("Tyrone", "Jones");

console.table(me);
```

| (index)   | Values   |
| --------- | -------- |
| firstName | 'Tyrone' |
| lastName  | 'Jones'  |

### مجموعه‌هایی از انواع ترکیبی

اگر عناصر آرایه یا ویژگی‌های شیء، خودشان آرایه یا شیء باشند، آنگاه عناصر یا ویژگی‌های آن‌ها در ردیف مربوطه، هر کدام در یک ستون جداگانه فهرست می‌شوند:

```js
// یک آرایه از آرایه‌ها

const people = [
  ["Tyrone", "Jones"],
  ["Janet", "Smith"],
  ["Maria", "Cruz"],
];
console.table(people);
```

| (index) | 0        | 1       |
| ------- | -------- | ------- |
| 0       | 'Tyrone' | 'Jones' |
| 1       | 'Janet'  | 'Smith' |
| 2       | 'Maria'  | 'Cruz'  |

```js
// یک آرایه از اشیاء

function Person(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}

const tyrone = new Person("Tyrone", "Jones");
const janet = new Person("Janet", "Smith");
const maria = new Person("Maria", "Cruz");

console.table([tyrone, janet, maria]);
```

اگر آرایه حاوی اشیاء باشد، ستون‌ها با نام ویژگی برچسب‌گذاری می‌شوند.

| (index) | firstName | lastName |
| ------- | --------- | -------- |
| 0       | 'Tyrone'  | 'Jones'  |
| 1       | 'Janet'   | 'Smith'  |
| 2       | 'Maria'   | 'Cruz'   |

```js
// یک شیء که ویژگی‌های آن اشیاء هستند

const family = {};

family.mother = new Person("Janet", "Jones");
family.father = new Person("Tyrone", "Jones");
family.daughter = new Person("Maria", "Jones");

console.table(family);
```

| (index)  | firstName | lastName |
| -------- | --------- | -------- |
| daughter | 'Maria'   | 'Jones'  |
| father   | 'Tyrone'  | 'Jones'  |
| mother   | 'Janet'   | 'Jones'  |

### محدود کردن ستون‌های نمایش داده‌شده

به‌طور پیش‌فرض، `console.table()` همه عناصر را در هر ردیف فهرست می‌کند. می‌توانید از پارامتر اختیاری `columns` برای انتخاب زیرمجموعه‌ای از ستون‌ها جهت نمایش استفاده کنید:

```js
// یک آرایه از اشیاء، فقط logging firstName

function Person(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}

const tyrone = new Person("Tyrone", "Jones");
const janet = new Person("Janet", "Smith");
const maria = new Person("Maria", "Cruz");

console.table([tyrone, janet, maria], ["firstName"]);
```

| (index) | firstName |
| ------- | --------- |
| 0       | 'Tyrone'  |
| 1       | 'Janet'   |
| 2       | 'Maria'   |

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مستندات مایکروسافت اج برای `console.table()`](https://learn.microsoft.com/en-us/microsoft-edge/devtools/console/api#table)
- [مستندات Node.js برای `console.table()`](https://nodejs.org/docs/latest/api/console.html#consoletabletabulardata-properties)
- [مستندات گوگل کروم برای `console.table()`](https://developer.chrome.com/docs/devtools/console/api/#table)
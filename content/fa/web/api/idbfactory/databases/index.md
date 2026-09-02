---
title: "IDBFactory: databases() method"
short-title: databases()
slug: Web/API/IDBFactory/databases
page-type: web-api-instance-method
browser-compat: api.IDBFactory.databases
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

متد **`databases`** از رابط {{domxref("IDBFactory")}} یک {{jsxref("Promise")}} برمی‌گرداند که با آرایه‌ای از اشیاء حاوی نام و نسخهٔ تمام پایگاه‌داده‌های موجود، تکمیل می‌شود.

این یک عکس فوری (snapshot) از پایگاه‌داده‌ها است که عمدتاً برای این در نظر گرفته شده تا برنامه‌های وب بتوانند بررسی کنند که چه پایگاه‌داده‌هایی ایجاد شده‌اند – مثلاً برای پاک‌سازی پایگاه‌داده‌هایی که توسط نسخه‌های قدیمی‌تر کد برنامه ایجاد شده‌اند.

## نحو (Syntax)

```js-nolint
databases()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با آرایه‌ای از اشیاء نشان‌دهندهٔ عکس فوری از پایگاه‌داده‌های موجود تکمیل می‌شود (یا با خطا/استثناهای زیر رد می‌شود).

هر شیء آرایه دارای ویژگی‌های زیر است:

- `name`
  - : نام پایگاه‌داده.
- `version`
  - : نسخهٔ پایگاه‌داده.

توجه داشته باشید که ترتیب اشیاء بازگشتی تعریف نشده است.

### استثناها

- `SecurityError` {{domxref("DOMException")}}
  - : اگر متد از یک [مبدأ opaque](https://stackoverflow.com/questions/42239643/when-do-browsers-send-the-origin-header-when-do-browsers-set-the-origin-to-null/42242802#42242802) فراخوانی شود یا کاربر فضای ذخیره‌سازی را غیرفعال کرده باشد، پرتاب می‌شود.
- `UnknownError` {{domxref("DOMException")}}
  - : اگر به هر دلیلی نتوان مجموعهٔ پایگاه‌داده‌های موجود را تعیین کرد، پرتاب می‌شود.

## مثال‌ها

### ایجاد و فهرست‌کردن پایگاه‌داده‌ها

این مثال تعدادی پایگاه‌داده ایجاد/باز می‌کند. پس از راه‌اندازی موفق هر پایگاه‌داده، تمام پایگاه‌داده‌های موجود را فهرست می‌کند.

```html hidden
<pre id="log"></pre>
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```css hidden
#log {
  height: 240px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### JavaScript

ابتدا تابعی را تعریف می‌کنیم که برای دریافت و ثبت پایگاه‌داده‌های موجود استفاده می‌شود. این تابع منتظر Promise بازگشتی از `indexedDB.databases()` می‌ماند و سپس آرایه را پیمایش کرده و مقادیر هر عنصر را فهرست می‌کند:

```js
async function getDb() {
  const databases = await indexedDB.databases();
  log("List databases:");
  databases.forEach((element) => {
    log(`name: ${element.name}, version: ${element.version}`);
  });
}
```

برای نشان دادن نحوهٔ استفاده از تابع بالا، در زیر دو پایگاه‌داده ایجاد می‌کنیم. برای هر پایگاه‌داده، درست قبل از باز شدن، یک پیام ثبت می‌کنیم. همچنین در زمان راه‌اندازی موفق (یا خطا) نیز ثبت می‌کنیم و سپس پایگاه‌داده‌های موجود را فهرست می‌کنیم.

```js
// Create a database named toDoList with default version (1)
const dbName1 = "toDoList";
log(`Opening: ${dbName1}`);
let DBOpenRequest = window.indexedDB.open(dbName1);

DBOpenRequest.addEventListener("error", (event) => {
  log(`Error opening: ${dbName1}`);
  getDb();
});

DBOpenRequest.addEventListener("success", (event) => {
  log(`Initialized: ${dbName1}`);
  getDb();
});

// Create database "AnotherDb"
const dbName2 = "AnotherDb";
log(`Opening ${dbName2}`);
DBOpenRequest = window.indexedDB.open(dbName2, 2);

DBOpenRequest.addEventListener("error", (event) => {
  log(`Error opening: ${dbName2}`);
  getDb();
});

DBOpenRequest.addEventListener("success", (event) => {
  log(`Initialized: ${dbName2}`);
  getDb();
});
```

#### نتیجه

نتیجه در زیر نشان داده شده است. توجه داشته باشید که زمان لازم برای دریافت پایگاه‌داده‌ها و ترتیب آن‌ها تعریف نشده است.

{{EmbedLiveSample('Create and list databases', '100%', '280px')}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- استفاده از تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم محدوده‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهدهٔ مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).
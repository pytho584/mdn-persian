---
title: "IDBIndex: getAllRecords() method"
short-title: getAllRecords()
slug: Web/API/IDBIndex/getAllRecords
page-type: web-api-instance-method
browser-compat: api.IDBIndex.getAllRecords
---

{{ APIRef("IndexedDB") }}

متد **`getAllRecords()`** از رابط {{domxref("IDBIndex")}} همهٔ رکوردها (شامل کلیدهای ایندکس، کلیدهای اصلی و مقادیر) را از ایندکس بازیابی می‌کند.

`getAllRecords()` با شمارش همزمان کلیدهای اصلی و مقادیر، عملاً عملکرد {{domxref("IDBIndex.getAllKeys", "getAllKeys()")}} و {{domxref("IDBIndex.getAll", "getAll()")}} را ترکیب می‌کند. این عملیات ترکیبی باعث می‌شود برخی الگوهای بازیابی داده به‌طور قابل توجهی سریع‌تر از جایگزین‌هایی مانند پیمایش با نشانگرها (cursors) انجام شوند.

## نحو

```js-nolint
getAllRecords()
getAllRecords(options)
```

### پارامترها

یک شیء گزینه‌ها که ویژگی‌های آن می‌توانند شامل موارد زیر باشند:

- `query` {{optional_inline}}
  - : یک کلید یا یک {{domxref("IDBKeyRange")}} که رکوردهای مورد نظر برای بازیابی را مشخص می‌کند. اگر این مقدار `null` باشد یا مشخص نشده باشد، مرورگر از یک بازهٔ کلید نامحدود (unbound key range) استفاده خواهد کرد.
- `count` {{optional_inline}}
  - : تعداد رکوردهایی است که باید برگردانده شوند. اگر این مقدار از تعداد رکوردهای موجود در کوئری بیشتر باشد، مرورگر فقط رکوردهای منطبق با کوئری را بازیابی می‌کند. اگر مقدار کمتر از `0` یا بیشتر از `2^32 - 1` باشد، یک استثنای {{jsxref("TypeError")}} پرتاب خواهد شد.
- `direction` {{optional_inline}}
  - : یک مقدار شمارشی که جهت پیمایش رکوردها را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
    - `next`
      - : رکوردها از ابتدا و به ترتیب صعودی کلید پیمایش می‌شوند. این مقدار پیش‌فرض است.
    - `nextunique`
      - : رکوردها از ابتدا و به ترتیب صعودی کلید پیمایش می‌شوند. برای هر کلیدی که رکوردهای تکراری دارد، تنها نزدیک‌ترین رکورد به شروع پیمایش بازگردانده می‌شود.
    - `prev`
      - : رکوردها از انتها و به ترتیب نزولی کلید پیمایش می‌شوند.
    - `prevunique`
      - : رکوردها از انتها و به ترتیب نزولی کلید پیمایش می‌شوند. برای هر کلیدی که رکوردهای تکراری دارد، تنها نزدیک‌ترین رکورد به شروع پیمایش بازگردانده می‌شود.

### مقدار بازگشتی

یک شیء {{domxref("IDBRequest")}} که رویدادهای بعدی مربوط به این عملیات روی آن ارسال می‌شوند.

اگر عملیات موفق باشد، مقدار ویژگی {{domxref("IDBRequest.result", "result")}} درخواست، یک {{jsxref("Array", "آرایه")}} از نمونه‌های {{domxref("IDBRecord")}} است که همهٔ رکوردهای منطبق با کوئری داده‌شده را تا تعداد مشخص‌شده توسط `count` (در صورت ارائه) نشان می‌دهد.

هر نمونهٔ {{domxref("IDBRecord")}} شامل ویژگی‌های زیر است:

- `key`
  - : مقداری که کلید رکورد را در ایندکس نشان می‌دهد.
- `primaryKey`
  - : مقداری که کلید رکورد را در {{domxref("IDBObjectStore")}} مرتبط با ایندکس نشان می‌دهد.
- `value`
  - : مقداری که مقدار رکورد را نشان می‌دهد.

### استثناها

این متد ممکن است یک {{domxref("DOMException")}} از انواع زیر برانگیزد:

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("IDBIndex")}} یا {{domxref("IDBObjectStore")}} مرتبط با آن حذف یا پاک شده باشد، پرتاب می‌شود.
- `TransactionInactiveError` {{domxref("DOMException")}}
  - : اگر تراکنش (transaction) این {{domxref("IDBIndex")}} غیرفعال باشد، پرتاب می‌شود.
- {{jsxref("TypeError")}} {{domxref("DOMException")}}
  - : اگر پارامتر [`count`](#count) بین `0` و `2^32 - 1` (به‌صورت شامل) نباشد، پرتاب می‌شود.

## مثال‌ها

### استفادهٔ پایه

این مثال یک {{domxref("IDBIndex")}} را برای حداکثر ۱۰۰ رکورد که مقادیر `lastName` آن‌ها بعد از `"Smith"` قرار دارند، کوئری می‌کند و نتایج را به ترتیب معکوس مرتب می‌کند.

کد ابتدا یک تراکنش روی {{domxref("IDBDatabase")}} به نام `db` ایجاد می‌کند (کد مربوط به باز کردن پایگاه داده حذف شده است) و سپس از آن برای دریافت یک {{domxref("IDBObjectStore")}} شامل فهرست مخاطبان و از آن، یک `IDBIndex` روی ویژگی `lastName` استفاده می‌کند.

سپس متد `getAllRecords()` را روی ایندکس فراخوانی می‌کند که یک نمونه {{domxref("IDBRequest")}} بازمی‌گرداند. شنونده‌های رویداد برای رویدادهای `success` و `error` به این درخواست اضافه می‌شوند. در صورت موفقیت، نتیجهٔ `event.target.result` در کنسول ثبت می‌شود (این مقدار از طریق `request.result` نیز در دسترس است). این نتیجه شامل آرایه‌ای از نمونه‌های `IDBRecord` است.

توجه داشته باشید که از آنجا که این یک کوئری روی `IDBIndex` است، `key` و `primaryKey` در هر رکورد ممکن است مقادیر متفاوتی داشته باشند: `key` کلید ایندکس است (در اینجا `lastName`) و `primaryKey` کلید رکورد در ذخیره‌گاه شیء است.

```js
// Create a transaction on the database and use it to get the contained store
const transaction = db.transaction(["contactsList"], "readonly");
const objectStore = transaction.objectStore("contactsList");
const myIndex = objectStore.index("lastName");

const query = IDBKeyRange.lowerBound("Smith", true);

const request = myIndex.getAllRecords({
  query,
  count: 100,
  direction: "prev",
});

request.addEventListener("success", (event) => {
  const myRecords = event.target.result; // Array of IDBRecord instances
  console.log(myRecords);
});

request.addEventListener("error", (event) => {
  console.error("Error retrieving records:", event.target.error);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("IDBIndex.getAll()")}}, {{domxref("IDBIndex.getAllKeys()")}}
- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- کار با تراکنش‌ها: {{domxref("IDBTransaction")}}
- تنظیم بازه‌ای از کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- کار با نشانگرها: {{domxref("IDBCursor")}}
- [نمونهٔ خواندن سریع‌تر IndexedDB با getAllRecords()](https://microsoftedge.github.io/Demos/idb-getallrecords/) از مایکروسافت، ۲۰۲۵